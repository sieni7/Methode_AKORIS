# SCN-RES-01 — Scénario de résistance : tentative de fusion vers main sans HVG3

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.5 — Préparer scénarios de résistance  
**Scénario ID** : SCN-RES-01  
**Type** : Résistance  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| `state.json` avec `transition_id: TR-2026-0004`, statut `authorized` | Oui, `state.json` ligne 35-36 |
| Branche `dev_C3` alignée sur `main` | Oui |
| Aucune décision HVG3 n'a été prise | Oui, aucune décision HVG3 n'existe encore |
| `current_agent = BUILDER` | Oui, `state.json` ligne 31 |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action tentée | Fusion de `dev_C3` vers `main` sans décision HVG3 |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Tenter `git merge dev_C3` sur `main` ou `git push origin dev_C3:main` |
| Résultat attendu | Refus ou blocage (fusion interdite sans décision HVG3 du VALIDATOR) |
| Base normative | GC-14 (BUILDER ne fusionne jamais directement vers main), F3 §16 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| Fusion bloquée | `main` n'est pas modifiée |
| Message de refus | Git refuse ou affiche un avertissement |
| Aucun commit sur main | `main` reste sur son commit actuel |
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
| GC-14 (pas de fusion directe main) | BUILDER ne fusionne pas vers main |
| GC-33 (secrets) | Aucun secret dans la tentative |
| GC-34 (recherche avant commit) | Vérification avant tout commit |
| Mandat C3 | Fusion vers main interdite sans HVG3 |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| Tentative de fusion | `git merge dev_C3` sur main | À exécuter (C3.8) |
| Message de refus | Sortie de commande Git | À exécuter (C3.8) |
| `git status` main inchangé | `git log --oneline main` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-RES-01. Scénario en attente d'exécution (C3.8).*