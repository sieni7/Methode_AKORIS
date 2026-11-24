# SCN-REC-03 — Scénario de récupération/reprise : reprise après pause

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.6 — Préparer scénarios de récupération/reprise  
**Scénario ID** : SCN-REC-03  
**Type** : Récupération/reprise  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| `state.json` avec `transition_id: TR-2026-0004`, statut `authorized` | Oui, `state.json` ligne 35-36 |
| Transition TR-2026-0004 non consommée | Oui, `consumed_at = null` |
| `current_agent = BUILDER` | Oui, `state.json` ligne 31 |
| Branche `dev_C3` active | Oui |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action autorisée | Reprendre l'expérimentation après une pause |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Reprendre l'expérimentation après une pause (interruption temporaire) |
| Méthode | Vérifier que la transition est toujours `authorized`, que le reçu est toujours valide, que l'exécution peut reprendre |
| Commit | Commit Conventional Commits sur `dev_C3` lié à l'identifiant C3.6 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| Transition reste valide | `state.json` montre `transition.status = authorized` |
| Reçu toujours valide | `livrables/C3/transition/recu_transition_C3.md` existe et est valide |
| Exécution reprend | L'exécution des scénarios peut reprendre |
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
| GC-33 (secrets) | Aucun secret dans la procédure de reprise |
| GC-34 (recherche avant commit) | Vérification avant le commit |
| GC-13 (pas de modification de state.json) | `state.json` lu uniquement |
| GC-14 (pas de fusion directe main) | Commit sur dev_C3 |
| INV-03 (current_agent = destinataire) | current_agent reste BUILDER |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| `state.json` lu | Racine du dépôt | À exécuter (C3.8) |
| Reçu de transition présent | `livrables/C3/transition/recu_transition_C3.md` | À exécuter (C3.8) |
| Rapport de reprise | `livrables/C3/scenarios/récupération/rapport_REC-03.md` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-REC-03. Scénario en attente d'exécution (C3.8).*