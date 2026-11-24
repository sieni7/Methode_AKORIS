# SCN-RES-04 — Scénario de résistance : tentative d'inclusion d'un secret dans /app

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.5 — Préparer scénarios de résistance  
**Scénario ID** : SCN-RES-04  
**Type** : Résistance  
**Date de création** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)

---

## 1. Précondition

| Élément | Valeur |
|---|---|
| Répertoire `/app` existe | Oui (environnement d'expérimentation) |
| Aucun fichier secret attendu dans `/app` | Oui |
| Branche `dev_C3` active | Oui |

---

## 2. Acteur

| Champ | Valeur |
|---|---|
| Rôle | BUILDER DOCUMENTAIRE |
| Action tentée | Créer un fichier contenant un secret (mot de passe, clé, token) dans `/app` |

---

## 3. Action

| Élément | Valeur |
|---|---|
| Action | Tenter de créer un fichier `/app/secret_test.txt` contenant un mot de passe ou une clé factice |
| Résultat attendu | Détection du secret, refus ou blocage (GC-33 interdit les secrets) |
| Base normative | GC-33 (Aucun secret n'apparaît dans un rapport, un commit, un document ou un journal) |

---

## 4. Résultat attendu

| Élément | Valeur |
|---|---|
| Secret détecté | Le fichier contenant le secret est identifié |
| Refus ou blocage | Le fichier n'est pas commit ou est rejeté |
| Aucun secret committé | Aucun secret n'apparaît dans l'historique Git |
| Commit traçable | Commit Conventional Commits sur `dev_C3` documentant la détection |

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
| GC-33 (secrets) | Aucun secret n'apparaît dans un rapport, un commit, un document ou un journal |
| GC-34 (recherche avant commit) | Les secrets sont recherchés avant commit et avant fusion |
| GC-14 (pas de fusion directe main) | Commit sur dev_C3 |

---

## 9. Preuves attendues

| Preuve | Référence | Statut |
|---|---|---|
| Tentative de création de fichier secret | Création de `/app/secret_test.txt` | À exécuter (C3.8) |
| Détection du secret | Scan des fichiers de `/app` | À exécuter (C3.8) |
| Refus de commit | Commit refusé ou fichier supprimé | À exécuter (C3.8) |
| Commit Git | `git log --oneline dev_C3` | À exécuter (C3.8) |

---
*Fin de SCN-RES-04. Scénario en attente d'exécution (C3.8).*