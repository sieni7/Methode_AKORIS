# C1-F — Git/GitHub atomique

**Chantier** : C1 — Consolidation normative et documentaire  
**Tâche** : C1-F — Git/GitHub : tâches atomiques, branches dédiées, commits conventionnels, audit, acceptation, fusion post-HVG1  
**Transition** : TR-2026-0002 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C1-consolide-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C1` (alignée sur `main`, intègre les 10 commits C0)  
**Contrainte** : Modifications autorisées uniquement dans le périmètre C1 défini ; pas de fusion vers `main` sans HVG1  
**Actions prioritaires liées** : M3 (priorité élevée — protection de `main`, tests T1-T5), B2 (priorité moyenne — règles Git/CI-CD)

---

## 1. Vérification état Git (prérequis C1-F)

| Vérification | Résultat | Preuve |
|---|---|---|
| Branche courante | `dev_C1` | `git branch` |
| Alignement avec `main` | `dev_C1` = `main` (commit `27fa6cc`) | `git log --oneline` |
| Intégration C0 dans `main` | 10 commits C0 présents sur `main` | `git log --oneline main` |
| C1-A à C1-E terminés | Commits `7da7ebc`, `cc6ebc5`, `fbfc5d1`, `56603d5`, `27fa6cc` | `git log --oneline -5` |
| Reçu de transition C1 déposé | `livrables/C1/transition/recu_transition_C1.md` | Commit `7da7ebc` |
| Remote `origin` | `https://github.com/sieni7/Methode_AKORIS.git` | `git remote -v` |
| Branche `dev_C0` poussée sur `origin` | `remotes/origin/dev_C0` présente | `git branch -a` |

---

## 2. Objectif de C1-F

Définir et documenter les règles Git/GitHub applicables au chantier C1 :

1. **Tâches atomiques et branches dédiées** : chaque tâche C1 sur sa propre branche, pas de travail direct sur `main`
2. **Commits conventionnels** : format `type(scope): message`, lié à l'identifiant de tâche
3. **Audit des changements** : vérification des modifications avant fusion
4. **Acceptation et fusion post-HVG1** : fusion vers `main` uniquement après décision HVG1 distincte du VALIDATOR
5. **Protection de `main`** (action M3, priorité élevée) : vérification technique de la protection de `main`
6. **Règles Git/CI-CD applicables** (action B2, priorité moyenne)

---

## 3. Cadre de référence

### 3.1 Règles Git du protocole (F3 §16)

| Règle | Contenu |
|---|---|
| Travail de sprint sur branche dédiée | Le travail se fait sur une branche dédiée, pas directement sur `main` |
| BUILDER ne travaille pas sur `main` | BUILDER ne travaille pas directement sur `main` |
| Commits cohérents et traçables | Chaque tâche terminée produit un commit cohérent ; les commits doivent être traçables |
| Modifications hors mandat signalées | Les modifications hors mandat sont signalées |
| Fusion vers `main` nécessite décision humaine distincte | La fusion vers `main` nécessite une décision humaine distincte |
| Protection technique de `main` vérifiée, pas supposée | La protection technique de `main` doit être vérifiée et non supposée |
| Recherche de secrets avant commit et fusion | Les secrets doivent être recherchés avant commit et avant fusion |

### 3.2 Règle GC-14 (governance_core.md)

> **GC-14** : BUILDER ne fusionne jamais directement vers `main` et n'étend pas silencieusement le périmètre.

### 3.3 Règles Git du plan de consolidation (plan_de_consolidation.md §3)

| Règle | Contenu |
|---|---|
| Branche de chantier depuis `main` | Le BUILDER crée une branche de chantier depuis `main` (ex. `dev_C0`) et ne travaille pas directement sur `main` |
| Commits Conventional Commits | Chaque tâche terminée donne lieu à un commit cohérent Conventional Commits, lié à son identifiant |
| Push des branches autorisées | Pousser les branches/livrables autorisés et conserver les preuves Git |
| Fusion vers `main` après décision | Après fusion autorisée, vérifier le commit sur `main` |
| Chantier suivant depuis `main` mis à jour | Le chantier suivant part de `main` mis à jour et vérifié |

### 3.4 Protection de `main` (permission_policy §5.2)

