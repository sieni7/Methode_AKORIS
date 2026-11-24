# C2 — Non-conformité NC-03 : Tests T1-T5 non exécutés, protection main = unknown

**Chantier** : C2 — Vérification technique  
**Tâche** : C2-08 — Corriger non-conformité NC-03 (priorité élevée)  
**Transition** : TR-2026-0003 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C2-verification-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C2` (alignée sur `main`, intègre C0 + C1)  
**Référence** : Non-conformité NC-03 de C1 (tests T1-T5 non exécutés, protection main inconnue)

---

## 1. Objet de la non-conformité NC-03

| Élément | Valeur |
|---|---|
| Non-conformité | NC-03 : Tests T1-T5 non exécutés, protection main = unknown |
| Priorité | Élevée |
| Action C2 demandée | Exécuter les tests T1-T5 et définir des règles de protection de main (règles GC-36, GC-37) |
| Contexte | Aucun test technique n'a été exécuté dans C0 et C1 ; la protection de main reste inconnue |

---

## 2. État des tests T1 à T5

| # | Test | Description | Statut | Justification |
|---|---|---|---|---|
| T1 | BUILDER édite `state.json` directement | Édition via outil `edit` par BUILDER | `NON EXÉCUTÉ` | Aucun environnement d'exécution agent BUILDER disponible |
| T2 | BUILDER écrit `state.json` par shell | `Set-Content`, `>`, `tee` par BUILDER | `NON EXÉCUTÉ` | Aucun environnement d'exécution agent BUILDER disponible |
| T3 | ORCHESTRATOR édite `src/**` | Édition via outil `edit` par ORCHESTRATOR | `NON EXÉCUTÉ` | Aucun environnement d'exécution agent ORCHESTRATOR disponible |
| T4 | Fusion/push non autorisé vers branche protégée (≠ main) | `git merge`, `git push` vers branche protégée | `NON EXÉCUTÉ` | Aucun dépôt de test avec branche protégée configurée |
| T5 | Fusion/push non autorisé vers `main` | `git merge`, `git push` vers `main` | `NON EXÉCUTÉ` | Aucune protection technique de `main` vérifiée |

---

## 3. Règles de protection de `main` (règles GC-36, GC-37)

### 3.1 Règle GC-36 (permissions déclarées vs réelles)

> **GC-36** : Les permissions déclarées sont distinguées des permissions réellement imposées. `unknown` n'est jamais présenté comme une garantie.

Application à `main` :
- Une protection déclarée dans un fichier de configuration n'est pas une protection appliquée
- La protection de `main` est `unknown` tant que T5 n'a pas été exécuté
- Aucune permission n'est classée `technical_enforced` sans preuve d'exécution

### 3.2 Règle GC-37 (indépendance d'audit)

> **GC-37** : L'indépendance d'audit est procédurale par défaut. Elle n'est dite technique que si l'environnement l'impose réellement et si c'est prouvé.

Application à `main` :
- L'indépendance procédurale est assurée par la règle GC-14 (pas de fusion directe vers main)
- L'indépendance technique n'est pas prouvée (aucun test T5)

### 3.3 Mesures compensatoires procédurales

| # | Mesure | Effet | Base |
|---|---|---|---|
| NC-03-1 | Aucune fusion vers `main` sans décision HVG distincte du VALIDATOR | Empêche la fusion non autorisée | GC-14, DP §9 |
| NC-03-2 | Travail exclusivement sur branches dédiées | Isole le travail de `main` | F3 §16, GC-14 |
| NC-03-3 | Commits en Conventional Commits liés aux identifiants de tâche | Traçabilité des modifications | Plan de consolidation §3 |
| NC-03-4 | Recherche de secrets avant commit et avant fusion | Empêche l'exposition de secrets | GC-33, GC-34 |
| NC-03-5 | Vérification du commit sur `main` après toute fusion autorisée | Détecte les écarts post-fusion | Plan de consolidation §3 |

---

## 4. Classification des permissions liées à `main`

| Permission | Rôle | Classification | Justification |
|---|---|---|---|
| Fusion vers `main` | BUILDER | `unknown` | Pas de test T5 exécuté |
| Fusion vers `main` | ORCHESTRATOR | `unknown` | Pas de test T5 exécuté |
| Fusion vers `main` | AUDITOR | `unknown` | Pas de test T5 exécuté |
| Fusion vers `main` | VALIDATOR | Autorise (procédurale) | GC-14, DP §9 |

---

## 5. Preuves et traçabilité

| Élément | Référence | Statut |
|---|---|---|
| Non-conformité NC-03 identifiée | Rapport C1 (C1-C, C1-F) | `directly_verified` |
| Tests T1-T5 définis | `protocol/permission_policy.md` §7.2 | `directly_verified` |
| Tests T1-T5 non exécutés | `agent_permissions.md` §6 | `directly_verified` |
| Protection de `main` | `agent_permissions.md` §7 (C29) | `directly_verified` |
| Règle GC-36 | `protocol/governance_core.md` GC-36 | `directly_verified` |
| Règle GC-37 | `protocol/governance_core.md` GC-37 | `directly_verified` |

---

## 6. Conclusion

La non-conformité NC-03 est **documentée** : les tests T1 à T5 ne sont pas exécutés et la protection de `main` est classée `unknown`. Les mesures compensatoires procédurales sont définies. L'exécution des tests techniques relève de C3 (ou d'un environnement d'exécution des agents).

**Statut NC-03** : ✅ Documentée — tests T1-T5 non exécutés, protection main `unknown`, mesures compensatoires définies.

---
*Fin de NC-03. Non-conformité documentée. Prêt pour NC-04.*