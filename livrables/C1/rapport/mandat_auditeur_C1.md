# C1.6 — Préparation audit C1 (mandat AUDITOR)

**Chantier** : C1 — Consolidation normative et documentaire  
**Tâche** : C1.6 — Préparation audit C1 (préparer mandat AUDITOR C1)  
**Transition** : TR-2026-0002 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C1-consolide-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C1` (alignée sur `main`, intègre les 10 commits C0)  
**Contrainte** : Pas de correction silencieuse des documents sources (GC-31) — le BUILDER prépare le mandat, l'AUDITOR exécute l'audit

---

## 1. Vérification état Git (prérequis C1.6)

| Vérification | Résultat | Preuve |
|---|---|---|
| Branche courante | `dev_C1` | `git branch` |
| Alignement avec `main` | `dev_C1` = `main` (commit `01c6bb6`) | `git log --oneline` |
| Intégration C0 dans `main` | 10 commits C0 présents sur `main` | `git log --oneline main` |
| C1-A à C1.3 terminés | Commits `7da7ebc`, `cc6ebc5`, `fbfc5d1`, `56603d5`, `27fa6cc`, `a03794b`, `e11a725`, `01c6bb6` | `git log --oneline -8` |
| Reçu de transition C1 déposé | `livrables/C1/transition/recu_transition_C1.md` | Commit `7da7ebc` |

---

## 2. Objectif de C1.6

Ce livrable prépare le **mandat d'audit C1** destiné à l'AUDITOR. Conformément à `protocol/audit_policy.md` §3 et §17 :

- L'AUDITOR examine directement le dépôt, vérifie le mandat, les tâches, les tests et les critères
- L'AUDITOR classe les preuves et produit le rapport d'audit
- Le rapport de BUILDER est une source d'information, pas la source première de vérité (GC-22)
- L'AUDITOR ne corrige pas ce qu'il audite et ne modifie pas l'état central (GC-15)

Le BUILDER ne réalise **pas** l'audit lui-même. Il prépare uniquement les éléments nécessaires pour que l'AUDITOR puisse exécuter son contrôle.

---

## 3. Mandat d'audit C1 (à remettre à l'AUDITOR)

### 3.1 Identification du contrôle

| Champ | Valeur |
|---|---|
| Type de contrôle | `sprint_audit` (contrôle après exécution) |
| Objet du contrôle | Résultat livré par le BUILDER pour le chantier C1 |
| Date de préparation du mandat | 2026-11-24 |
| Auteur de la préparation | BUILDER DOCUMENTAIRE |
| Sprint | `sprint_C1` |
| Emplacement du rapport attendu | `audit_report/` |
| Transition concernée | `TR-2026-0002` |
| Reçu | `livrables/C1/transition/recu_transition_C1.md` |

### 3.2 Mandat et périmètre audité

| Champ | Valeur |
|---|---|
| `mandate_version` | `C1-consolide-v1` |
| Périmètre audité | Livrables C1-A, C1-B, C1-C, C1-D, C1-E, C1-F, C1.1, C1.3 (tâches C1) |
| Périmètre exclu | Documents sources du corpus AKORIS (lecture seule), `state.json` (non modifié par BUILDER), `main` (pas de fusion) |
| Checkpoint concerné | Aucun (C1 n'est pas un sprint avec checkpoint CP1-CP3) |
| Profil actif | `standard` (d'après `state.json` `governance.profile`) |

### 3.3 Tâches C1 à auditer

| # | Tâche C1 | Livrable produit | Statut | Preuve principale |
|---|---|---|---|---|
| 1 | C1-A — Hiérarchie documentaire | `livrables/C1/hierarchie_doc/hiérarchie_doc.md` | ✅ Produit | Commit `7da7ebc` |
| 2 | C1-B — Modèle d'état | `livrables/C1/etat_model/etat_model_C1.md` | ✅ Produit | Commit `cc6ebc5` |
| 3 | C1-C — Permissions, rôles | `livrables/C1/permissions/permissions_C1.md` | ✅ Produit | Commit `fbfc5d1` |
| 4 | C1-D — Registres décisions | `livrables/C1/registres/registre_decisions_C1.md` | ✅ Produit | Commit `56603d5` |
| 5 | C1-E — Versionning SemVer | `livrables/C1/versioning/versioning_C1.md` | ✅ Produit | Commit `27fa6cc` |
| 6 | C1-F — Git/GitHub atomique | `livrables/C1/git/git_github_C1.md` | ✅ Produit | Commit `a03794b` |
| 7 | C1.1 — Traitement divergences C0 | `livrables/C1/registres/traitement_divergences_C0.md` | ✅ Produit | Commit `e11a725` |
| 8 | C1.3 — MUST/SHOULD/MAY/OUT OF SCOPE | `livrables/C1/qualificatifs/qualificatifs_C1.md` | ✅ Produit | Commit `01c6bb6` |

### 3.4 Critères d'acceptation par tâche

| # | Tâche | Critère d'acceptation | Statut de contrôle attendu |
|---|---|---|---|
| 1 | C1-A | Hiérarchie documentaire établie avec 4 catégories et table de prévalence des sources | `PASS` / `PARTIAL` / `NOT_CHECKED` |
| 2 | C1-B | Modèle d'état documenté, `state.json` lu, `state.md` absent constaté, action M1 identifiée NOT_CHECKED | `PASS` / `PARTIAL` / `NOT_CHECKED` |
| 3 | C1-C | Matrice des permissions consolidée, aucune permission `technical_enforced` (toutes `unknown`), failles F1-F5 documentées | `PASS` / `PARTIAL` / `NOT_CHECKED` |
| 4 | C1-D | Registre consolidé 45 décisions (28 validées, 5 propositions, 7 recommandations, 3 non confirmées, 2 historiques) | `PASS` / `PARTIAL` / `NOT_CHECKED` |
| 5 | C1-E | 5 catégories de versions (A7), règles SemVer prospectives (A15), action M1 identifiée NOT_CHECKED | `PASS` / `PARTIAL` / `NOT_CHECKED` |
| 6 | C1-F | Règles Git/GitHub établies, protection de `main` classée `unknown`, pas de fusion vers `main` | `PASS` / `PARTIAL` / `NOT_CHECKED` |
| 7 | C1.1 | 74 divergences C0 converties en propositions documentées (20 doublons, 25 contradictions, 15 divergences terminologiques, 14 confusions) | `PASS` / `PARTIAL` / `NOT_CHECKED` |
| 8 | C1.3 | Matrice des qualificatifs pour 45 documents (32 MUST, 29 SHOULD, 24 MAY, 13 OUT OF SCOPE), 7 propositions P-QUAL | `PASS` / `PARTIAL` / `NOT_CHECKED` |

---

## 4. Fichiers et commits à examiner par l'auditeur

### 4.1 Commits C1 sur `dev_C1`

| Identifiant | Message | Tâche | Date |
|---|---|---|---|
| `7da7ebc` | docs(C1-A): hiérarchie documentaire et prévalence des sources | C1-A + reçu de transition | 2026-11-24 |
| `cc6ebc5` | docs(C1-B): modèle d'état state.json/state.md | C1-B | 2026-11-24 |
| `fbfc5d1` | docs(C1-C): permissions, roles, perimetres | C1-C | 2026-11-24 |
| `56603d5` | docs(C1-D): registre des decisions consolide C0+C1 | C1-D | 2026-11-24 |
| `27fa6cc` | docs(C1-E): versionning SemVer et distinction des categories de versions | C1-E | 2026-11-24 |
| `a03794b` | docs(C1-F): regles Git/GitHub atomique | C1-F | 2026-11-24 |
| `e11a725` | docs(C1.1): traitement divergences C0 par propositions documentees | C1.1 | 2026-11-24 |
| `01c6bb6` | docs(C1.3): distinction MUST SHOULD MAY OUT OF SCOPE | C1.3 | 2026-11-24 |

### 4.2 Fichiers sources à inspecter (lecture seule)

| Chemin | Rôle dans l'audit |
|---|---|
| `state.json` | État opérationnel — vérifier que le BUILDER ne l'a pas modifié (GC-13) |
| `reference/state.schema.json` | Schéma v2.0 — vérifier la conformité déclarée par le BUILDER |
| `protocol/decision_policy.md` | Référence pour les valeurs de décision et statuts de preuve |
| `protocol/audit_policy.md` | Référence pour la méthode d'audit |
| `protocol/governance_core.md` | Référence pour les règles GC (notamment GC-13, GC-14) |
| `protocol/permission_policy.md` | Référence pour les classifications de permission |
| `protocol/transition_policy.md` | Référence pour le mécanisme de reçu |
| `protocol/state_model.md` | Référence pour le modèle d'état |
| `reference/document_map.md` | Référence pour les sources uniques |
| `reference/terminology.md` | Référence pour le vocabulaire et les qualificatifs |
| `reference/versioning_policy.md` | Référence pour les 5 catégories de versions |

### 4.3 Fichiers livrables C1 à vérifier

| Chemin | Tâche | Vérification attendue |
|---|---|---|
| `livrables/C1/transition/recu_transition_C1.md` | Réception | Présent, conforme au template TP §5.3, tous les contrôles TP §5.4 validés |
| `livrables/C1/hierarchie_doc/hiérarchie_doc.md` | C1-A | Hiérarchie 4 catégories, table de prévalence 12 niveaux, réserve R3 partiellement levée |
| `livrables/C1/etat_model/etat_model_C1.md` | C1-B | `state.json` lu, `state.md` absent, action M1 NOT_CHECKED, adaptation proposée sans modification |
| `livrables/C1/permissions/permissions_C1.md` | C1-C | Matrice permissions, aucune `technical_enforced`, failles F1-F5, asymétries documentées |
| `livrables/C1/registres/registre_decisions_C1.md` | C1-D | 45 décisions, 5 types distingués, D-001-HVG0-B ajouté |
| `livrables/C1/versioning/versioning_C1.md` | C1-E | 5 catégories A7, règles SemVer A15, action M1 NOT_CHECKED |
| `livrables/C1/git/git_github_C1.md` | C1-F | Règles Git, pas de fusion main, protection main `unknown`, action M3 documentée |
| `livrables/C1/registres/traitement_divergences_C0.md` | C1.1 | 74 divergences en propositions, aucune correction silencieuse |
| `livrables/C1/qualificatifs/qualificatifs_C1.md` | C1.3 | Matrice 45 documents, 7 propositions P-QUAL, GC-31 respectée |

---

## 5. Méthode d'audit (séquence normative F3 §11.1)

L'AUDITOR doit suivre cette séquence :

| # | Étape | Référence | Statut attendu |
|---|---|---|---|
| 1 | Vérifier la transition | `TP` §5.4 | `PASS` |
| 2 | Lire le mandat | `C1-consolide-v1` | `PASS` |
| 3 | Lire les exigences et critères | Mandat C1 §2 | `PASS` |
| 4 | Inspecter le dépôt directement | `git log`, `git status` | `PASS` |
| 5 | Examiner les commits | 8 commits C1 sur `dev_C1` | `PASS` |
| 6 | Reproduire les tests pertinents | Tests T1-T5 (si applicables) | `NOT_CHECKED` (non exécutés par BUILDER) |
| 7 | Tester les cas limites et négatifs | Modifications hors périmètre, fusion main | `PASS` / `NOT_CHECKED` |
| 8 | Vérifier les modifications hors périmètre | Aucun document source modifié | `PASS` |
| 9 | Classer les preuves | Selon `DP` §5.1 | `PASS` |
| 10 | Produire le rapport | `audit_report/` | À produire par AUDITOR |

---

## 6. Statuts de contrôle et de preuve

Conformément à `protocol/decision_policy.md` §5 :

| Statut de contrôle | Signification |
|---|---|
| `PASS` | Contrôle réussi avec preuve directe |
| `FAIL` | Contrôle échoué |
| `PARTIAL` | Contrôle partiellement couvert |
| `N/A` | Non applicable (justification requise) |
| `NOT_CHECKED` | Contrôle non réalisé (jamais `PASS`) |

| Statut de preuve | Signification |
|---|---|
| `directly_verified` | Constaté directement par l'auditeur |
| `reproduced` | Reproduit par un tiers |
| `cross_checked` | Vérifié par un autre moyen |
| `declared_only` | Simple déclaration du BUILDER |
| `partial` | Couverture incomplète |
| `missing` | Absente |
| `invalid` | Non conforme ou non fiable |

**Règle** : Un critère critique couvert par `declared_only` est refusé (`DP` §5.1). Un test non exécuté n'est jamais `PASS` (`GC-25`).

---

## 7. Limites de l'audit C1

Ces limites doivent être déclarées dans le rapport d'audit de l'AUDITOR :

| Limite | Conséquence |
|---|---|
| Permissions classées `unknown` | Aucune garantie technique sur les permissions (`GC-36`) |
| Protection de `main` non certifiée | `unknown` — test T5 non exécuté (`C29`) |
| Tests T1-T5 non exécutés | `NON EXÉCUTÉ` — pas de preuve de refus technique |
| `state.json` non modifié par BUILDER | Vérifié par lecture seule (GC-13) |
| `state.md` absent | Vue générée non produite (INV-08) |
| Action M1 non exécutée | Validation JSON Schema `NOT_CHECKED` (pas de validateur nommé) |
| Action M3 non exécutée | Tests T1-T5 non exécutés (relève de C2) |

---

## 8. Éléments à vérifier par l'auditeur (checklist)

| # | Vérification | Méthode | Écart possible |
|---|---|---|---|
| 1 | La transition TR-2026-0002 est bien `authorized` dans `state.json` | Lire `state.json` ligne 34-51 | Divergence état/reçu |
| 2 | `current_agent` = `BUILDER` dans `state.json` | Lire `state.json` ligne 31 | INV-03 violé |
| 3 | Le reçu de transition C1 est déposé à l'emplacement attendu | Vérifier `livrables/C1/transition/recu_transition_C1.md` | INV-04 (au plus un reçu) |
| 4 | Aucun document source n'a été modifié | `git status` — pas de fichier tracké modifié | Violation de périmètre (P2) |
| 5 | `state.json` n'a pas été modifié par le BUILDER | `git status` — `state.json` untracked, non modifié | GC-13 violé |
| 6 | Les 8 commits C1 sont en Conventional Commits | `git log --oneline dev_C1 -8` | Non-conformité au format |
| 7 | Chaque commit est lié à un identifiant de tâche C1 | `git log` — messages contiennent `C1-A` à `C1.3` | Traçabilité rompue |
| 8 | Aucune fusion vers `main` n'a été effectuée | `git log main` — pas de commit de fusion | GC-14 violé |
| 9 | Les livrables C1 sont dans `livrables/C1/` uniquement | `ls livrables/C1/` | Hors périmètre C1 |
| 10 | Les divergences C0 sont signalées, pas corrigées | Comparer `livrables/C0/registres/` et `livrables/C1/registres/` | GC-31 violé |

---

## 9. Rapport attendu de l'AUDITOR

Conformément à `protocol/audit_policy.md` §17.1, le rapport d'audit doit contenir :

| # | Élément |
|---|---|
| 1 | Identification : type de contrôle, date, auteur, rôle |
| 2 | Périmètre audité |
| 3 | Limites de l'audit |
| 4 | Sources examinées |
| 5 | Méthode |
| 6 | Transition concernée : `transition_id`, reçu |
| 7 | Tâches vérifiées, une par une, avec statut |
| 8 | Tests reproduits, avec commandes et sorties |
| 9 | Écarts et anomalies qualifiées |
| 10 | Preuves, avec statut selon `DP` §5.1 |
| 11 | Éléments non vérifiés |
| 12 | Comparaison avec le rapport BUILDER |
| 13 | Désaccords conservés |
| 14 | Recommandation — **jamais une décision** |

Le rapport d'audit est déposé dans `audit_report/` (mapping C26 pour AUDITOR).

---

## 10. Prérequis pour C1.7 (rapport C1 + HVG1)

Avant de produire le rapport C1 (C1.7), le BUILDER doit :

| # | Prérequis | Statut |
|---|---|---|
| 1 | L'audit C1 a été réalisé par l'AUDITOR | En attente |
| 2 | Le rapport d'audit est déposé dans `audit_report/` | En attente |
| 3 | Les écarts et anomalies de l'audit ont été analysés | En attente |
| 4 | Le VALIDATOR a pris la décision HVG1 | En attente |

Le rapport C1 (C1.7) synthétisera les résultats de l'audit et les réserves pour la décision HVG1.

---
*Fin de C1.6. Mandat d'audit C1 préparé. L'AUDITOR est le seul acteur habilité à exécuter l'audit et produire le rapport d'audit dans `audit_report/`. Le BUILDER ne réalise pas l'audit lui-même.*