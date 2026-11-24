# Politique des transitions

| Champ | Valeur |
|---|---|
| Version | 0.2 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | Transitions, autorisations, reçus, consommation, expiration, invalidation |
| Autorité | Normatif — **source unique du mécanisme de reçu** |
| Vague | 3 |

**Sources citées :** `F3` = `AKORIS_consolide.md` §6, §10.5 · `F2` = `AKORIS_architecture_documentaire.md` · `GC` = `protocol/governance_core.md` · `SM` = `protocol/state_model.md` · décisions VALIDATOR **A2**, **C22**, **C24**.

---

## 0. Objet

Cette politique est la **source unique** de tout ce qui concerne une transition : son anatomie, son cycle de vie, son autorisation, sa consommation, sa preuve et sa fin.

Elle existe séparément pour trois raisons :

1. Le mécanisme de reçu est un **composant central** du dispositif, pas un détail d'implémentation (C8).
2. Le reçu doit avoir une **source normative propre** : il ne peut pas dépendre d'un manuel historique (C24, A6).
3. Le cycle de vie d'une transition est trop dense pour rester un paragraphe de `state_model.md`.

`state_model.md` définit les **états** et les **invariants**. Cette politique définit les **règles de passage**, la **preuve** et la **fin de vie**. Aucun des deux ne duplique l'autre.

---

## 1. Définition

Une **transition** est un passage autorisé d'un rôle à un autre, pour une action déterminée, sur un périmètre déterminé, pendant une durée déterminée.

Elle porte un identifiant unique de la forme `TR-AAAA-NNNN` (voir `reference/terminology.md` §9).

**Une transition n'est pas :**

- une autorisation implicite ;
- une preuve cryptographique (`GC-48`) ;
- un ordre permanent : elle se consomme ;
- un droit d'agir hors périmètre.

---

## 2. Anatomie

| Champ | Obligatoire | Rôle |
|---|---|---|
| `transition_id` | oui | Identifiant unique, jamais réutilisé |
| `from_agent` | oui | Émetteur |
| `to_agent` | oui | Destinataire |
| `action` | oui | Action autorisée, nommée |
| `mandate_version` | oui | Version du mandat concerné |
| `sprint_id` | oui | Sprint concerné |
| `status` | oui | État du cycle de vie |
| `created_at` | oui | Création |
| `expires_at` | selon profil | Échéance |
| `authorized_at` | à l'autorisation | Date de l'acte humain |
| `authorized_by` | à l'autorisation | Auteur de l'acte |
| `decision_id` | à l'autorisation | Décision de référence |
| `consumed_at` | à la consommation | Date de consommation |
| `receipt_reference` | à la consommation | Référence du reçu |
| `completed_at` | à l'achèvement | Date de production du résultat |
| `result_report` | à l'achèvement | Rapport produit |

> **Nommage (C22).** Le champ normatif est `transition_id`. Le nom `token` est déprécié : il suggère une garantie cryptographique que le protocole exclut.

---

## 3. Les cinq notions à ne jamais confondre

| Notion | Acte | Acteur | Preuve |
|---|---|---|---|
| **Autorisation** | Permettre l'action | VALIDATOR | `authorized_at`, `authorized_by`, `decision_id` |
| **Consommation** | Accepter et utiliser l'autorisation | agent destinataire | **Reçu de transition** |
| **Exécution** | Réaliser l'action | agent destinataire | Commits, journaux, rapport |
| **Achèvement** | Produire le résultat | agent destinataire | `result_report`, `completed_at` |
| **Acceptation** | Accepter le résultat | VALIDATOR | Décision (`GO`, `GO_WITH_RESERVES`, …) |

Une autorisation non consommée n'a produit aucun effet. Une consommation non exécutée est un écart. Une exécution non achevée est un blocage. Un achèvement non accepté n'est pas un résultat.

---

## 4. Cycle de vie

Les états sont définis dans `state_model.md` §4. Cette politique précise **ce qui se passe** à chaque franchissement.

| État | Signification | Condition d'entrée | Condition de sortie |
|---|---|---|---|
| `draft` | Transition en préparation | Mandat rédigé | Soumission au VALIDATOR |
| `awaiting_human_go` | En attente d'autorisation | Soumission | Décision humaine ou expiration |
| `authorized` | Autorisée, non consommée | Acte du VALIDATOR | Reçu déposé ou expiration |
| `consumed` | Consommée, non démarrée | Reçu valide | Démarrage effectif |
| `in_progress` | Action en cours | Démarrage | Résultat produit |
| `completed` | Résultat produit | Rapport livré | — (terminal) |
| `rejected` | Refusée | Refus du VALIDATOR | — (terminal) |
| `expired` | Échue sans usage | Échéance atteinte | — (terminal) |
| `cancelled` | Annulée | Décision | — (terminal) |

