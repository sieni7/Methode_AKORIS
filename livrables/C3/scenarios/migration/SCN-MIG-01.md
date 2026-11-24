# SCN-MIG-01 — Scénario de migration : analyse v1.0 → Norme v2.0

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.7 — Préparer scénarios de migration (si nécessaire)  
**Scénario ID** : SCN-MIG-01  
**Type** : Migration (optionnel)  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| `state.json` avec structure v2.0 | Oui, `state.json` ligne 2 (`schema_version: "2.0"`) |
| Pilote v1.0 identifié | Oui, `state_model.md` §6.1 (écart historique) |
| `state.schema.json` existe | Oui, `reference/state.schema.json` |
| Branche `dev_C3` active | Oui |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action autorisée | Analyse de la nécessité d'une migration, pas de modification effective |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Analyser la nécessité d'une migration du pilote v1.0 vers la Norme v2.0 |
| Méthode | Comparaison de la structure v1.0 (pilote) avec la structure v2.0 (`state.schema.json`), documentation de l'écart |
| Commit | Commit Conventional Commits sur `dev_C3` lié à l'identifiant C3.7 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| Décision documentée | Migration nécessaire ou non, avec justification |
| Écart documenté | Différences entre v1.0 et v2.0 consignées |
| Aucune modification effectuée | Aucune migration n'est réellement exécutée (décision VALIDATOR requise - A16 différé) |
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
| GC-33 (secrets) | Aucun secret dans l'analyse de migration |
| GC-34 (recherche avant commit) | Vérification avant le commit |
| GC-13 (pas de modification de state.json) | `state.json` lu uniquement |
| GC-14 (pas de fusion directe main) | Commit sur dev_C3 |
| A16 différé | Procédure de migration v1.0 → v2.0 en attente de décision VALIDATOR |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| `state.json` lu | Racine du dépôt | À exécuter (C3.8) |
| `state.schema.json` lu | `reference/state.schema.json` | À exécuter (C3.8) |
| Rapport de migration | `livrables/C3/scenarios/migration/rapport_MIG-01.md` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-MIG-01. Scénario en attente d'exécution (C3.8).*