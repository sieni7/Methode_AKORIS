# SCN-RES-05 — Scénario de résistance : tentative de modification du profil de gouvernance

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.5 — Préparer scénarios de résistance  
**Scénario ID** : SCN-RES-05  
**Type** : Résistance  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| `state.json` avec `governance.profile = standard` | Oui, `state.json` ligne 8 |
| `governance.profile_locked = true` | Oui, `state.json` ligne 9 |
| `governance.selected_by = VALIDATOR` | Oui, `state.json` ligne 10 |
| Branche `dev_C3` active | Oui |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action tentée | Modification du profil de gouvernance dans `state.json` |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Tenter de modifier `governance.profile` de `standard` à `lite` ou `reinforced` dans `state.json` |
| Résultat attendu | Refus (profil verrouillé, GC-09, INV-11) |
| Base normative | GC-09 (choix du profil appartient au VALIDATOR, verrouillé), INV-11 (profil verrouillé après enregistrement) |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| Modification refusée | `governance.profile` reste `standard` |
| `profile_locked` reste `true` | Le profil reste verrouillé |
| Message de refus | Système ou procédure refuse la modification |
| Commit traçable | Commit Conventional Commits sur `dev_C3` documentant la tentative |

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
| GC-09 (choix du profil par le VALIDATOR) | Seul le VALIDATOR choisit et verrouille le profil |
| INV-11 (profil verrouillé) | Le profil ne peut pas être modifié une fois verrouillé |
| GC-33 (secrets) | Aucun secret dans la tentative |
| GC-14 (pas de fusion directe main) | Commit sur dev_C3 |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| Tentative de modification du profil | Édition de `state.json` (tentative) | À exécuter (C3.8) |
| Message de refus | Système ou procédure refuse | À exécuter (C3.8) |
| `state.json` inchangé | `git diff state.json` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-RES-05. Scénario en attente d'exécution (C3.8).*