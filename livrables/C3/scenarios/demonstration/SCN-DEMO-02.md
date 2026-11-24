# SCN-DEMO-02 — Scénario de démonstration : dépôt d'un rapport d'expérimentation

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.3 — Préparer scénarios de démonstration  
**Scénario ID** : SCN-DEMO-02  
**Type** : Démonstration  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| `state.json` existe | Oui, à la racine du dépôt |
| `transition_id: TR-2026-0004` autorisé | Oui, `state.json` ligne 35-50 |
| `to_agent = BUILDER` | Oui, `state.json` ligne 38 |
| Branche `dev_C3` active | Oui, alignée sur `main` |
| Répertoire `livrables/C3/rapport/` existe | Oui |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action autorisée | Création de rapports dans `livrables/C3/rapport/` |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Créer un rapport d'expérimentation `livrables/C3/rapport/rapport_demo_02.md` décrivant le déroulement d'une démonstration du method AKORIS |
| Contenu | Description de la démonstration, objectives, méthode, résultats attendus |
| Commit | Commit Conventional Commits sur `dev_C3` lié à l'identifiant C3.3 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| Rapport créé | `livrables/C3/rapport/rapport_demo_02.md` existe |
| Contenu rédigé | Rapport décrivant la démonstration |
| Commit traçable | Commit Conventional Commits sur `dev_C3` avec message lié à C3.3 |
| Aucun document source modifié | Aucun fichier du corpus AKORIS n'est modifié |
| Aucun secret | Aucun secret n'apparaît dans le rapport (GC-33) |

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
| GC-33 (secrets) | Aucun secret dans le rapport |
| GC-34 (recherche avant commit) | Vérification avant le commit |
| GC-14 (pas de fusion directe main) | Commit sur `dev_C3`, pas sur `main` |
| Périmètre C3 | Fichier créé dans `livrables/C3/rapport/`, pas hors périmètre |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| Rapport créé | `livrables/C3/rapport/rapport_demo_02.md` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |
| `git status` propre | Pas de fichier tracké modifié | À exécuter (C3.8) |

---
*Fin de SCN-DEMO-02. Scénario en attente d'exécution (C3.8).*