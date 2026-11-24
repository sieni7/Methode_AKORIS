# SCN-NOM-05 — Scénario de validation nominale : vérification de l'absence de secrets dans /app

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.4 — Préparer scénarios de validation nominale  
**Scénario ID** : SCN-NOM-05  
**Type** : Validation nominale  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| Répertoire `/app` existe | Oui (environnement d'expérimentation) |
| Aucun fichier secret attendu | Oui (données fictives ou anonymisées uniquement) |
| Branche `dev_C3` active | Oui |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action autorisée | Lecture des fichiers de `/app`, recherche de secrets |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Vérifier qu'aucun secret n'apparaît dans les fichiers de `/app` (mots de passe, clés, tokens, etc.) |
| Méthode | Scan des fichiers de `/app`, recherche de patterns de secrets |
| Commit | Commit Conventional Commits sur `dev_C3` lié à l'identifiant C3.4 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| Aucun secret détecté | Aucun fichier de `/app` ne contient de secret |
| Commit traçable | Commit Conventional Commits sur `dev_C3` |
| Aucun document source modifié | Aucun fichier du corpus AKORIS n'est modifié |

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
| GC-33 (secrets) | Aucun secret dans les fichiers de `/app` |
| GC-34 (recherche avant commit) | Vérification avant le commit |
| GC-14 (pas de fusion directe main) | Commit sur `dev_C3` |
| Périmètre C3 | Scan de `/app` uniquement |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| Scan de `/app` | Répertoire `/app` | À exécuter (C3.8) |
| Rapport de validation | `livrables/C3/scenarios/nominalle/rapport_NOM-05.md` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-NOM-05. Scénario en attente d'exécution (C3.8).*