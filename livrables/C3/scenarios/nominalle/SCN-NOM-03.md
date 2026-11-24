# SCN-NOM-03 — Scénario de validation nominale : vérification des 5 réserves R1-R5

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.4 — Préparer scénarios de validation nominale  
**Scénario ID** : SCN-NOM-03  
**Type** : Validation nominale  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| `state.json` existe | Oui |
| `last_decision.reserves` contient R1 à R5 | Oui, `state.json` lignes 59-65 |
| `reserves` contient R1 à R5 | Oui, `state.json` lignes 69-75 |
| 5 réserves documentées | Oui (R1 à R5) |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action autorisée | Lecture de `state.json`, vérification des réserves |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Vérifier que les 5 réserves R1 à R5 sont présentes dans `state.json` (`last_decision.reserves` et `reserves`) |
| Méthode | Lecture directe de `state.json` |
| Commit | Commit Conventional Commits sur `dev_C3` lié à l'identifiant C3.4 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| 5 réserves présentes | R1, R2, R3, R4, R5 dans `state.json` |
| Réserves correctement libellées | Chaque réserve a un intitulé, une gravité et une consigne |
| Commit traçable | Commit Conventional Commits sur `dev_C3` |
| Aucun document source modifié | `state.json` lu uniquement |

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
| GC-33 (secrets) | Aucun secret dans les réserves |
| GC-34 (recherche avant commit) | Vérification avant le commit |
| GC-13 (pas de modification de state.json) | `state.json` lu uniquement |
| GC-14 (pas de fusion directe main) | Commit sur `dev_C3` |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| `state.json` lu | Racine du dépôt | À exécuter (C3.8) |
| Rapport de validation | `livrables/C3/scenarios/nominalle/rapport_NOM-03.md` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-NOM-03. Scénario en attente d'exécution (C3.8).*