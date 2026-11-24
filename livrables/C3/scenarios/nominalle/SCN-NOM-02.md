# SCN-NOM-02 — Scénario de validation nominale : vérification de current_agent = BUILDER

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.4 — Préparer scénarios de validation nominale  
**Scénario ID** : SCN-NOM-02  
**Type** : Validation nominale  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| `state.json` existe | Oui |
| `transition_id: TR-2026-0004` | Oui, `state.json` ligne 35 |
| `transition.status` = "authorized" | Oui, `state.json` ligne 36 |
| `current_agent = BUILDER` | Oui, `state.json` ligne 31 |
| Branche `dev_C3` active | Oui |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action autorisée | Lecture de `state.json`, vérification du champ `current_agent` |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Vérifier que `current_agent` dans `state.json` est bien `BUILDER` |
| Méthode | Lecture directe de `state.json` |
| Commit | Commit Conventional Commits sur `dev_C3` lié à l'identifiant C3.4 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| `current_agent` = `BUILDER` | Confirmé dans `state.json` |
| `to_agent` = `BUILDER` | Confirmé dans `state.json` (transition TR-2026-0004) |
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
| GC-33 (secrets) | Aucun secret dans `state.json` |
| GC-34 (recherche avant commit) | Vérification avant le commit |
| GC-13 (pas de modification de state.json) | `state.json` lu uniquement |
| GC-14 (pas de fusion directe main) | Commit sur `dev_C3` |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| `state.json` lu | Racine du dépôt | À exécuter (C3.8) |
| Rapport de validation | `livrables/C3/scenarios/nominalle/rapport_NOM-02.md` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-NOM-02. Scénario en attente d'exécution (C3.8).*