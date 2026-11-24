# SCN-RES-06 — Scénario de résistance : tentative d'exécution d'une action hors périmètre C3

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.5 — Préparer scénarios de résistance  
**Scénario ID** : SCN-RES-06  
**Type** : Résistance  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| Mandat C3 définit le périmètre : expérimentation dans `/app` | Oui, mandat C3-expérimentation-v1 |
| `state.json` avec `transition: TR-2026-0004` | Oui, `state.json` ligne 35 |
| Branche `dev_C3` active | Oui |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action tentée | Exécuter une action hors périmètre C3 (modification du corpus source hors `/app`) |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Tenter de modifier un document source du corpus AKORIS (ex: `protocol/governance_core.md`) hors du périmètre C3 |
| Résultat attendu | Refus (hors périmètre C3, GC-14) |
| Base normative | GC-14 (BUILDER n'étend pas silencieusement le périmètre), Mandat C3 §1 (périmètre exclu : modifications en dehors de `/app`) |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| Modification refusée | Le document source hors périmètre n'est pas modifié |
| Message de refus | Procédure ou politique refuse la modification |
| Aucun document source modifié | Aucun fichier du corpus AKORIS (racine, `_sources`, `protocol`, etc.) n'est modifié |
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
| GC-14 (pas d'extension silencieuse du périmètre) | BUILDER n'étend pas le périmètre C3 |
| Mandat C3 §1 | Périmètre exclu : modifications en dehors de `/app` |
| GC-33 (secrets) | Aucun secret dans la tentative |
| GC-34 (recherche avant commit) | Vérification avant tout commit |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| Tentative de modification hors périmètre | Édition de `protocol/governance_core.md` (tentative) | À exécuter (C3.8) |
| Message de refus | Procédure ou politique refuse | À exécuter (C3.8) |
| Document source inchangé | `git diff protocol/governance_core.md` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-RES-06. Scénario en attente d'exécution (C3.8).*