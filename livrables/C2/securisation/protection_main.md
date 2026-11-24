# C2 — M3 : Protection de `main` (règles et procédures)

**Chantier** : C2 — Vérification technique  
**Tâche** : C2-09 — Protection de `main` (action M3, priorité élevée)  
**Transition** : TR-2026-0003 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C2-verification-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C2` (alignée sur `main`, intègre C0 + C1)  
**Contrainte** : Pas de fusion vers `main` sans décision HVG2 distincte du VALIDATOR

---

## 1. État actuel de la protection de `main`

| Élément | Valeur | Justification |
|---|---|---|
| Protection technique de `main` | `unknown` | Aucun test T5 exécuté ; aucune preuve de refus technique |
| Protection procédurale de `main` | Activée | Règle GC-14, plan de consolidation, mesures compensatoires |
| Tests T1 à T5 | `NON EXÉCUTÉS` | Aucun environnement d'exécution des agents disponible |
| Classification de permission | `unknown` | Conformément à `permission_policy.md` §2.1 |

> **Règle GC-14** : BUILDER ne fusionne jamais directement vers `main` et n'étend pas silencieusement le périmètre.
> **Règle F3 §16** : La protection de `main` doit être vérifiée, jamais supposée.

---

## 2. Mesures compensatoires procédurales (en attendant vérification technique)

Puisque aucune protection technique n'est vérifiée (statut `unknown`), les mesures procédurales suivantes sont appliquées :

### 2.1 Interdiction de fusion directe

| Règle | Contenu | Base normative |
|---|---|---|
| M3-P1 | Aucune fusion vers `main` par le BUILDER | GC-14, plan de consolidation §3 |
| M3-P2 | Aucune fusion vers `main` sans décision HVG distincte du VALIDATOR | DP §9, plan de consolidation §3 |
| M3-P3 | Vérification du commit sur `main` après toute fusion autorisée | Plan de consolidation §3 |

### 2.2 Travail sur branches dédiées

| Règle | Contenu | Base normative |
|---|---|---|
| M3-P4 | Travail exclusivement sur branche dédiée (`dev_C2`) | F3 §16, GC-14 |
| M3-P5 | Pas de travail directement sur `main` | GC-14 |

### 2.3 Opérations Git protégées

| Opération | Statut | Base |
|---|---|---|
| `git merge main*` | Interdit | agent_permissions.md §3.1 (règle 17) |
| `git push --force*` | Interdit | agent_permissions.md §3.1 (règle 18) |
| `git push -f *` | Interdit | agent_permissions.md §3.1 (règle 19) |
| `git checkout main*` | Interdit | agent_permissions.md §3.1 (règle 20) |
| `git switch main*` | Interdit | agent_permissions.md §3.1 (règle 21) |
| `git reset --hard*` | Interdit | agent_permissions.md §3.1 (règle 22) |

### 2.4 Recherche de secrets

| Règle | Contenu | Base normative |
|---|---|---|
| M3-P7 | Recherche de secrets avant commit et avant fusion | GC-33, GC-34 |
| M3-P8 | Aucune donnée sensible dans les rapports ni le dépôt | F3 §2.12, GC-33 |

### 2.5 Traçabilité des commits

| Règle | Contenu | Base normative |
|---|---|---|
| M3-P9 | Commits en Conventional Commits (`type(scope): message`) | Plan de consolidation §3 |
| M3-P10 | Chaque commit lié à un identifiant de tâche C2 | Plan de consolidation §3 |
| M3-P10 | Commits cohérents et traçables | F3 §16 |

---

## 3. Procédure de fusion vers `main` (quand autorisée par HVG2)

Lorsque le VALIDATOR prononcera la décision HVG2, la procédure suivante s'applique :

| # | Étape | Acteur | Justification |
|---|---|---|---|
| 1 | Décision HVG1 (déjà prononcée : GO_WITH_RESERVES) | VALIDATOR | Déjà effectuée |
| 2 | Décision HVG2 (après audit C2) | VALIDATOR | En attente |
| 3 | Fusion `dev_C2` → `main` | ORCHESTRATOR (pas le BUILDER) | GC-14 |
| 4 | Vérification du commit sur `main` | ORCHESTRATOR | Plan de consolidation §3 |
| 5 | Vérification que `main` pointe sur le dernier commit C2 | ORCHESTRATOR | Plan de consolidation §3 |

---

## 4. Classification et statut

| Élément | Classification | Justification |
|---|---|---|
| Protection technique de `main` | `unknown` | Aucun test T5 exécuté ; aucune preuve de refus technique |
| Protection procédurale de `main` | Activée | Mesures M3-P1 à M3-P9 en place |
| Tests T1 à T5 | `NON EXÉCUTÉS` | Aucun environnement d'exécution des agents |
| Règle GC-14 | Respectée | Pas de fusion directe vers `main` par le BUILDER |

---

## 5. Recommandations pour C3

| Recommandation | Acteur | Priorité |
|---|---|---|
| Exécuter le test T5 (fusion/push non autorisé vers `main`) | ORCHESTRATOR / C3 | Élevée |
| Configurer une protection technique de `main` (branche protégée, CI) | ORCHESTRATOR / C3 | Élevée |
| Reclasser la protection de `main` en `technical_enforced` si T5 passe | VALIDATOR | Élevée |
| Maintenir les mesures compensatoires procédurales jusqu'à vérification | BUILDER / ORCHESTRATOR | Continue |

---
*Fin de M3 — Protection de `main`. Protection technique `unknown` ; mesures compensatoires procédurales activées. Fusion vers `main` interdite sans décision HVG2 distincte du VALIDATOR.*