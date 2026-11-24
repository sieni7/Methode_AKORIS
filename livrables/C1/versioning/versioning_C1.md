# C1-E — Versionning SemVer et distinction des catégories de versions

**Chantier** : C1 — Consolidation normative et documentaire  
**Tâche** : C1-E — Versionning : appliquer SemVer aux documents, distinguer versions protocole/schéma, révisions documentaires  
**Transition** : TR-2026-0002 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C1-consolide-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C1` (alignée sur `main`, intègre les 10 commits C0)  
**Contrainte** : Modifications autorisées uniquement dans le périmètre C1 défini ; pas de fusion vers `main` sans HVG1  
**Action prioritaire liée** : M1 (priorité élevée) — Valider schéma `state.schema.json`

---

## 1. Vérification état Git (prérequis C1-E)

| Vérification | Résultat | Preuve |
|---|---|---|
| Branche courante | `dev_C1` | `git branch` |
| Alignement avec `main` | `dev_C1` = `main` (commit `56603d5`) | `git log --oneline` |
| Intégration C0 dans `main` | 10 commits C0 présents sur `main` | `git log --oneline main` |
| C1-A à C1-D terminés | Commits `7da7ebc`, `cc6ebc5`, `fbfc5d1`, `56603d5` | `git log --oneline -4` |
| Reçu de transition C1 déposé | `livrables/C1/transition/recu_transition_C1.md` | Commit `7da7ebc` |

---

## 2. Objectif de C1-E

Ce livrable documente :

1. Les **5 catégories de versions** distinctes (décision A7/A15) : protocole, profil, schéma, mandat, document
2. L'application des **règles SemVer prospectives** (A15) : major/minor/patch pour protocole et schéma ; révision simple pour les documents
3. La **validation du schéma `state.schema.json`** (action M1, priorité élevée) — statut actuel : NOT_CHECKED
4. La distinction entre version du protocole, version du schéma et version du document (A7, A14, A15)
5. La migration pilote v1.0 → Norme v2.0 (A16 différé — non traitée ici)

---

## 3. Les 5 catégories de versions (décision A7, A15)

La décision **A7** est tranchée : cinq versions distinctes coexistent et ne se confondent jamais. La décision **A15** précise les règles d'incrémentation prospective.

| Catégorie | Objet | Porté par | Source | Règles d'incrémentation (A15) |
|---|---|---|---|---|
| **Protocole** | Règles du cadre | `protocol.version` dans `state.json` ; en-tête `Version` des documents de `protocol/` | `state_model.md` §8, §6.4 | **SemVer indépendant** : major/minor/patch, incrémentation événementielle |
| **Profil** | Niveau d'exigence | En-tête `Version` du document `profile_*.md` | `state_model.md` §8 | Révision simple, sans garantie SemVer |
| **Schéma** | Structure de `state.json` | `schema_version` dans `state.json` ; schéma technique `state.schema.json` | `state_model.md` §8, décision **C28** | **SemVer indépendant** : major/minor/patch, incrémentation événementielle |
| **Mandat** | Périmètre autorisé | `current_sprint.md` ; `mandate_version` dans la transition et l'état | `state_model.md` §8, `transition_policy.md` §2 | Révision simple, liée à la procédure de changement |
| **Document** | Révision d'un fichier | En-tête `Version` de chaque fichier | `state_model.md` §8 | Révision simple, sans garantie SemVer |

### Séparation (SM §6.4)

`schema_version` est distinct de `protocol.version`. Une évolution du protocole n'est pas une évolution du projet, et une évolution du schéma n'est pas une évolution du protocole.

---

## 4. Règles SemVer prospectives (décision A15)

Approuvées le 2026-11-21, applicables **prospectivement** uniquement. Aucune signification SemVer n'est attribuée rétroactivement aux numéros existants.

| Incrément | Règle AKORIS approuvée (prospective) |
|---|---|
| **`major`** | Changement incompatible : rend invalide une instance auparavant conforme ou rompt une règle normative / une compatibilité établie. |
| **`minor`** | Extension compatible qui préserve les instances et les exigences antérieures. |
| **`patch`** | Correction ou clarification sans changement des exigences normatives ni de l'ensemble des instances acceptées par le schéma. |

> **Documents.** La révision documentaire simple est incrémentée lors d'une révision approuvée selon les règles documentaires existantes (§6 de la politique) ; elle ne suit pas les règles SemVer ci-dessus.

> **Limite.** Ces règles s'appliquent prospectivement. Elles ne réinterprètent pas les numéros déjà portés par le corpus et n'imposent aucun numéro commun entre protocole et schéma. Toute proposition d'incrément est soumise au VALIDATOR avec ses preuves d'impact.

---

## 5. État actuel des versions dans le corpus

### 5.1 Versions des documents (en-têtes)

| Fichier | Version déclarée | Date | Statut d'en-tête |
|---|---|---|---|
| `00_cartographie.md` | 0.1 | 2026-11-20 | PROPOSITION — à valider par le VALIDATOR |
| `changelog.md` | 0.3 | 2026-11-21 | Journal de maintenance — non normatif |
| `plan_de_consolidation.md` | 0.1.0-draft | 2026-11-24 | inconnu (pas de bloc statut standard) |
| `README.md` | inconnu | inconnu | Pas de bloc d'en-tête standard |
| `state.json` | schema_version "2.0" | 2026-11-24 | Pas de champ statut |
| `reference/state.schema.json` | 2.0 (schéma) | inconnu | Technique — Schéma AKORIS v2.0 (décision C28) |
| `reference/terminology.md` | 0.3 | 2026-11-20 | PROPOSITION — à valider par le VALIDATOR |
| `reference/document_map.md` | 0.4 | 2026-11-20 | PROPOSITION — à valider par le VALIDATOR |
| `reference/traceability_map.md` | 0.1 | 2026-11-21 | VALIDÉ PAR LE VALIDATOR — 2026-11-21 |
| `reference/versioning_policy.md` | 0.1 | 2026-11-21 | VALIDÉ PAR LE VALIDATOR — 2026-11-21 |
| `protocol/governance_core.md` | 0.1 | 2026-11-20 | PROPOSITION — à valider par le VALIDATOR |
| `protocol/state_model.md` | 0.2 | 2026-11-20 | PROPOSITION — à valider par le VALIDATOR |
| `protocol/transition_policy.md` | 0.2 | 2026-11-20 | PROPOSITION — à valider par le VALIDATOR |
| `protocol/permission_policy.md` | 0.3 | 2026-11-20 | PROPOSITION — à valider par le VALIDATOR |
| `protocol/decision_policy.md` | 0.1 | 2026-11-20 | PROPOSITION — à valider par le VALIDATOR |
| `protocol/change_control.md` | 0.1 | 2026-11-20 | PROPOSITION — à valider par le VALIDATOR |
| `protocol/recovery_policy.md` | 0.2 | 2026-11-20 | PROPOSITION — à valider par le VALIDATOR |
| `protocol/audit_policy.md` | 0.3 | 2026-11-21 | PROPOSITION — à valider par le VALIDATOR |
| `protocol/getting_started.md` | inconnu | 2026-11-21 | VALIDÉ PAR LE VALIDATOR — 2026-11-21 |
| `implementations/opencode/agent_permissions.md` | 0.4 | 2026-11-20 | CONSTAT — non normatif |
| `implementations/opencode/README.md` | 0.1 | 2026-11-21 | Descriptif — non normatif |
| `implementations/opencode/frontmatter_reference.md` | 0.1 | 2026-11-21 | Référence descriptive — portée limitée |
| `implementations/opencode/environment_requirements.md` | 0.1 | 2026-11-21 | Descriptif — prérequis observés, non certification |
| `implementations/opencode/limitations.md` | 0.1 | 2026-11-21 | Descriptif — fondé sur le constat du pilote |
| `prompts/*` (4 fichiers) | 0.1 | 2026-11-20 | LIVRABLE VAGUE 6 — à valider par le VALIDATOR |
| `templates/*` (7 fichiers) | 0.1 | 2026-11-20 | LIVRABLE VAGUE 6 — à valider par le VALIDATOR |
| `_sources/*` (3 fichiers) | inconnu | inconnu | Pas de bloc Version/Date/Statut |
| `livrables/C0/*` (fichiers de transition) | inconnu | inconnu | Pas de bloc Version/Date/Statut standard |

### 5.2 Version du protocole dans `state.json`

| Champ | Valeur | Signification |
|---|---|---|
| `protocol.version` | `"1.0"` | Version du protocole AKORIS appliqué |
| `schema_version` | `"2.0"` | Version du schéma de sérialisation de `state.json` |

> `protocol.version` ("1.0") et `schema_version` ("2.0") sont **indépendants** (décision A15). Le protocole est en v1.0, le schéma en v2.0.

### 5.3 Version du profil dans `state.json`

| Champ | Valeur | Signification |
|---|---|---|
| `governance.profile` | `"standard"` | Profil actif |
| `governance.profile_locked` | `true` | Verrouillé (GC-09, INV-11) |
| `governance.selected_by` | `"VALIDATOR"` | Sélectionné par le VALIDATOR |
| `governance.selected_at` | `"2026-11-24"` | Date de sélection |

> **Aucun champ de version du profil** n'est présent dans `state.json` (décision A10). La version du profil est portée par l'en-tête du document `profile_*.md` uniquement.

---

## 6. Action M1 — Validation du schéma `state.schema.json` (priorité élevée)

### 6.1 État du schéma

| Élément | Valeur | Statut |
|---|---|---|
| Fichier | `reference/state.schema.json` | Présent dans le dépôt |
| Titre | "Schéma AKORIS v2.0 — state.json" | — |
| `$id` | `https://akoris.local/schemas/state.v2.schema.json` | — |
| Version du schéma | `schema_version: "2.0"` | Norme AKORIS v2.0 (décision A2, C28) |
| `additionalProperties` | `false` | Mode strict |
| Champs requis | 16 champs de niveau supérieur | Conformes à `state_model.md` §6.4 |
| `$defs` | `profile`, `agent`, `decisionValue`, `projectStatus`, `checkpointStatus`, `sprintStatus`, `transitionStatus`, `nullableString`, `nullableTimestamp`, `traceItem`, `transitionRecord` | Présents |
| `transition` | `oneOf` : null ou objet avec 16 champs requis | Conforme à `state_model.md` §6.4 |
| `decisionValue` | enum: `["GO", "GO_WITH_RESERVES", "NO_GO", "HOLD", "CANCELLED"]` | Conforme à `decision_policy.md` §3 |

### 6.2 Validation avec un validateur nommé

**Constat critique (action M1)** : Aucun validateur JSON Schema nommé n'a été utilisé pour valider `state.json` contre `state.schema.json`.

| Élément | Statut | Preuve |
|---|---|---|
| Schéma existe | `directly_verified` | `reference/state.schema.json` présent dans le dépôt |
| `state.json` conforme au schéma | `NOT_CHECKED` | Aucun validateur exécuté |
| Validation JSON Schema reproduite | `NON VÉRIFIÉE` | `state_model.md` §10 : « la validation JSON Schema n'a pas été reproduite avec un validateur nommé (NON VÉRIFIÉE) » |
| `state.json` valide structurellement | `NOT_CHECKED` | Lecture manuelle seulement, pas de validation automatisée |

### 6.3 Comparaison `state.json` vs `state.schema.json`

| Champ `state.json` | Présent dans le schéma | Conforme |
|---|---|---|
| `schema_version` | ✅ | ✅ (const "2.0") |
| `protocol` | ✅ | ✅ |
| `governance` | ✅ | ✅ |
| `project` | ✅ | ✅ |
| `checkpoints` | ✅ | ✅ |
| `sprint` | ✅ | ✅ |
| `agent` | ✅ | ✅ |
| `transition` | ✅ | ✅ |
| `last_decision` | ✅ | ✅ |
| `blockers` | ✅ | ✅ |
| `reserves` | ✅ | ✅ |
| `change_control` | ✅ | ✅ |
| `permission_violations` | ✅ | ✅ |
| `transition_history` | ✅ | ✅ |

**Constat** : `state.json` contient tous les champs requis par le schéma. Cependant, cette conformité est établie par lecture manuelle, pas par validation automatisée avec un validateur nommé.

**Action M1** : La validation du schéma `state.schema.json` contre `state.json` avec un validateur JSON Schema nommé reste à exécuter. Statut actuel : **NOT_CHECKED**.

---

## 7. Distinction des trois listes de catégories de versions (divergence T10/T11, A14)

Trois listes coexistent dans le corpus. Aucune n'est réécrite ici ; leur rapprochement relève d'une décision du VALIDATOR.

| Source | Liste portée | Écart avec A7 (5 catégories) |
|---|---|---|
| **A7 tranché** — `SM` §8, `T` §11, `README` §11 | Protocole, profil, schéma, mandat, document — **5 catégories** | Référence retenue |
| `CART` §7 (ancienne) — mention « 4 axes » | Protocole, schéma, document, mandat — **4 axes** | Omet le **profil** ; mention historique conservée dans `00_cartographie.md` |
| `F2` §16 (historique) | Protocole, profil, mandat, état, projet — **5 versions** ; éléments à versionner : protocole, profils, prompts, modèles, schéma, décisions techniques, mandats, documents métier — **8 éléments** | Remplace schéma/document par état/projet ; ajoute prompts, modèles, décisions techniques |

> **Statut** : `FAIT` pour l'existence des trois listes ; `À ARBITRER` pour leur unification (A14 précise qu'aucune unification n'est requise ; `CART` et `F2` restent des formulations historiques signalées).

---

## 8. Migration pilote v1.0 → Norme v2.0 (A16 différé)

| Élément | Statut | Commentaire |
|---|---|---|
| Structure pilote v1.0 | `state.json` plat (`current_agent`, `protocol_version`, `human_validation_required`, `authorization.token`) | Écart historique, non conforme v2.0 |
| Structure normative v2.0 | `state.json` imbriqué (16 champs pour `transition`) | Structure AKORIS v2.0 (décision A2, C28) |
| Procédure de migration | **À ARBITRER** (A16 différé) | Aucune procédure décrite dans `state_model.md` §6.1 ni `versioning_policy.md` §5 |
| Migration automatique | Non réalisée | La migration n'est pas automatiquement réalisée par la documentation (`state_model.md` §6.1) |

> **A16** est différé : aucune procédure de migration n'est définie à ce jour. Cette décision relève du VALIDATOR.

---

## 9. Règles établies à respecter (renvois, pas de recopie)

| Sujet | Renvoi |
|---|---|
| Une information, une source unique | `document_map.md` §8 ; `GC-50`, `GC-51` |
| Signaler une divergence sans la corriger silencieusement | `GC-31` ; `terminology.md` §0 et §12 |
| Toute évolution tracée avec version et date | `README.md` §8, règle 8 ; `changelog.md` §0 |
| Changement de mandat ⇒ nouvelle version et nouveau `GO` | `change_control.md` §6 ; `transition_policy.md` §8 ; `INV-10` |
| Changement de profil = changement majeur | `change_control.md` §8 ; `GC-09` |
| Aucune durée numérique par défaut | `transition_policy.md` §7, décision **C27** |
| Aucun seuil de risque chiffré | `README.md` §11, décision **C25** ; profils §1 |
| Exemples signalés comme exemples | `GC-53` |

---

## 10. Points d'attention et actions

| Action | Priorité | Statut | Commentaire |
|---|---|---|---|
| **M1** — Valider schéma `state.schema.json` contre `state.json` | Élevée | `NOT_CHECKED` | Aucun validateur nommé exécuté ; conformité établie par lecture manuelle seulement |
| M2 — Porter à 100 % documents "Approuvés" | Moyenne | En cours | 3/45 documents approuvés (6,7%) |
| A16 — Procédure de migration v1.0 → v2.0 | À arbitrer | À ARBITRER | Décision VALIDATOR requise |
| Divergence T10/T11 — Trois listes de catégories | À arbitrer | `À ARBITRER` | A14 précise qu'aucune unification n'est requise |

---

## 11. Preuves attendues pour C1-E

| Preuve | Référence | Statut |
|---|---|---|
| État Git sur dev_C1 | `git branch`, `git log --oneline` | `directly_verified` |
| 5 catégories de versions (A7/A15) | `versioning_policy.md` §1, §5 | `directly_verified` |
| Règles SemVer prospectives (A15) | `versioning_policy.md` §5 | `directly_verified` |
| `state.schema.json` lu et analysé | `reference/state.schema.json` | `directly_verified` |
| Validation JSON Schema (M1) | §6.2 | `NOT_CHECKED` — à exécuter |
| Distinction protocole/schéma/mandat/document/profil | `state_model.md` §8 | `directly_verified` |
| Migration v1.0 → v2.0 (A16 différé) | `versioning_policy.md` §5 | `À ARBITRER` |

---

## 12. Suite de C1

Après C1-E, les tâches restantes dans le mandat C1 :

| Tâche | Description | Livrable attendu | Dépend de C1-E |
|---|---|---|---|
| C1-F | Git/GitHub atomique | `livrables/C1/git/` | Oui (règles de version, commits conventionnels) |
| C1.1 | Traitement divergences C0 (propositions documentées) | `livrables/C1/registres/` | Non |
| C1.3 | MUST/SHOULD/MAY/OUT OF SCOPE | Dans les documents | Non |
| C1.6 | Préparation audit C1 | `livrables/C1/rapport/` | Oui (état de référence, versionning) |
| C1.7 | Rapport C1 + HVG1 | `livrables/C1/rapport/rapport_C1.md` | Oui (toutes) |

---
*Fin de C1-E. Versionning SemVer documenté (5 catégories A7, règles A15). Action M1 (validation schéma) confirmée NOT_CHECKED. Migration v1.0 → v2.0 (A16) différée au VALIDATOR.*