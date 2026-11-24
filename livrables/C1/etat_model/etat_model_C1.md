# C1-B — Modèle d'état (state.json / state.md)

**Chantier** : C1 — Consolidation normative et documentaire  
**Tâche** : C1-B — Modèle d'état  
**Transition** : TR-2026-0002 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C1-consolide-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C1` (alignée sur `main`, intègre les 10 commits C0)  
**Contrainte** : Modifications autorisées uniquement dans le périmètre C1 défini ; pas de fusion vers `main` sans HVG1

---

## 1. Vérification état Git (prérequis C1-B)

| Vérification | Résultat | Preuve |
|---|---|---|
| Branche courante | `dev_C1` | `git branch` |
| Alignement avec `main` | `dev_C1` = `main` (commit `ea42a48`) | `git log --oneline` |
| Intégration C0 dans `main` | 10 commits C0 présents sur `main` | `git log --oneline main` |
| Reçu de transition C1 déposé | `livrables/C1/transition/recu_transition_C1.md` | Fichier créé, commité (`7da7ebc`) |
| C1-A terminé | `livrables/C1/hierarchie_doc/hiérarchie_doc.md` | Fichier créé, commité (`7da7ebc`) |

---

## 2. Objectif de C1-B

Recréer et adapter le modèle d'état (`state.json`, `state.md`) pour intégrer :

1. Les résultats de l'inventaire C0 (45 documents, classifications, statuts, décisions, divergences, lacunes)
2. Les états de transition, reçus, cycle de vie (TR-2026-0002)
3. La validation du schéma `state.schema.json` (action M1, priorité élevée)
4. Les points d'attention : 3/45 documents approuvés (6,7%), tests T1-T5 non exécutés, protection de `main` inconnue

---

## 3. État actuel de `state.json` (lecture directe)

`state.json` à la racine du dépôt, lu le 2026-11-24. Il intègre déjà les résultats C0 :

| Champ | Valeur actuelle | Provenance |
|---|---|---|
| `schema_version` | `"2.0"` | Décision A2, C28 (Norme AKORIS v2.0) |
| `protocol.name` | `"AKORIS"` | — |
| `protocol.version` | `"1.0"` | — |
| `governance.profile` | `"standard"` | Décision VALIDATOR |
| `governance.profile_locked` | `true` | GC-09, INV-11 |
| `governance.selected_by` | `"VALIDATOR"` | — |
| `governance.selected_at` | `"2026-11-24"` | — |
| `project.id` | `"C0"` | Chantier C0 |
| `project.name` | `"Inventaire et état de référence du corpus AKORIS"` | — |
| `project.status` | `"framing"` | État du projet C0 |
| `project.created_at` / `updated_at` | `"2026-11-24"` | — |
| `checkpoints.cp1/cp2/cp3` | `"pending"` | Non validés |
| `sprint.current_id` | `null` | Aucun sprint courant |
| `sprint.current_status` | `"framing"` | — |
| `sprint.next_id` | `"sprint_C0"` | — |
| `agent.current_agent` | `"BUILDER"` | Mis à jour pour C1 |
| `agent.state_owner` | `"ORCHESTRATOR"` | GC-12 |
| `transition.transition_id` | `"TR-2026-0002"` | Transition C1 |
| `transition.status` | `"authorized"` | Autorisée par VALIDATOR |
| `transition.from_agent` | `"ORCHESTRATOR"` | — |
| `transition.to_agent` | `"BUILDER"` | Destinataire C1 |
| `transition.mandate_version` | `"C1-consolide-v1"` | Mandat C1 |
| `transition.action` | `"execute_C1_consolidation"` | — |
| `transition.sprint_id` | `"sprint_C1"` | — |
| `transition.created_at` | `"2026-11-24T11:00:00Z"` | — |
| `transition.authorized_at` | `"2026-11-24T11:05:00Z"` | Acte VALIDATOR |
| `transition.authorized_by` | `"VALIDATOR"` | — |
| `transition.decision_id` | `"D-001-HVG0-B"` | Décision HVG0-B |
| `transition.consumed_at` | `null` | Non encore consommé (reçu déposé, pas encore consommé techniquement) |
| `transition.receipt_reference` | `"RC-2026-0002-C1"` | Référence reçue C1 |
| `transition.completed_at` | `null` | C1 en cours |
| `transition.result_report` | `null` | Rapport C1 à produire |
| `last_decision.id` | `"D-001-HVG0"` | Décision C0 |
| `last_decision.value` | `"GO_WITH_RESERVES"` | HVG0 |
| `last_decision.author` | `"VALIDATOR"` | — |
| `last_decision.date` | `"2026-11-24"` | — |
| `last_decision.motif` | Voir `state.json` lignes 52-66 | — |
| `last_decision.perimetre` | Inventaire et état de référence C0 | — |
| `last_decision.reserves` | R1 à R5 | 5 réserves C0 |
| `blockers` | `[]` | Aucun bloqueur |
| `reserves` | R1 à R5 | 5 réserves C0 |
| `change_control.active_changes` | `[]` | Aucun changement actif |
| `change_control.change_history` | CC-2026-0001 à 0003 | 3 entrées (C0, audit C0, fusion C0→main) |
| `permission_violations` | `[]` | Aucune violation |

### Constat : `state.json` intègre déjà les résultats C0

Le fichier `state.json` a été mis à jour par l'ORCHESTRATOR pour refléter :
- La fin de C0 avec HVG0-B GO_WITH_RESERVES
- La fusion `dev_C0` → `main` (CC-2026-0003)
- La transition C1 (TR-2026-0002, `authorized`, `current_agent: BUILDER`)
- Les 5 réserves R1-R5

---

## 4. État actuel de `state.md`

`state.md` **n'existe pas** dans le dépôt. Conformément à GC-08 et INV-08 :
- `state.md` est une **vue générée** à partir de `state.json`
- Il ne doit **jamais** être édité manuellement
- Il ne doit **jamais** devenir une source concurrente de `state.json`

**Point d'attention C1-B** : `state.md` est absent du corpus. Sa génération doit être prévue dans C1 (ou documentée comme manquante).

---

## 5. Validation du schéma `state.schema.json` (action M1, priorité élevée)

### 5.1 État du schéma

| Élément | Valeur | Statut |
|---|---|---|
| Fichier | `reference/state.schema.json` | Présent dans le dépôt |
| Titre | "Schéma AKORIS v2.0 — state.json" | — |
| `$id` | `https://akoris.local/schemas/state.v2.schema.json` | — |
| Version | `schema_version: "2.0"` | Norme AKORIS v2.0 (décision A2, C28) |
| `additionalProperties` | `false` | Mode strict |
| Champs requis | 16 champs de niveau supérieur | Conformes à `state_model.md` §6.4 |
| `$defs` complets | `profile`, `agent`, `decisionValue`, `projectStatus`, `checkpointStatus`, `sprintStatus`, `transitionStatus`, `nullableString`, `nullableTimestamp`, `traceItem`, `transitionRecord` | Présents |
| `transition` | `oneOf` : null ou objet avec 16 champs requis | Conforme à `state_model.md` §6.4 |

