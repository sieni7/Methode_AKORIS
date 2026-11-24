# SCN-NOM-01 — Scénario de validation nominale : vérification de la structure de state.json

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.4 — Préparer scénarios de validation nominale  
**Scénario ID** : SCN-NOM-01  
**Type** : Validation nominale  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| `state.json` existe à la racine | Oui |
| `reference/state.schema.json` existe | Oui |
| `state.json` respecte la structure v2.0 | À vérifier |
| `schema_version` = "2.0" | Oui, `state.json` ligne 2 |
| Branche `dev_C3` active | Oui |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action autorisée | Lecture de `state.json` et `state.schema.json`, comparaison structurelle |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Vérifier la conformité structurelle de `state.json` contre `reference/state.schema.json` (champ par champ, 16 champs requis) |
| Méthode | Lecture structurée, comparaison manuelle |
| Commit | Commit Conventional Commits sur `dev_C3` lié à l'identifiant C3.4 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| Conformité structurelle | `state.json` contient tous les 16 champs requis par le schéma v2.0 |
| Aucun champ supplémentaire | `additionalProperties: false` respecté |
| Commit traçable | Commit Conventional Commits sur `dev_C3` |
| Aucun document source modifié | `state.json` et `state.schema.json` lus seulement, pas modifiés |

---

## 5. Résultat observé

| Élément | Valeur |
|---|---|
| Statut | Non encore exécuté (à remplir pendant C3.8) |
| Observé | Non encore exécuté |
| Preuve | Non encore exécuté |

---

## 6. Écart

| Élément | Valeur |
|---|---|
| Statut | Non déterminé (à remplir pendant C3.9) |
| Description | Non déterminé |

---

## 7. Impact

| Élément | Valeur |
|---|---|
| Statut | Non déterminé (à remplir pendant C3.9) |
| Description | Non déterminé |

---

## 8. Règles de sécurité applicables

| Règle | Application |
|---|---|
| GC-33 (secrets) | Aucun secret dans les fichiers lus |
| GC-34 (recherche avant commit) | Vérification avant le commit du rapport |
| GC-13 (pas de modification de state.json) | `state.json` lu uniquement, pas modifié |
| GC-14 (pas de fusion directe main) | Commit sur `dev_C3`, pas sur `main` |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| `state.json` lu | Racine du dépôt | À exécuter (C3.8) |
| `state.schema.json` lu | `reference/state.schema.json` | À exécuter (C3.8) |
| Rapport de validation | `livrables/C3/scenarios/nominalle/rapport_NOM-01.md` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-NOM-01. Scénario en attente d'exécution (C3.8).*