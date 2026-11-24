# SCN-DEMO-03 — Scénario de démonstration : création d'un sous-dossier de test dans /app

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.3 — Préparer scénarios de démonstration  
**Scénario ID** : SCN-DEMO-03  
**Type** : Démonstration  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| Répertoire `/app` existe | Oui (environnement d'expérimentation) |
| Branche `dev_C3` active | Oui, alignée sur `main` |
| Transition TR-2026-0004 autorisée | Oui, `state.json` ligne 35-50 |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action autorisée | Création de dossiers et fichiers dans `/app` |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Créer un sous-dossier `/app/test_demo_03/` et y ajouter un fichier scénario de démonstration décrivant le déroulement d'un test du method AKORIS |
| Contenu | Description du scénario de test, préconditions, étapes, résultats attendus |
| Commit | Commit Conventional Commits sur `dev_C3` lié à l'identifiant C3.3 |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| Sous-dossier créé | `/app/test_demo_03/` existe |
| Fichier scénario créé | Fichier de scénario écrit dans le sous-dossier |
| Commit traçable | Commit Conventional Commits sur `dev_C3` avec message lié à C3.3 |
| Aucun document source modifié | Aucun fichier du corpus AKORIS n'est modifié |
| Aucun secret | Aucun secret n'apparaît dans le fichier (GC-33) |

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
| GC-33 (secrets) | Aucun secret dans le fichier de scénario |
| GC-34 (recherche avant commit) | Vérification avant le commit |
| GC-14 (pas de fusion directe main) | Commit sur `dev_C3`, pas sur `main` |
| Périmètre C3 | Fichier créé dans `/app`, pas hors périmètre |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| Sous-dossier créé | `/app/test_demo_03/` | À exécuter (C3.8) |
| Fichier scénario créé | `/app/test_demo_03/scenario_demo_03.txt` | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |
| `git status` propre | Pas de fichier tracké modifié | À exécuter (C3.8) |

---
*Fin de SCN-DEMO-03. Scénario en attente d'exécution (C3.8).*