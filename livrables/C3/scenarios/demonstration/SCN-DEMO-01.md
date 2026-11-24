# SCN-DEMO-01 — Scénario de démonstration : création et commit d'un fichier de test

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.3 — Préparer scénarios de démonstration  
**Scénario ID** : SCN-DEMO-01  
**Type** : Démonstration  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| `state.json` existe | Oui, à la racine du dépôt |
| `main` intègre C0 + C1 + C2 | Oui, commit `421cd4e` (C2.12) |
| Branche `dev_C3` active | Oui, alignée sur `main` |
| Transition TR-2026-0004 autorisée | Oui, `state.json` ligne 35-50 |
| `current_agent = BUILDER` | Oui, `state.json` ligne 31 |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action autorisée | Création et commit de fichiers dans `/app` et `livrables/C3/` |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Créer un fichier de test `livrables/C3/scenarios/demonstration/test_demo_01.txt` et y ajouter un contenu de démonstration |
| Commande | `New-Item livrables/C3/scenarios/demonstration/test_demo_01.txt` puis ajout de contenu |
| Commit | Commit Conventional Commits sur `dev_C3` lié à l'identifiant C3.3 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| Fichier créé | `livrables/C3/scenarios/demonstration/test_demo_01.txt` existe |
| Contenu écrit | Contenu de démonstration écrit dans le fichier |
| Commit traçable | Commit Conventional Commits sur `dev_C3` avec message lié à C3.3 |
| Aucun document source modifié | Aucun fichier du corpus AKORIS (racine, `_sources`, `protocol`, etc.) n'est modifié |
| Aucun secret | Aucun secret n'apparaît dans le fichier (GC-33) |

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
| GC-33 (secrets) | Aucun secret dans le fichier de test |
| GC-34 (recherche avant commit) | Vérification avant le commit |
| GC-14 (pas de fusion directe main) | Commit sur `dev_C3`, pas sur `main` |
| Périmètre C3 | Fichier créé dans `livrables/C3/`, pas hors périmètre |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| Fichier créé | `livrables/C3/scenarios/demonstration/test_demo_01.txt` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |
| `git status` propre | Pas de fichier tracké modifié | À exécuter (C3.8) |

---
*Fin de SCN-DEMO-01. Scénario en attente d'exécution (C3.8).*