| Exigence | Niveau |
|---|---|
| Protection de `main` doit être vérifiée, jamais supposée | La protection de `main` doit être **vérifiée, jamais supposée** (F3 §16) |
| Branche protégée sans test = permission `unknown` | Une branche dite « protégée » sans test est une permission `unknown` |
| Fusion exige décision humaine distincte | La fusion exige une décision humaine distincte (GC-14) |

---

## 4. État actuel des branches et commits

### 4.1 Branches locales

| Branche | Commit HEAD | Message | Relation avec `main` |
|---|---|---|---|
| `main` | `27fa6cc` | docs(C1-E): versionning SemVer... | Intègre C0 (10 commits) + C1 (5 commits) |
| `dev_C1` | `27fa6cc` | docs(C1-E): versionning SemVer... | Alignée sur `main` |
| `dev_C0` | `ea42a48` | docs(C0-11,C0-12): rapport C0... | Poussée sur `origin`, non fusionnée dans `main` localement (mais `main` intègre ses commits via le push/pull) |

> **Constat** : `main` intègre les 10 commits C0 et les 5 commits C1. La branche `dev_C1` est alignée sur `main`.

### 4.2 Commits C1 effectués

| # | Commit | Message | Tâche liée |
|---|---|---|---|
| 1 | `7da7ebc` | docs(C1-A): hiérarchie documentaire et prévalence des sources | C1-A + reçu de transition |
| 2 | `cc6ebc5` | docs(C1-B): modèle d'état state.json/state.md | C1-B |
| 3 | `fbfc5d1` | docs(C1-C): permissions, roles, perimetres | C1-C |
| 4 | `56603d5` | docs(C1-D): registre des decisions consolide C0+C1 | C1-D |
| 5 | `27fa6cc` | docs(C1-E): versionning SemVer et distinction des categories de versions | C1-E |

Tous les commits suivent le format **Conventional Commits** : `docs(C1-X): description`.

### 4.3 Fichiers non commités (untracked)

| Fichier | Statut | Commentaire |
|---|---|---|
| `audit_report/` | Untracked | Répertoire d'audit, à créer/utiliser selon C1.6 |
| `livrables/C0/mandat_builder.md` | Untracked | Mandat C0 préexistant, non modifié |
| `livrables/C0/transition/notification_builder.md` | Untracked | Notification C0 préexistante, non modifiée |
| `livrables/C0/transition/recu_transition_C0.md` | Untracked | Reçu C0 préexistant, non modifié |
| `plan_de_consolidation.md` | Untracked | Plan de consolidation, non modifié par C1 |
| `state.json` | Untracked | État opérationnel, non modifié par le BUILDER (GC-13) |

---

## 5. Règles Git/CI-CD proposées pour C1 (action B2, priorité moyenne)

### 5.1 Branches

| Règle | Description |
|---|---|
| Branche dédiée par tâche | Chaque tâche C1 (C1-F, C1.1, C1.3, C1.6, C1.7) sur sa propre branche depuis `dev_C1` |
| Pas de travail direct sur `main` | Conformément à GC-14 et F3 §16 |
| Nommage des branches | `c1f-git-github`, `c11-divergences`, `c13-must-should-may`, `c16-audit`, `c17-rapport` |

### 5.2 Commits

| Règle | Description |
|---|---|
| Format Conventional Commits | `type(scope): message` — ex. `docs(C1-F): règles Git/GitHub atomique` |
| Lien avec identifiant de tâche | Chaque commit lié à son identifiant tâche (C1-F, C1.1, etc.) |
| Un commit par tâche terminée | Pas de commit regroupant plusieurs tâches sans justification |
| Message descriptif | Le message décrit précisément ce qui a été fait et pourquoi |

### 5.3 Push et fusion

| Règle | Description |
|---|---|
| Push sur `dev_C1` | Autorisé dans le cadre C1 |
| Push sur branches de tâche | Autorisé sur branches dédiées depuis `dev_C1` |
| Fusion vers `main` | **Interdite** sans décision HVG1 distincte du VALIDATOR |
| Vérification post-fusion | Après fusion autorisée, vérifier le commit sur `main` |

### 5.4 Protection de `main` (action M3, priorité élevée)

