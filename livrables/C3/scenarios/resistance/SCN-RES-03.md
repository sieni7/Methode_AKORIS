# SCN-RES-03 — Scénario de résistance : tentative de réutilisation d'un identifiant consommé

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.5 — Préparer scénarios de résistance  
**Scénario ID** : SCN-RES-03  
**Type** : Résistance  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| `state.json` avec `transition_id: TR-2026-0004` | Oui, `state.json` ligne 35 |
| `transition.status` = "authorized" | Oui, `state.json` ligne 36 |
| `TR-2026-0001` est un identifiant consommé (C0) | Oui, `state.json` historique montre TR-2026-0001 consommé |
| Branche `dev_C3` active | Oui |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action tentée | Réutilisation de l'identifiant `TR-2026-0001` pour une nouvelle action |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Tenter de créer une nouvelle transition avec l'identifiant `TR-2026-0001` (déjà consommé lors de C0) |
| Résultat attendu | Refus (INV-04, GC-32 : identifiant consommé jamais réutilisé) |
| Base normative | INV-04 (un identifiant consommé, expiré ou annulé n'est jamais réutilisé), GC-32 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| Réutilisation refusée | `TR-2026-0001` ne peut pas être réutilisé |
| Message de refus | Système ou procédure refuse la réutilisation |
| Nouvel identifiant requis | Un nouvel identifiant `TR-2026-NNNN` doit être créé |
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
| INV-04 (identifiant consommé jamais réutilisé) | TR-2026-0001 ne peut pas être réutilisé |
| GC-32 (identifiant consommé jamais réutilisé) | Même règle |
| GC-33 (secrets) | Aucun secret dans la tentative |
| GC-14 (pas de fusion directe main) | Commit sur dev_C3 |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| Tentative de réutilisation | Tentative de création de transition avec TR-2026-0001 | À exécuter (C3.8) |
| Message de refus | Système ou procédure refuse | À exécuter (C3.8) |
| `state.json` inchangé | `git diff state.json` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-RES-03. Scénario en attente d'exécution (C3.8).*