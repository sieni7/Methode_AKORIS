# Reçu de transition — C3 Expérimentation dans /app

**Identifiant de transition** : TR-2026-0004  
**Destinataire** : BUILDER DOCUMENTAIRE  
**Date de dépôt** : 2026-11-24  
**Déposé par** : BUILDER DOCUMENTAIRE

---

## 1. Contenu minimal normatif (TP §5.3)

| Champ | Valeur |
|---|---|
| `transition_id` | TR-2026-0004 |
| `received_by` | BUILDER |
| `sprint_id` | sprint_C3 |
| `action` | run_experiments |
| `mandate_version` | C3-expérimentation-v1 |
| `received_at` | 2026-11-24 |
| `scope_acknowledged` | Expérimentation dans `/app` — validation du method AKORIS dans un environnement contrôlé, périmètre C3 défini (scénarios de démonstration, nominale, résistance, récupération, migration le cas échéant), livrables dans `livrables/C3/` |
| `exclusions_acknowledged` | Aucune expérience en dehors de `/app` sans autorisation explicite ; aucun scénario non autorisé par le mandat C3 ; aucune modification du method AKORIS sans décision HVG3 distincte ; aucun accès à des données sensibles sans anonymisation ; aucun scénario violant GC-33 (secrets) ou GC-34 (permissions) |

---

## 2. Champs de correspondance avec la transition et l'état

| Champ | Origine | Valeur |
|---|---|---|
| `from_agent` | Anatomie de la transition | ORCHESTRATOR |
| `to_agent` | Anatomie de la transition | BUILDER |
| `project_id` | state.json → project.id | C3 (projet d'expérimentation technique) |
| Statut de la transition au dépôt | state.json → transition.status | authorized |
| `created_at` | Anatomie de la transition | 2026-11-24T11:30:00Z |
| `authorized_at` | Acte du VALIDATOR | 2026-11-24T11:35:00Z |
| `authorized_by` | Acte du VALIDATOR | VALIDATOR |
| `decision_id` | Acte du VALIDATOR | D-001-HVG2 |
| `consumed_at` | Consommation | 2026-11-24 (dépose du présent reçu) |
| `expires_at` | Mandat / profil | Non requis (aucune durée par défaut, C27) |
| `result_report` | Achèvement | livrables/C3/rapport/rapport_C3.md (à produire) |
| `completed_at` | Achèvement | Non atteint (C3 en cours, décision HVG3 distincte requise) |

---

## 3. Contrôles avant consommation (TP §5.4)

| # | Contrôle | Résultat | Preuve ou remarque |
|---|---|---|---|
| 1 | Identifiant présent dans l'historique | VALIDÉ | TR-2026-0004 tracé dans `state.json` |
| 2 | Aucun reçu antérieur pour cet identifiant | VALIDÉ | Aucun reçu préalable pour TR-2026-0004 (INV-04) |
| 3 | Statut `authorized` | VALIDÉ | Décision HVG2 GO_WITH_RESERVES VALIDATOR du 24 novembre 2026 |
| 4 | Transition non expirée | VALIDÉ | Aucun délai par défaut (C27) ; mandat C3-expérimentation-v1 en vigueur |
| 5 | Destinataire = `current_agent` | VALIDÉ | `current_agent` = BUILDER dans `state.json` |
| 6 | Émetteur = agent précédent | VALIDÉ | ORCHESTRATOR a émis la transition (from_agent = ORCHESTRATOR) |
| 7 | `mandate_version` = mandat courant | VALIDÉ | C3-expérimentation-v1 correspond au mandat C3 |
| 8 | Action inscrite au mandat | VALIDÉ | run_experiments ∈ mandat C3-expérimentation-v1 |
| 9 | Périmètre explicite | VALIDÉ | Périmètre C3 défini dans le mandat C3 (expérimentation dans `/app`) |

**Aucun `NOT_CHECKED` n'a été compté comme `PASS`** (GC-25, DP §5.2).

---

## 4. Preuves jointes

| # | Preuve | Statut | Référence |
|---|---|---|---|
| 1 | Décision VALIDATOR HVG2 GO_WITH_RESERVES | `directly_verified` | `state.json` (`decision_id: D-001-HVG2`, `transition.status: authorized`) |
| 2 | Transition TR-2026-0004 autorisée | `directly_verified` | `state.json` (`transition_id: TR-2026-0004`, `to_agent: BUILDER`, `current_agent: BUILDER`) |
| 3 | Branche dev_C3 alignée sur main (C0 + C1 + C2) | `directly_verified` | `git log --oneline dev_C3` — HEAD sur `421cd4e` (dernier commit C2) |
| 4 | Fusion dev_C2 → main effectuée | `directly_verified` | `git log --oneline main` — HEAD sur `421cd4e` (commits C0 + C1 + C2) |
| 5 | Mandat C3 présent | `directly_verified` | Mandat C3-expérimentation-v1 (communiqué par ORCHESTRATOR) |
| 6 | Aucune modification source C3 | `declared_only` | À vérifier après exécution des tâches C3 |

---

## 5. Destination du reçu — mapping C26

| Destinataire | Emplacement du reçu |
|---|---|
| BUILDER | `livrables/C3/transition/recu_transition_C3.md` |

**Déposé par** : BUILDER DOCUMENTAIRE  
**Date de dépôt** : 2026-11-24

---

## 6. Limites du reçu

| Limite à rappeler | État |
|---|---|
| Permissions | `unknown` — aucune garantie sans test contradictoire (T1 à T5 non exécutés, voir M3) |
| Protection de `main` | `unknown` — T5 préparé, non exécuté |
| T1 à T5 | `NON EXÉCUTÉS` (action M3 priorité élevée) |
| Décision HVG3 | Non prise à cette étape ; sera prononcée après exécution C3 et audit |

Le reçu est une preuve procédurale par défaut. Il n'est ni une preuve cryptographique, ni une preuve d'exécution, ni une preuve de qualité. Sa valeur probante dépend de l'environnement : voir `permission_policy.md` et `implementations/opencode/agent_permissions.md`.

Un reçu ne se modifie pas après dépôt : une correction produit un nouvel événement, pas une réécriture (TP §5.5). Un `transition_id` possède au plus un reçu (INV-04).

---
*Réception de transition C3 déposée par le BUILDER DOCUMENTAIRE le 2026-11-24. Prêt pour commencer les tâches C3 (priorité : C3.1 définir périmètre et conditions de sécurité).*