### 5.2 Validation avec un validateur nommé

**Constat critique (action M1)** : Aucun validateur JSON Schema nommé n'a été utilisé pour valider `state.json` contre `state.schema.json`.

| Élément | Statut | Preuve |
|---|---|---|
| Schéma existe | `directly_verified` | `reference/state.schema.json` présent |
| `state.json` conforme au schéma | `NOT_CHECKED` | Aucun validateur exécuté |
| Validation JSON Schema reproduite | `NON VÉRIFIÉE` | `state_model.md` §10 : « la validation JSON Schema n'a pas été reproduite avec un validateur nommé (NON VÉRIFIÉE) » |

**Action M1** : La validation du schéma `state.schema.json` contre `state.json` reste à exécuter. C'est une action prioritaire élevée pour C1.

---

## 6. Intégration des résultats C0 dans le modèle d'état

Les résultats C0 sont déjà intégrés dans `state.json` (voir §3). Voici le récapitulatif de l'intégration :

| Résultat C0 | Intégré dans `state.json` | Champ |
|---|---|---|
| Décision HVG0-B GO_WITH_RESERVES | ✅ | `last_decision` |
| 5 réserves R1-R5 | ✅ | `last_decision.reserves` + `reserves` |
| Transition C1 TR-2026-0002 | ✅ | `transition` |
| current_agent = BUILDER | ✅ | `agent.current_agent` |
| Fusion dev_C0 → main | ✅ | `change_control.change_history` (CC-2026-0003) |
| Inventaire C0 (45 documents) | ❌ | Pas de champ dans `state.json` — état de référence C0 est dans `livrables/C0/reference/référence_c0.md` |
| Classification C0-04 | ❌ | Pas de champ dans `state.json` |
| Statuts C0-09 | ❌ | Pas de champ dans `state.json` |

**Constat** : `state.json` est l'état opérationnel du projet, pas l'état de référence documentaire. Les résultats documentaires de C0 vivent dans `livrables/C0/` (état de référence figé), pas dans `state.json`. Cette distinction est conforme à la réserve R4.

---

## 7. Points d'attention C1-B

### 7.1 Taux d'approbation des documents (3/45 = 6,7%)

| Statut | Nombre | Pourcentage |
|---|---|---|
| Approuvé | 3 | 6,7 % |
| Proposé | 24 | 53,3 % |
| Non vérifié | 18 | 40,0 % |
| **Total** | **45** | **100 %** |

