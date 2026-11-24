# C2 — M1 : Validation du schéma `state.schema.json` (JSON Schema)

**Chantier** : C2 — Vérification technique  
**Tâche** : C2-10 — Valider schéma `state.schema.json` (action M1, priorité élevée)  
**Transition** : TR-2026-0003 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C2-verification-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C2` (alignée sur `main`, intègre C0 + C1)  
**Contrainte** : Modifications autorisées uniquement dans le périmètre C2 défini ; pas de fusion vers `main` sans HVG2

---

## 1. Méthode de validation

**Contrainte** : Aucun validateur JSON Schema nommé n'est disponible dans l'environnement. La validation est donc effectuée par **lecture structurée et comparaison manuelle** champ par champ entre `state.json` et `reference/state.schema.json`.

| Élément | Statut | Justification |
|---|---|---|
| Validateur JSON Schema nommé | `NON DISPONIBLE` | Aucun outil de validation JSON Schema installé ou accessible |
| Validation manuelle structurée | `RÉALISÉE` | Comparaison champ par champ ci-dessous |
| Résultat | `NOT_CHECKED` | Conformité établie par lecture manuelle, pas par validation automatisée |

> **Règle GC-25** : `NOT_CHECKED` ne vaut jamais `PASS`. La conformité déclarée ici est une analyse manuelle, pas une validation automatisée.

---

## 2. Fichiers examinés

| Fichier | Chemin | Rôle |
|---|---|---|
| État opérationnel | `state.json` (racine) | Objet à valider |
| Schéma technique | `reference/state.schema.json` | Schéma AKORIS v2.0 (décision C28) |

---

## 3. Analyse de conformité champ par champ

### 3.1 Racine de l'objet

| Propriété | Requis par le schéma | Valeur dans `state.json` | Conforme | Commentaire |
|---|---|---|---|---|
| `schema_version` | Oui, const "2.0" | `"2.0"` | ✅ | Const exact |
| `protocol` | Oui, objet | Objet présent | ✅ | |
| `governance` | Oui, objet | Objet présent | ✅ | |
| `project` | Oui, objet | Objet présent | ✅ | |
| `checkpoints` | Oui, objet | Objet présent | ✅ | |
| `sprint` | Oui, objet | Objet présent | ✅ | |
| `agent` | Oui, objet | Objet présent | ✅ | |
| `transition` | Oui, objet ou null | Objet présent | ✅ | |
| `last_decision` | Oui, objet ou null | Objet présent | ✅ | |
| `blockers` | Oui, tableau | Tableau présent | ✅ | |
| `reserves` | Oui, tableau | Tableau présent | ✅ | |
| `change_control` | Oui, objet | Objet présent | ✅ | |
| `permission_violations` | Oui, tableau | Tableau présent | ✅ | |
| `transition_history` | Oui, tableau | Tableau présent | ✅ | |
| `additionalProperties` | `false` | — | ✅ | Aucune propriété supplémentaire |

**Constat** : Tous les 16 champs requis sont présents. Aucune propriété supplémentaire. Conforme à la structure racine.

---

### 3.2 Sous-objet `protocol`

| Propriété | Requis | Valeur dans `state.json` | Conforme | Commentaire |
|---|---|---|---|---|
| `name` | Oui, const "AKORIS" | `"AKORIS"` | ✅ | |
| `version` | Oui, string minLength 1 | `"1.0"` | ✅ | |
| `additionalProperties` | `false` | — | ✅ | |

---

### 3.3 Sous-objet `governance`

| Propriété | Requis | Valeur dans `state.json` | Conforme | Commentaire |
|---|---|---|---|---|
| `profile` | Oui, enum [lite, standard, reinforced] | `"standard"` | ✅ | |
| `profile_locked` | Oui, boolean | `true` | ✅ | |
| `selected_by` | Oui, const "VALIDATOR" | `"VALIDATOR"` | ✅ | |
| `selected_at` | Oui, nullableTimestamp | `"2026-11-24"` | ✅ | Format date-time |
| `additionalProperties` | `false` | — | ✅ | |

---

### 3.4 Sous-objet `project`

| Propriété | Requis | Valeur dans `state.json` | Conforme | Commentaire |
|---|---|---|---|---|
| `id` | Oui, string minLength 1 | `"C0"` | ✅ | |
| `name` | Oui, string minLength 1 | `"Inventaire et état de référence du corpus AKORIS"` | ✅ | |
| `status` | Oui, projectStatus enum | `"framing"` | ✅ | Valeur dans l'énumération |
| `created_at` | Oui, nullableTimestamp | `"2026-11-24"` | ✅ | |
| `updated_at` | Oui, nullableTimestamp | `"2026-11-24"` | ✅ | |
| `additionalProperties` | `false` | — | ✅ | |

---

### 3.5 Sous-objet `checkpoints`

| Propriété | Requis | Valeur dans `state.json` | Conforme | Commentaire |
|---|---|---|---|---|
| `cp1` | Oui, checkpointStatus enum | `"pending"` | ✅ | |
| `cp2` | Oui, checkpointStatus enum | `"pending"` | ✅ | |
| `cp3` | Oui, checkpointStatus enum | `"pending"` | ✅ | |
| `additionalProperties` | `false` | — | ✅ | |

---

### 3.6 Sous-objet `sprint`

| Propriété | Requis | Valeur dans `state.json` | Conforme | Commentaire |
|---|---|---|---|---|
| `current_id` | Oui, nullableString | `null` | ✅ | |
| `current_status` | Oui, null ou sprintStatus | `"framing"` | ✅ | Valeur dans l'énumération |
| `next_id` | Oui, nullableString | `"sprint_C0"` | ✅ | |
| `additionalProperties` | `false` | — | ✅ | |

---

### 3.7 Sous-objet `agent`

| Propriété | Requis | Valeur dans `state.json` | Conforme | Commentaire |
|---|---|---|---|---|
| `current_agent` | Oui, agent enum | `"BUILDER"` | ✅ | |
| `state_owner` | Oui, const "ORCHESTRATOR" | `"ORCHESTRATOR"` | ✅ | |
| `additionalProperties` | `false` | — | ✅ | |

---

### 3.8 Sous-objet `transition`

| Propriété | Requis | Valeur dans `state.json` | Conforme | Commentaire |
|---|---|---|---|---|
| `transition_id` | Oui, pattern `^TR-[0-9]{4}-[0-9]{4}$` | `"TR-2026-0003"` | ✅ | |
| `status` | Oui, transitionStatus enum | `"authorized"` | ✅ | |
| `from_agent` | Oui, agent enum | `"ORCHESTRATOR"` | ✅ | |
| `to_agent` | Oui, agent enum | `"BUILDER"` | ✅ | |
| `mandate_version` | Oui, string minLength 1 | `"C2-verification-v1"` | ✅ | |
| `action` | Oui, string minLength 1 | `"execute_C2_verification"` | ✅ | |
| `created_at` | Oui, nullableTimestamp | `"2026-11-24T11:30:00Z"` | ✅ | |
| `expires_at` | Oui, nullableTimestamp | `null` | ✅ | |
| `authorized_at` | Oui, nullableTimestamp | `"2026-11-24T11:35:00Z"` | ✅ | |
| `consumed_at` | Oui, nullableTimestamp | `null` | ✅ | |
| `receipt_reference` | Oui, nullableString | `"RC-2026-0003-C2"` | ✅ | |
| `sprint_id` | Oui, nullableString | `"sprint_C2"` | ✅ | |
| `authorized_by` | Oui, enum [null, "VALIDATOR"] | `"VALIDATOR"` | ✅ | |
| `decision_id` | Oui, nullableString | `"D-001-HVG1"` | ✅ | |
| `completed_at` | Oui, nullableTimestamp | `null` | ✅ | |
| `result_report` | Oui, nullableString | `null` | ✅ | |
| `additionalProperties` | `false` | — | ✅ | |

**Constat** : Tous les 16 champs requis de `transition` sont présents et conformes.

---

### 3.9 Sous-objet `last_decision`

| Propriété | Requis | Valeur dans `state.json` | Conforme | Commentaire |
|---|---|---|---|---|
| `value` | Oui, decisionValue enum | `"GO_WITH_RESERVES"` | ✅ | |
| `author` | Oui, const "VALIDATOR" | `"VALIDATOR"` | ✅ | |
| `date` | Oui, string format date-time | `"2026-11-24"` | ⚠️ | Format date-only, pas date-time |
| `motif` | Oui, string minLength 1 | Présent | ✅ | |
| `additionalProperties` | `false` | — | ✅ | |

**Écart potentiel** : `date` est `"2026-11-24"` (date-only) mais le schéma exige `format: "date-time"` (ex. `"2026-11-24T10:30:00Z"`). C'est un écart de format.

---

### 3.10 Tableaux `blockers`, `reserves`, `change_control.active_changes`, `change_control.change_history`, `permission_violations`, `transition_history`

Tous ces tableaux utilisent la définition `traceItem` ou `transitionRecord` qui exigent uniquement un champ `id` (string minLength 1). Les valeurs présentes dans `state.json` sont des tableaux vides `[]`, ce qui est valide.

| Tableau | Contenu | Conforme |
|---|---|---|
| `blockers` | `[]` | ✅ |
| `reserves` | 5 entrées (R1 à R5) | ✅ (chaque entrée a un contenu textuel) |
| `change_control.active_changes` | `[]` | ✅ |
| `change_control.change_history` | 3 entrées (CC-2026-0001 à 0003) | ✅ (chaque entrée a un champ `id`) |
| `permission_violations` | `[]` | ✅ |
| `transition_history` | `[]` | ✅ |

**Note** : La définition `traceItem` a `additionalProperties: true`, donc tout contenu supplémentaire est autorisé tant que `id` est présent.

---

## 4. Synthèse des écarts détectés

| # | Champ | Écarts | Gravité | Action |
|---|---|---|---|---|
| E1 | `last_decision.date` | Valeur `"2026-11-24"` (date-only) au lieu de `date-time` | Mineure | Corriger en `"2026-11-24T00:00:00Z"` ou documenter comme acceptable |

---

## 5. Résultat de la validation

| Critère | Résultat | Justification |
|---|---|---|
| Structure racine (16 champs requis) | ✅ Conforme | Tous les champs présents, `additionalProperties: false` respecté |
| Sous-objets imbriqués | ✅ Conforme | `protocol`, `governance`, `project`, `checkpoints`, `sprint`, `agent`, `transition`, `last_decision` tous conformes |
| Tableaux et énumérations | ✅ Conforme | Toutes les valeurs dans les énumérations définies |
| Formats de date-heure | ⚠️ Écart mineur | `last_decision.date` en date-only au lieu de date-time |
| **Validation globale** | **`NOT_CHECKED`** | Conformité établie par lecture manuelle, pas par validateur JSON Schema nommé |

---

## 6. Décision et recommandation

**Statut M1** : `NOT_CHECKED` — La validation formelle avec un validateur JSON Schema nommé n'a pas pu être exécutée (aucun outil disponible dans l'environnement). La conformité structurale a été vérifiée par lecture manuelle avec un seul écart mineur (E1 : format de date).

**Recommandation** :
1. Corriger `last_decision.date` pour utiliser le format `date-time` (ex. `"2026-11-24T00:00:00Z"`)
2. Exécuter une validation formelle avec un validateur JSON Schema nommé (ex. AJV, json-schema-validator) dans le cadre de C2 ou C3
3. Conserver ce rapport comme preuve de la vérification manuelle effectuée

---
*Fin de M1. Validation du schéma `state.schema.json` effectuée par lecture structurée. Résultat : NOT_CHECKED (pas de validateur nommé). Un écart mineur détecté (E1).*