**Règle :** aucun état terminal n'est réactivable. Une nouvelle action exige un **nouvel identifiant** (`GC-46`).

---

## 5. Le reçu de transition

### 5.1 Rôle

Le reçu est la **preuve de l'événement de consommation**. Il répond à une question que `state.json` ne peut pas trancher seul : *l'agent destinataire a-t-il réellement reçu et accepté cette autorisation, à cette date, pour ce périmètre ?*

Cette question se pose parce qu'un seul agent écrit l'état central (`GC-12`). Sans reçu, la consommation serait une affirmation d'ORCHESTRATOR sur le comportement d'un autre agent — c'est-à-dire une preuve `declared_only`.

### 5.2 Qui dépose, et où

| Destinataire | Emplacement du reçu |
|---|---|
| BUILDER | `sprint_report/` |
| AUDITOR | `audit_report/` |
| ORCHESTRATOR | `docs/governance/receipts/` (décision **C26**) |

**Mapping normatif (décision C26) :**

```text
BUILDER       → sprint_report/
AUDITOR       → audit_report/
ORCHESTRATOR  → docs/governance/receipts/
```

Le reçu est déposé **par l'agent destinataire**, dans son propre périmètre d'écriture. C'est ce qui le rend opposable : ORCHESTRATOR ne peut pas le produire à sa place.

> **Décision C26 — portée.** Le reçu est une **preuve d'événement**, non une seconde source de vérité. La source de vérité reste `state.json` (`A2`) ; une divergence entre l'état et le reçu est bloquante.

### 5.3 Contenu minimal

| Champ | Obligatoire | Contenu |
|---|---|---|
| `transition_id` | oui | Identifiant reçu |
| `received_by` | oui | Agent destinataire |
| `sprint_id` | oui | Sprint concerné |
| `action` | oui | Action autorisée |
| `mandate_version` | oui | Version du mandat vérifiée |
| `received_at` | oui | Horodatage de réception |
| `checks_performed` | oui | Contrôles effectués avant consommation |
| `scope_acknowledged` | oui | Périmètre accepté, en une phrase |
| `exclusions_acknowledged` | recommandé | Ce qui est explicitement hors périmètre |

Le modèle correspondant est `templates/transition_receipt_template.md` (vague 6).

### 5.4 Contrôles avant consommation

Le destinataire vérifie, dans cet ordre, et **ne consomme pas** si un contrôle échoue :

| # | Contrôle | Échec ⇒ |
|---|---|---|
| 1 | L'identifiant existe dans l'historique | Blocage |
| 2 | L'identifiant n'a jamais été consommé (`INV-04`) | Violation P1 |
| 3 | Le statut est `authorized` | Attente ou blocage |
| 4 | La transition n'est pas expirée | `expired` |
| 5 | Le destinataire est bien `current_agent` (`INV-03`) | Blocage |
| 6 | L'émetteur est bien l'agent précédent | Blocage |
| 7 | `mandate_version` correspond au mandat courant (`INV-10`) | Blocage |
| 8 | L'action demandée figure dans le mandat | Blocage |
| 9 | Le périmètre est explicite | Blocage |

Un contrôle non réalisable est déclaré `NOT_CHECKED` : il ne vaut jamais succès (`GC-25`).

### 5.5 Unicité

- Un `transition_id` possède **au plus un** reçu (`INV-04`).
- Deux reçus pour un même identifiant constituent une **divergence bloquante** (`state_model.md` §7).
- Un reçu ne se modifie pas après dépôt : une correction produit un nouvel événement, pas une réécriture.

### 5.6 Ce qu'un reçu n'est pas

- Ce n'est **pas** une preuve cryptographique.
- Ce n'est **pas** une preuve d'exécution : il prouve la réception, pas le travail.
- Ce n'est **pas** une preuve de qualité.
- Ce n'est **pas** infalsifiable : sans contrôle technique, il reste une preuve **procédurale**. Sa solidité dépend de l'environnement (`permission_policy.md`).

### 5.7 Reçu pour ORCHESTRATOR — décision C26

Le dispositif ne définissait initialement un emplacement de reçu que pour BUILDER et AUDITOR, alors qu'ORCHESTRATOR est également destinataire de transitions (fin de sprint, remontée d'audit).

> **Décision C26 appliquée.** Le reçu d'ORCHESTRATOR est déposé dans **`docs/governance/receipts/`**, par ORCHESTRATOR lui-même en tant que destinataire. La symétrie du dispositif est ainsi complète : le rédacteur de l'état ne produit pas le reçu de sa propre consommation.

**Conséquences :**

1. Le reçu suit les règles communes des §5.3 à §5.6 : contenu minimal, unicité, non-modification après dépôt.
2. Le dossier `docs/governance/receipts/` appartient au projet gouverné ; sa création et les permissions d'écriture associées relèvent de la configuration du projet.
3. Aucune permission n'est requalifiée par cette décision : le classement reste `unknown` tant que T1 à T5 ne sont pas exécutés.
4. `receipt_reference` dans `state.json` désigne le reçu ; il ne le remplace pas.

