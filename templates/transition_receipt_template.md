# Modèle — Reçu de transition

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **LIVRABLE VAGUE 6 — à valider par le VALIDATOR** |
| Nature | Modèle générique — preuve d'événement, non état du projet |
| Référence normative | [Politique des transitions](../protocol/transition_policy.md) §5.3 et §5.7 (décision C26) |

> **Le reçu ne remplace jamais `state.json`.** `state.json` est la source de vérité de l'état courant (A2) ; le reçu est une preuve de consommation déposée par l'agent destinataire. Toute divergence entre les deux est bloquante jusqu'à réconciliation.

> Toute valeur entre crochets est **à renseigner**. Ce modèle ne fournit aucune donnée réelle. Un `transition_id` est un identifiant, pas une preuve cryptographique (C22).

## 1. Contenu minimal normatif

Ces champs sont ceux de [TP](../protocol/transition_policy.md) §5.3 ; ils constituent le contenu minimal du reçu.

| Champ | Obligatoire | Valeur |
|---|---|---|
| `transition_id` | oui | [format `TR-AAAA-NNNN` — à renseigner] |
| `received_by` | oui | [BUILDER / AUDITOR / ORCHESTRATOR — destinataire] |
| `sprint_id` | oui | [À renseigner] |
| `action` | oui | [action autorisée, nommée] |
| `mandate_version` | oui | [version du mandat vérifiée] |
| `received_at` | oui | [horodatage de réception] |
| `checks_performed` | oui | [contrôles effectués avant consommation — voir §3] |
| `scope_acknowledged` | oui | [périmètre accepté, en une phrase] |
| `exclusions_acknowledged` | recommandé | [ce qui est explicitement hors périmètre] |

## 2. Champs de correspondance avec la transition et l'état

Ces champs ne créent pas d'exigence nouvelle : ils renvoient à des champs déjà définis dans [TP](../protocol/transition_policy.md) §2 et dans [state_model.md](../protocol/state_model.md) §6.4. À renseigner lorsqu'ils sont disponibles dans `state.json` ou le mandat.

| Champ | Origine | Valeur |
|---|---|---|
| `from_agent` | anatomie de la transition | [agent source] |
| `to_agent` | anatomie de la transition | [agent destinataire — doit correspondre à `received_by`] |
| `project_id` | `state.json` → `project.id` | [À renseigner] |
| Statut de la transition au dépôt | `state.json` → `transition.status` | [`authorized` attendu avant consommation] |
| `created_at` | anatomie de la transition | [horodatage ou « non disponible »] |
| `authorized_at` | acte du VALIDATOR | [horodatage] |
| `authorized_by` | acte du VALIDATOR | [VALIDATOR] |
| `decision_id` | acte du VALIDATOR | [référence] |
| `consumed_at` | consommation | [horodatage] |
| `expires_at` | mandat / profil | [horodatage ou « non requis » — aucune durée par défaut, C27] |
| `result_report` | achèvement | [référence au rapport produit — à renseigner à l'achèvement] |
| `completed_at` | achèvement | [horodatage ou « non atteint »] |

## 3. Contrôles avant consommation

Les contrôles sont définis dans [TP](../protocol/transition_policy.md) §5.4. Indiquer le résultat de chaque contrôle avec les statuts de [DP](../protocol/decision_policy.md) §5.2.

| # | Contrôle | Résultat | Preuve ou remarque |
|---|---|---|---|
| 1 | Identifiant présent dans l'historique | [statut] | [À renseigner] |
| 2 | Aucun reçu antérieur pour cet identifiant | [statut] | [À renseigner] |
| 3 | Statut `authorized` | [statut] | [À renseigner] |
| 4 | Transition non expirée | [statut] | [À renseigner] |
| 5 | Destinataire = `current_agent` | [statut] | [À renseigner] |
| 6 | Émetteur = agent précédent | [statut] | [À renseigner] |
| 7 | `mandate_version` = mandat courant | [statut] | [À renseigner] |
| 8 | Action inscrite au mandat | [statut] | [À renseigner] |
| 9 | Périmètre explicite | [statut] | [À renseigner] |

`NOT_CHECKED` ne vaut jamais succès. Un contrôle en échec interdit la consommation.

## 4. Preuves jointes

| # | Preuve | Statut | Référence |
|---|---|---|---|
| 1 | [À renseigner] | [`directly_verified` / `reproduced` / `cross_checked` / `declared_only` / `partial` / `missing` / `invalid`] | [À renseigner] |

## 5. Destination du reçu — mapping C26

| Destinataire | Emplacement du reçu |
|---|---|
| BUILDER | `sprint_report/` |
| AUDITOR | `audit_report/` |
| ORCHESTRATOR | `docs/governance/receipts/` |

Le reçu est déposé **par l'agent destinataire** dans son propre périmètre d'écriture. ORCHESTRATOR ne produit pas le reçu de sa propre consommation à la place du destinataire.

| Champ | Valeur |
|---|---|
| `destination` | [sprint_report/ / audit_report/ / docs/governance/receipts/ — selon `received_by`] |
| Déposé par | [`received_by`] |
| Date de dépôt | [horodatage] |

## 6. Limites du reçu

Le reçu est une preuve **procédurale** par défaut. Il n'est ni une preuve cryptographique, ni une preuve d'exécution, ni une preuve de qualité, ni un mécanisme infalsifiable sans contrôle technique. Sa valeur probante dépend de l'environnement : voir [permission_policy.md](../protocol/permission_policy.md) et [constat OpenCode](../implementations/opencode/agent_permissions.md).

| Limite à rappeler | État |
|---|---|
| Permissions | `unknown` — aucune garantie sans test contradictoire |
| Protection de `main` | `unknown` — T5 préparé, non exécuté |
| T1 à T5 | `NON EXÉCUTÉS` tant qu'aucune preuve d'exécution n'est fournie |

Un reçu ne se modifie pas après dépôt : une correction produit un nouvel événement, pas une réécriture (TP §5.5). Un `transition_id` possède au plus un reçu (INV-04).
