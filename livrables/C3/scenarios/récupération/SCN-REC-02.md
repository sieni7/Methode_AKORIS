# SCN-REC-02 — Scénario de récupération/reprise : retour à l'état normal après écart

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.6 — Préparer scénarios de récupération/reprise  
**Scénario ID** : SCN-REC-02  
**Type** : Récupération/reprise  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| Écarts détectés (ex: SCN-RES-01) | Oui, écarts potentiels des scénarios de résistance |
| Branche `dev_C3` active | Oui |
| `state.json` non modifié | Oui, `state.json` lu uniquement |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action autorisée | Revenir à l'état antérieur après une action non autorisée |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Revenir à l'état antérieur après une action non autorisée (ex: tentative de fusion vers main) |
| Méthode | `git checkout` ou `git reset` sur les fichiers modifiés par erreur, vérification que `git status` est propre |
| Commit | Commit Conventional Commits sur `dev_C3` lié à l'identifiant C3.6 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| État cohérent rétabli | Aucun fichier hors périmètre n'est modifié |
| `git status` propre | Aucun fichier tracké modifié |
| Aucun document source modifié | Aucun fichier du corpus AKORIS n'est modifié |
| Commit traçable | Commit Conventional Commits sur `dev_C3` |
| Aucun secret | Aucun secret n'apparaît dans les fichiers de reprise |

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
| GC-33 (secrets) | Aucun secret dans les fichiers de reprise |
| GC-34 (recherche avant commit) | Vérification avant le commit |
| GC-13 (pas de modification de state.json) | `state.json` lu uniquement |
| GC-14 (pas de fusion directe main) | Commit sur dev_C3 |
| Périmètre C3 | Revenu à l'état dans le périmètre C3 |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| `git status` propre | Dépôt Git | À exécuter (C3.8) |
| `git diff` vide | Aucun fichier modifié | À exécuter (C3.8) |
| Rapport de reprise | `livrables/C3/scenarios/récupération/rapport_REC-02.md` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-REC-02. Scénario en attente d'exécution (C3.8).*