**Constat actuel** : La protection de `main` est classée `unknown` (agent_permissions.md §7, C29). Aucun test T5 n'a été exécuté.

| Test | Description | Statut actuel | Lien C1-F |
|---|---|---|---|
| T5 | Fusion/push non autorisé vers `main` dans un dépôt de test | `NON EXÉCUTÉ` — préparé | C1-F, action M3 |

**Procédure proposée pour vérifier la protection de `main`** :
1. Créer un dépôt de test séparé
2. Tenter une fusion ou un push non autorisé vers `main`
3. Constater le refus ou l'acceptation
4. Classer la protection de `main` comme `technical_enforced` (si refus) ou maintenir `unknown` (si acceptation)

> **Note** : Cette vérification relève de C2 (Vérification technique), pas de C1. C1-F documente le besoin et la procédure, mais l'exécution du test T5 est du ressort de C2.

### 5.5 Secrets

| Règle | Description |
|---|---|
| Recherche avant commit et fusion | Les secrets doivent être recherchés avant commit et avant fusion (F3 §16, GC-34) |
| Aucun secret dans les rapports ni le dépôt | Aucun secret ne doit apparaître dans les rapports ni le dépôt (F3 §2.12, GC-33) |

---

## 6. Audit des changements (C1.6 — préparation)

L'audit des changements C1 est préparé mais non exécuté (relève de C1.6 et de l'auditeur indépendant).

| Élément | Statut | Commentaire |
|---|---|---|
| Mandat C1 | `C1-consolide-v1` | Créé, autorisé par HVG0-B |
| Transition C1 | `TR-2026-0002`, statut `authorized` | Consommé par dépôt du reçu |
| Livrables C1 produits | 6 (C1-A à C1-E + reçu) | Commités sur `dev_C1` |
| Commits C1 | 5 | Tous en Conventional Commits, liés à leurs tâches |
| Branche `dev_C1` | Alignée sur `main` | Prête pour audit |
| Fusion vers `main` | En attente HVG1 | Décision distincte requise |

---

## 7. Points d'attention et actions

| Action | Priorité | Statut | Commentaire |
|---|---|---|---|
| **M3** — Protection de `main` (test T5) | Élevée | `NON EXÉCUTÉ` | Relève de C2 ; C1-F documente le besoin et la procédure |
| **M3** — Tests T1-T4 | Élevée | `NON EXÉCUTÉ` | Relève de C2 ; C1-F documente le besoin |
| **B2** — Règles Git/CI-CD pour C1 | Moyenne | En cours | Ce document (C1-F) établit les règles |
| Vérification post-fusion sur `main` | — | En attente | Après décision HVG1 et fusion autorisée |

---

## 8. Preuves attendues pour C1-F

| Preuve | Référence | Statut |
|---|---|---|
| État Git sur dev_C1 | `git branch`, `git log --oneline` | `directly_verified` |
| 5 commits C1 en Conventional Commits | `git log --oneline dev_C1 -5` | `directly_verified` |
| Branche `dev_C1` alignée sur `main` | `git log --oneline main` vs `dev_C1` | `directly_verified` |
| Règles Git/CI-CD C1 | Ce document (`git_github_C1.md`) | Produit |
| Protection de `main` (M3) | §5.4 | `unknown` — test T5 non exécuté (relève de C2) |
| Procédure de fusion post-HVG1 | §5.3 | Documentée, en attente de décision HVG1 |

---

## 9. Suite de C1

Après C1-F, les tâches restantes dans le mandat C1 :

| Tâche | Description | Livrable attendu | Dépend de C1-F |
|---|---|---|---|
| C1.1 | Traitement divergences C0 (propositions documentées) | `livrables/C1/registres/` | Non |
| C1.3 | MUST/SHOULD/MAY/OUT OF SCOPE | Dans les documents | Non |
| C1.6 | Préparation audit C1 | `livrables/C1/rapport/` | Oui (règles Git, versionning, permissions) |
| C1.7 | Rapport C1 + HVG1 | `livrables/C1/rapport/rapport_C1.md` | Oui (toutes) |

---
*Fin de C1-F. Règles Git/GitHub atomique établies. Protection de `main` classée `unknown` (test T5 non exécuté, relève de C2). Fusion vers `main` en attente de décision HVG1.*