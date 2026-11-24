# SCN-NOM-04 — Scénario de validation nominale : vérification de l'alignement de dev_C3 sur main

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.4 — Préparer scénarios de validation nominale  
**Scénario ID** : SCN-NOM-04  
**Type** : Validation nominale  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| Branche `dev_C3` existe | Oui |
| Branche `main` existe | Oui |
| `dev_C3` alignée sur `main` | Oui, HEAD sur `421cd4e` (C2.12) |
| 16 commits présents sur `main` (C0 + C1 + C2) | Oui |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action autorisée | Lecture de l'historique Git, comparaison des branches |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Vérifier que `dev_C3` pointe sur le dernier commit C2 et est alignée sur `main` |
| Méthode | `git log --oneline main` et `git log --oneline dev_C3`, comparaison |
| Commit | Commit Conventional Commits sur `dev_C3` lié à l'identifiant C3.4 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| `dev_C3` = `main` | Les deux branches pointent sur le même commit |
| C0 + C1 + C2 intégrés | 16 commits présents sur `main` |
| Commit traçable | Commit Conventional Commits sur `dev_C3` |
| Aucun document source modifié | Aucun fichier modifié |

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
| GC-33 (secrets) | Aucun secret dans l'historique Git |
| GC-34 (recherche avant commit) | Vérification avant le commit |
| GC-14 (pas de fusion directe main) | Lecture de `main` uniquement, pas de fusion |
| Périmètre C3 | Lecture de l'historique Git, pas de modification |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| `git log --oneline main` | Dépôt Git | À exécuter (C3.8) |
| `git log --oneline dev_C3` | Dépôt Git | À exécuter (C3.8) |
| Rapport de validation | `livrables/C3/scenarios/nominalle/rapport_NOM-04.md` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-NOM-04. Scénario en attente d'exécution (C3.8).*