---

## 6. Anti-réutilisation (rejeu)

Une autorisation ne se rejoue jamais. Le contrôle repose sur quatre barrières :

| Barrière | Mécanisme | Niveau |
|---|---|---|
| 1 | Identifiant unique et non réutilisable | Procédural |
| 2 | Vérification d'absence de reçu antérieur | Procédural |
| 3 | Statut terminal non réactivable | Procédural + état |
| 4 | Historique conservé (`transition_history`) | Procédural |

**Aucune de ces barrières n'est cryptographique.** Un rejeu réussi est une violation **P1** (« fusion non autorisée, décision modifiée ») et peut invalider le résultat (`GC-44`).

Une protection technique n'existe que si l'environnement l'impose et si c'est prouvé (`GC-36`).

---

## 7. Expiration

| Profil | Expiration |
|---|---|
| Lite | Facultative ; si elle est absente, la faiblesse est **explicitement signalée** |
| Standard | Recommandée ; durée fixée dans le mandat **lorsque le risque le justifie** |
| Reinforced | **Obligatoire** |

> **Décision C27 appliquée.** Aucune durée numérique universelle n'est introduite. Le **VALIDATOR** doit décider ou confirmer la durée applicable dans le mandat concerné.

- L'expiration est calculée à partir de `expires_at`.
- `expires_at` est renseigné **lorsque le mandat l'exige** ; sa valeur n'est pas déduite du seul profil.
- Une transition expirée passe à `expired` : elle n'est plus consommable et ne peut **jamais** être réactivée.
- Une transition sans `expires_at` n'expire pas automatiquement : la faiblesse est signalée dans le mandat.
- L'absence de durée par défaut reste un fait `INCONNU` : elle n'est pas devenue une règle chiffrée.

---

## 8. Invalidation

L'autorisation en cours est **suspendue ou invalidée** dès qu'un changement modifie (`F3` §10.5) :

- le périmètre ;
- le sprint ;
- l'action ;
- l'architecture ;
- les critères d'acceptation ;
- le profil de risque ;
- la version du mandat.

Procédure :

1. L'ancienne autorisation est invalidée, jamais réutilisée.
2. Le mandat reçoit une **nouvelle version**.
3. Les documents affectés sont mis à jour.
4. Une **nouvelle transition** est créée, avec un nouvel identifiant.
5. Un **nouveau `GO`** est requis.

Une transition invalidée conserve sa trace : elle n'est pas supprimée.

---

## 9. Divergence état / reçu

Le traitement est défini dans `state_model.md` §7 : gel, blocage, constat, réconciliation, décision de reprise, trace.

**Rappel de la règle (A2) :** `state.json` est la source de vérité de l'état courant ; les reçus sont des preuves d'événements ; toute divergence est une incohérence **bloquante** jusqu'à réconciliation.

Aucune des deux sources ne « gagne » automatiquement. La réconciliation est un acte explicite.

---

## 10. Conservation et historique

- Toute transition est conservée dans `transition_history`, y compris rejetée, expirée ou annulée.
- Tout reçu est conservé avec son sprint.
- Aucune suppression : une transition erronée est annulée et remplacée, jamais effacée (`GC-32`).
- La durée de conservation n'est pas définie dans les sources (`INCONNU`).

---

## 11. Limites

| Limite | Conséquence |
|---|---|
| Le reçu est procédural par défaut | Sa valeur probante dépend de l'environnement |
| Aucun mécanisme cryptographique | Un identifiant peut être recopié |
| Emplacement du reçu ORCHESTRATOR — désormais tranché (C26) | `docs/governance/receipts/` (§5.7) ; plus d'asymétrie sur ce point |
| Aucune durée d'expiration par défaut | Une autorisation peut rester ouverte indéfiniment |
| Aucun contrôle technique de réutilisation | Repose sur la discipline et l'audit |

Ces limites sont **déclarées**, pas masquées : c'est la condition pour que le dispositif soit crédible.

---

## 12. Renvois

| Sujet | Document |
|---|---|
| États et invariants | `protocol/state_model.md` |
| Valeurs de décision | `protocol/decision_policy.md` |
| Matrice des permissions | `protocol/permission_policy.md` |
| Blocage, reprise, incident | `protocol/recovery_policy.md` |
| Forme du reçu | `templates/transition_receipt_template.md` |
| Configuration réelle | `implementations/opencode/agent_permissions.md` |

---

## 13. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 3) — source normative du reçu (C24), `transition_id` (C22) |
| 0.2 | 2026-11-20 | C26 : reçu ORCHESTRATOR dans `docs/governance/receipts/` ; C27 : aucune durée numérique par défaut |