Les 3 documents approuvés sont les livrables V7 validés par le VALIDATOR le 2026-11-21 : `protocol/getting_started.md`, `reference/traceability_map.md`, `reference/versioning_policy.md`.

**Action M2 (priorité moyenne)** : Porter à 100 % de documents "Approuvés" — à planifier dans C1.

### 7.2 Tests T1-T5 non exécutés

| Test | Description | Statut |
|---|---|---|
| T1 | BUILDER édite `state.json` | `NON EXÉCUTÉ` |
| T2 | BUILDER écrit `state.json` par shell | `NON EXÉCUTÉ` |
| T3 | ORCHESTRATOR édite `src/**` | `NON EXÉCUTÉ` |
| T4 | Fusion/push non autorisé vers branche protégée (≠ main) | `NON EXÉCUTÉ` |
| T5 | Fusion/push non autorisé vers `main` | `NON EXÉCUTÉ` — préparé |

**Action M3 (priorité élevée)** : Exécuter les tests T1-T5 et protéger `main`. Dépend de C2 (Vérification technique).

### 7.3 Protection de `main`

| Élément | Statut | Preuve |
|---|---|---|
| Protection technique de `main` | `unknown` | `agent_permissions.md` §7 (C29) |
| Test T5 | `NON EXÉCUTÉ` | — |
| Règle GC-14 | BUILDER ne fusionne jamais directement vers `main` | Respectée |

### 7.4 `state.md` absent

| Élément | Statut | Conséquence |
|---|---|---|
| Fichier `state.md` | Absent du dépôt | Vue générée non produite |
| Règle INV-08 | `state.md` n'est jamais édité manuellement | À générer, pas à écrire |

---

## 8. Adaptations proposées pour C1 (sans modification de `state.json`)

Conformément à GC-12 (ORCHESTRATOR est le seul rédacteur normal de `state.json`), le BUILDER **ne modifie pas** `state.json` directement. Les adaptations proposées ci-dessous sont des recommandations pour l'ORCHESTRATOR :

| Adaptation | Champ concerné | Justification | Acteur |
|---|---|---|---|
| Passer `project.status` de `"framing"` à `"in_progress"` | `project.status` | C1 démarre, le projet de consolidation est en cours | ORCHESTRATOR |
| Ajouter `project.updated_at` à la date de début C1 | `project.updated_at` | Traçabilité de l'évolution | ORCHESTRATOR |
| Passer `transition.status` de `"authorized"` à `"consumed"` après dépôt du reçu | `transition.status` | Réception de transition C1 effectuée | BUILDER (via reçu) |
| Passer `transition.completed_at` à la date de fin C1 | `transition.completed_at` | À l'achèvement de C1 | BUILDER |
| Ajouter `transition.result_report` vers `livrables/C1/rapport/rapport_C1.md` | `transition.result_report` | Rapport C1 | BUILDER |
| Générer `state.md` à partir de `state.json` | N/A (fichier généré) | Vue lisible requise | ORCHESTRATOR |

---

## 9. Preuves attendues pour C1-B

| Preuve | Référence | Statut |
|---|---|---|
| État Git sur dev_C1 | `git branch`, `git log --oneline` | `directly_verified` |
| Lecture de `state.json` | `state.json` (racine) | `directly_verified` |
| Lecture de `state.schema.json` | `reference/state.schema.json` | `directly_verified` |
| Constat `state.md` absent | Vérification du dépôt | `directly_verified` |
| Modèle d'état C1 | Ce document (`etat_model_C1.md`) | Produit |
| Validation schéma (M1) | §5.2 | `NOT_CHECKED` — à exécuter (action M1) |

---

## 10. Suite de C1

Après C1-B, les tâches suivantes sont prévues dans le mandat C1 :

| Tâche | Description | Livrable attendu | Dépend de C1-B |
|---|---|---|---|
| C1-C | Permissions, rôles | `livrables/C1/permissions/` | Non |
| C1-D | Registres décisions | `livrables/C1/registres/` | Non |
| C1-E | Versionning SemVer | `livrables/C1/versioning/` | Oui (schéma state.json) |
| C1-F | Git/GitHub atomique | `livrables/C1/git/` | Non |
| C1.1 | Traitement divergences C0 | `livrables/C1/registres/` | Non |
| C1.3 | MUST/SHOULD/MAY/OUT OF SCOPE | Dans les documents | Non |
| C1.6 | Préparation audit C1 | `livrables/C1/rapport/` | Oui (état de référence) |
| C1.7 | Rapport C1 + HVG1 | `livrables/C1/rapport/rapport_C1.md` | Oui (toutes) |

---
*Fin de C1-B. Modèle d'état documenté. Action M1 (validation schéma) identifiée comme NOT_CHECKED. Réserve R4 maintenue (distinction état de référence C0 vs state.json).*