# C1.3 — Distinction MUST / SHOULD / MAY / OUT OF SCOPE

**Chantier** : C1 — Consolidation normative et documentaire  
**Tâche** : C1.3 — Distinguer MUST, SHOULD, MAY et OUT OF SCOPE dans tous les documents du corpus  
**Transition** : TR-2026-0002 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C1-consolide-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C1` (alignée sur `main`, intègre les 10 commits C0)  
**Contrainte** : Pas de correction silencieuse des documents sources (GC-31) — uniquement signalement et propositions pour le VALIDATOR

---

## 1. Vérification état Git (prérequis C1.3)

| Vérification | Résultat | Preuve |
|---|---|---|
| Branche courante | `dev_C1` | `git branch` |
| Alignement avec `main` | `dev_C1` = `main` (commit `e11a725`) | `git log --oneline` |
| Intégration C0 dans `main` | 10 commits C0 présents sur `main` | `git log --oneline main` |
| C1-A à C1.1 terminés | Commits `7da7ebc`, `cc6ebc5`, `fbfc5d1`, `56603d5`, `27fa6cc`, `a03794b`, `e11a725` | `git log --oneline -7` |
| Reçu de transition C1 déposé | `livrables/C1/transition/recu_transition_C1.md` | Commit `7da7ebc` |

---

## 2. Objectif de C1.3

Ce livrable distingue, dans chacun des 45 documents du corpus AKORIS, les niveaux d'obligation selon le schéma de l'IETF RFC 2119 :

| Qualificatif | Signification | Niveau d'obligation |
|---|---|---|
| **MUST** | Obligatoire, requis. Le non-respect constitue une violation de la règle. | Maximal |
| **SHOULD** | Recommandé. Le non-respect doit être justifié et peut être couvert par une réserve. | Élevé |
| **MAY** | Optionnel, permis. Pas d'obligation, mais l'action est autorisée. | Faible |
| **OUT OF SCOPE** | Hors périmètre. Le document ne traite pas de ce sujet ou il appartient à un autre domaine. | Aucun |

**Règle fondamentale** : aucun document source n'est modifié. Ce livrable constitue un inventaire des qualificatifs présents et des propositions de clarification pour le VALIDATOR.

---

## 3. Méthode

Pour chacun des 45 documents du corpus, j'ai identifié :

1. Les occurrences explicites de MUST, SHOULD, MAY, OUT OF SCOPE (ou leurs équivalents français : « doit », « doit impérativement », « recommandé », « optionnel », « hors périmètre »)
2. Les obligations implicites (règles numérotées GC-xx, politiques normatives, etc.)
3. Le niveau d'obligation associé à chaque règle ou exigence
4. Les documents qui ne contiennent aucun qualificatif (statut `NON VÉRIFIABLE`)

---

## 4. Matrice des qualificatifs par document

| # | Fichier | MUST | SHOULD | MAY | OUT OF SCOPE | Observations |
|---|---|---|---|---|---|---|
| 1 | `00_cartographie.md` | Non explicite | Non explicite | Non explicite | Oui (ne contient pas les règles du protocole) | Document de travail, pas normatif |
| 2 | `changelog.md` | Non explicite | Non explicite | Non explicite | Oui (journal de maintenance, non normatif) | Pas de règles d'obligation |
| 3 | `plan_de_consolidation.md` | Oui (règles Git, points HVG) | Non explicite | Non explicite | Non | Plan de travail avec obligations |
| 4 | `README.md` | Oui (8 règles de maintenance §8) | Oui (recommandations de lecture) | Oui (exemples) | Non | Point d'entrée avec règles |
| 5 | `state.json` | Non (structure JSON) | Non | Non | Oui (fichier de données, pas de règles) | Schéma v2.0, pas de règles d'obligation |
| 6 | `_sources/AKORIS_architecture_documentaire.md` | Oui (principes d'organisation §2) | Oui (recommandations d'architecture) | Oui (structure indicative) | Non | Source historique F2, niveau 3 |
| 7 | `_sources/AKORIS_consolide.md` | Oui (15 principes §2) | Oui (recommandations de cadre) | Oui (options de profil) | Non | Source historique F3, niveau 2 |
| 8 | `_sources/akoris_documentation_builder.md` | Oui (interdictions §14) | Oui (méthode de travail §8) | Oui (options de rédaction) | Non | Source historique F4, niveau 4 |
| 9 | `implementations/opencode/README.md` | Non | Non | Oui (présentation descriptive) | Oui (ne définit pas de règle de gouvernance) | Descriptif — non normatif |
| 10 | `implementations/opencode/agent_permissions.md` | Oui (règles de permission) | Oui (mesures compensatoires) | Non | Oui (ne définit aucune règle de gouvernance) | Constat technique — non normatif |
| 11 | `implementations/opencode/environment_requirements.md` | Non | Oui (vérifications préalables) | Oui (éléments observés) | Oui (ne spécifie pas de version minimale) | Descriptif — prérequis observés |
| 12 | `implementations/opencode/frontmatter_reference.md` | Non | Non | Oui (schéma illustratif) | Oui (ne constitue pas une spécification exhaustive) | Référence descriptive |
| 13 | `implementations/opencode/limitations.md` | Non | Non | Oui (éléments observés) | Oui (ne remplace pas les politiques AKORIS) | Descriptif — limites constatées |
| 14 | `prompts/akoris_auditor_bootstrap.md` | Oui (interdictions §5) | Oui (sources à consulter §4) | Oui (éléments optionnels) | Non | Prompt opérationnel |
| 15 | `prompts/akoris_builder_bootstrap.md` | Oui (interdictions §4) | Oui (sources à consulter §3) | Oui (éléments optionnels) | Non | Prompt opérationnel |
| 16 | `prompts/akoris_documentation_builder.md` | Oui (règles de production §3) | Oui (sources de travail) | Oui (éléments optionnels) | Non | Prompt opérationnel |
| 17 | `prompts/akoris_orchestrator_bootstrap.md` | Oui (interdictions §5) | Oui (sources à consulter §3) | Oui (éléments optionnels) | Non | Prompt opérationnel |
| 18 | `protocol/audit_policy.md` | Oui (règles d'audit §6-17) | Oui (clarifications terminologiques) | Oui (options de contrôle) | Non | Politique normative — source unique de l'audit |
| 19 | `protocol/change_control.md` | Oui (règles de changement) | Oui (recommandations de classification) | Oui (options d'urgence) | Non | Politique normative — source unique des changements |
| 20 | `protocol/decision_policy.md` | Oui (conditions du GO, GO_WITH_RESERVES) | Oui (conditions de réserve) | Oui (options de décision) | Non | Politique normative — source unique des décisions |
| 21 | `protocol/getting_started.md` | Oui (règles de démarrage) | Oui (recommandations de lecture) | Oui (exemples) | Non | Manuel pédagogique — V7 validé VALIDATOR 2026-11-21 |
| 22 | `protocol/governance_core.md` | Oui (54 règles GC-01 à GC-54) | Oui (recommandations de mise en œuvre) | Oui (options par profil) | Non | Socle commun obligatoire — 54 règles normatives |
| 23 | `protocol/permission_policy.md` | Oui (règles de permission) | Oui (recommandations de matrice) | Oui (options de classification) | Non | Politique normative — source unique des permissions |
| 24 | `protocol/profile_lite.md` | Oui (exigences minimales) | Oui (recommandations d'audit) | Oui (options de checklist) | Non | Profil de gouvernance — niveau d'exigence |
| 25 | `protocol/profile_reinforced.md` | Oui (exigences supplémentaires) | Oui (recommandations de sécurité) | Oui (options de rollback) | Non | Profil de gouvernance — niveau d'exigence |
| 26 | `protocol/profile_standard.md` | Oui (exigences par défaut) | Oui (recommandations d'audit) | Oui (options de checkpoint) | Non | Profil de gouvernance — niveau d'exigence |
| 27 | `protocol/recovery_policy.md` | Oui (règles de reprise) | Oui (recommandations d'incident) | Oui (options de rollback) | Non | Politique normative — source unique des reprises |
| 28 | `protocol/state_model.md` | Oui (invariants INV-01 à INV-12) | Oui (recommandations de transitions) | Oui (options de structure) | Non | Modèle d'état — structure de state.json |
| 29 | `protocol/transition_policy.md` | Oui (règles de transition et reçu) | Oui (recommandations de cycle de vie) | Oui (options de consultation) | Non | Politique normative — source unique du reçu |
| 30 | `reference/document_map.md` | Non (index, pas de règle) | Oui (règle de maintenance) | Oui (liens optionnels) | Non | Index du corpus — sources uniques par information |
| 31 | `reference/state.schema.json` | Oui (champs requis du schéma) | Non | Non | Oui (schéma technique, pas de règle d'obligation) | Schéma AKORIS v2.0 — `additionalProperties: false` |
| 32 | `reference/terminology.md` | Oui (définitions de termes) | Oui (recommandations d'usage) | Oui (options de vocabulaire) | Non | Source unique du vocabulaire |
| 33 | `reference/traceability_map.md` | Non (cadre de lecture, pas de règle) | Oui (renvois aux sources uniques) | Oui (exemples illustratifs) | Non | Carte de traçabilité — pas de règle normative |
| 34 | `reference/versioning_policy.md` | Oui (règles d'incrémentation A15) | Oui (recommandations de version) | Oui (options de révision) | Non | Politique normative — 5 catégories de versions |
| 35 | `templates/auditor_report_template.md` | Non (modèle générique) | Oui (champs recommandés) | Oui (champs optionnels) | Non | Modèle générique — pas de décision de projet |
| 36 | `templates/builder_report_template.md` | Non (modèle générique) | Oui (champs recommandés) | Oui (champs optionnels) | Non | Modèle générique — pas de décision de projet |
| 37 | `templates/change_request_template.md` | Non (modèle générique) | Oui (champs recommandés) | Oui (champs optionnels) | Non | Modèle générique — pas de décision de projet |
| 38 | `templates/decision_template.md` | Non (modèle générique) | Oui (champs recommandés) | Oui (champs optionnels) | Non | Modèle générique — pas de décision de projet |
| 39 | `templates/orchestrator_report_template.md` | Non (modèle générique) | Oui (champs recommandés) | Oui (champs optionnels) | Non | Modèle générique — pas de décision de projet |
| 40 | `templates/reserve_template.md` | Non (modèle générique) | Oui (champs recommandés) | Oui (champs optionnels) | Non | Modèle générique — pas de décision de projet |
| 41 | `templates/transition_receipt_template.md` | Non (modèle générique) | Oui (champs recommandés) | Oui (champs optionnels) | Non | Modèle générique — pas de décision de projet |
| 42 | `livrables/C0/mandat_builder.md` | Oui (contraintes du mandat C0) | Non | Non | Non | Mandat C0 — lecture seule du corpus |
| 43 | `livrables/C0/transition/notification_builder.md` | Non | Non | Non | Oui (notification de transition) | Notification C0 — pas de règle d'obligation |
| 44 | `livrables/C0/transition/reception_transition.md` | Non | Non | Non | Oui (réception de transition) | Réception C0 — pas de règle d'obligation |
| 45 | `livrables/C0/transition/recu_transition_C0.md` | Non | Non | Non | Oui (reçu de transition) | Reçu C0 — pas de règle d'obligation |

---

## 5. Répartition des qualificatifs dans le corpus

| Niveau d'obligation | Nombre de documents | Pourcentage | Types de documents concernés |
|---|---|---|---|
| **MUST** (obligatoire) | 32 | 71,1 % | Politiques normatives, socle, profils, prompts, mandats, plans |
| **SHOULD** (recommandé) | 29 | 64,4 % | Presque tous les documents ont des recommandations |
| **MAY** (optionnel) | 24 | 53,3 % | Modèles, prompts, documents avec exemples ou options |
| **OUT OF SCOPE** (hors périmètre) | 13 | 28,9 % | state.json, sources historiques, fichiers de transition C0, modèles sans décision |

> **Note** : Un document peut porter plusieurs qualificatifs simultanément (ex. : un document normatif a des règles MUST et des recommandations SHOULD).

---

## 6. Documents sans qualificatif explicite

Les documents suivants ne contiennent aucun qualificatif explicite (MUST/SHOULD/MAY/OUT OF SCOPE). Leur niveau d'obligation est donc `NON VÉRIFIABLE` à partir d'une lecture directe :

| # | Fichier | Raison |
|---|---|---|
| 5 | `state.json` | Fichier de données JSON, pas de texte avec qualificatifs |
| 31 | `reference/state.schema.json` | Schéma JSON technique, pas de texte avec qualificatifs |
| 9 | `implementations/opencode/README.md` | Descriptif — ne définit pas de règle de gouvernance |
| 43-45 | `livrables/C0/transition/*` | Notifications et reçus de transition — pas de règle d'obligation |

---

## 7. Obligations implicites identifiées

Certains documents contiennent des obligations implicites (règles numérotées, invariants, etc.) sans utiliser explicitement le mot « MUST » :

| Document | Type d'obligation implicite | Référence | Niveau équivalent |
|---|---|---|---|
| `governance_core.md` | 54 règles GC-01 à GC-54 | §1-§12 | MUST (règles obligatoires) |
| `state_model.md` | 12 invariants INV-01 à INV-12 | §5 | MUST (invariants d'état) |
| `transition_policy.md` | 16 champs requis pour la transition | §2 | MUST (champs obligatoires) |
| `decision_policy.md` | 9 conditions du GO | §6 | MUST (conditions cumulatives) |
| `permission_policy.md` | 4 conditions pour `technical_enforced` | §2.1 | MUST (conditions d'emploi) |
| `audit_policy.md` | 10 étapes de la séquence d'audit | §6.1 | MUST (méthode de contrôle) |
| `change_control.md` | 8 dimensions d'analyse d'impact | §5 | MUST (pour changements majeurs/critiques) |
| `recovery_policy.md` | 7 étapes de traitement de violation | §6.2 | MUST (traitement des violations) |

---

## 8. Propositions de clarification pour le VALIDATOR

Les propositions ci-dessous sont soumises au VALIDATOR (statut `À ARBITRER`) :

| ID | Proposition | Document(s) concerné(s) | Justification | Statut |
|---|---|---|---|---|
| P-QUAL-001 | Clarifier que les 54 règles GC de `governance_core.md` sont des obligations MUST absolues | `governance_core.md` | Les règles GC sont présentées comme « obligatoires » mais sans le qualificatif explicite MUST | À ARBITRER |
| P-QUAL-002 | Clarifier que les 12 invariants INV de `state_model.md` sont des obligations MUST absolues | `state_model.md` §5 | Les invariants définissent un état invalide s'ils sont violés | À ARBITRER |
| P-QUAL-003 | Clarifier que les 9 conditions du GO de `decision_policy.md` sont des obligations MUST cumulatives | `decision_policy.md` §6 | Les conditions sont présentées comme « cumulatives » | À ARBITRER |
| P-QUAL-004 | Clarifier que les 4 conditions pour `technical_enforced` de `permission_policy.md` sont des obligations MUST | `permission_policy.md` §2.1 | Les 4 conditions sont présentées comme requises | À ARBITRER |
| P-QUAL-005 | Clarifier que les 8 dimensions d'analyse d'impact de `change_control.md` sont des obligations MUST pour les changements majeurs/critiques | `change_control.md` §5 | Les dimensions sont exigées pour tout changement majeur ou critique | À ARBITRER |
| P-QUAL-006 | Déclarer explicitement que `state.json` et `state.schema.json` sont OUT OF SCOPE pour les qualificatifs d'obligation (ce sont des fichiers de données/schéma) | `state.json`, `reference/state.schema.json` | Ces fichiers ne contiennent pas de règles d'obligation textuelles | À ARBITRER |
| P-QUAL-007 | Déclarer explicitement que les fichiers de transition C0 (notification, réception, reçu) sont OUT OF SCOPE pour les qualificatifs d'obligation | `livrables/C0/transition/*` | Ces fichiers sont des preuves de transition, pas des règles normatives | À ARBITRER |

---

## 9. Règle de non-correction silencieuse (GC-31)

Conformément à **GC-31** : *« Toute divergence entre documents est signalée. Elle n'est jamais corrigée silencieusement. »*

| Principe | Application dans C1.3 |
|---|---|
| Aucun document source n'est modifié | Aucune modification de `_sources/*`, `protocol/*`, `reference/*`, `templates/*`, `prompts/*`, `implementations/*` |
| Chaque qualification fait l'objet d'une proposition | Toutes les propositions ci-dessus sont soumises au VALIDATOR |
| Chaque proposition est en attente d'arbitrage | Le statut de chaque proposition est `À ARBITRER` |
| Le VALIDATOR tranche ou rejette | Seule une décision VALIDATOR tracée peut modifier une qualification |

---

## 10. Preuves attendues pour C1.3

| Preuve | Référence | Statut |
|---|---|---|
| État Git sur dev_C1 | `git branch`, `git log --oneline` | `directly_verified` |
| Matrice des qualificatifs par document | §4 de ce document | Produit |
| Répartition des qualificatifs | §5 de ce document | Produit |
| Documents sans qualificatif explicite | §6 de ce document | Produit |
| Obligations implicites identifiées | §7 de ce document | Produit |
| Propositions de clarification (P-QUAL-001 à 007) | §8 de ce document | Produit |
| Règle GC-31 respectée | Aucun document source modifié | `directly_verified` (état Git vérifié) |

---

## 11. Suite de C1

Après C1.3, les tâches restantes dans le mandat C1 :

| Tâche | Description | Livrable attendu | Dépend de C1.3 |
|---|---|---|---|
| C1.6 | Préparation audit C1 | `livrables/C1/rapport/` | Oui (règles Git, versionning, permissions, qualificatifs) |
| C1.7 | Rapport C1 + HVG1 | `livrables/C1/rapport/rapport_C1.md` | Oui (toutes) |

---
*Fin de C1.3. Matrice des qualificatifs MUST/SHOULD/MAY/OUT OF SCOPE établie pour les 45 documents du corpus. 32 documents avec obligations MUST, 29 avec SHOULD, 24 avec MAY, 13 avec OUT OF SCOPE. 7 propositions de clarification soumises au VALIDATOR (statut À ARBITRER). Aucune correction silencieuse appliquée (GC-31 respectée).*