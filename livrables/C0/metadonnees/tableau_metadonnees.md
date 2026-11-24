# C0-03 — Tableau des métadonnées par document

**Tâche** : C0-03 — Relever métadonnées de chaque document  
**Date d'exécution** : 2026-11-24  
**Contrainte** : Pas de modification source ; valeurs manquantes signalées non remplies  
**Valeurs autorisées pour métadonnées manquantes** : `inconnu`, `non indiqué`, `non vérifiable`, `sans objet`

---

## 1. Méthode

Pour chacun des 45 documents inventoriés (voir C0-02), les métadonnées suivantes sont relevées : rôle, statut documentaire, version, date, relations. Lorsqu'une information est absente du document, elle est portée par l'une des valeurs autorisées ci-dessus, sans invention.

---

## 2. Tableau des métadonnées

| # | Fichier | Rôle | Statut documentaire | Version | Date | Relations (liens, dépendances, sources) |
|---|---|---|---|---|---|---|
| 1 | `00_cartographie.md` | Cartographie de l'existant, diagnostic, doubles, contradictions | Proposé (en attente de validation VALIDATOR) | 0.1 | 2026-11-20 | Sources F1/F2/F3 ; dépend de `document_map.md` §3, §4.4–4.5 ; renvoie vers `permission_policy.md`, `decision_policy.md`, `versioning_policy.md`, `traceability_map.md` |
| 2 | `changelog.md` | Journal du cadre documentaire | Non vérifié (journal de maintenance, non normatif) | 0.3 | 2026-11-21 | Centralise historiques de `README.md`, `document_map.md`, `terminology.md`, `agent_permissions.md` ; maintient M1, M2, V7 |
| 3 | `plan_de_consolidation.md` | Plan de consolidation C0–C5, registre de suivi, journal des décisions | inconnu (brouillon v0.1.0-draft, pas de statut d'en-tête validé) | 0.1.0-draft | 2026-11-24 | Mandat C0-revise-v1 ; référence commit `f3b2eb7` ; décisions D-001 ; points HVG0–HVG5 |
| 4 | `README.md` | Point d'entrée documentation, parcours de lecture, état d'avancement | inconnu (en-tête sans bloc statut standard) | inconnu | inconnu | Dépend de `terminology`, `document_map` ; §5 rôles ; §8 règles de maintenance ; §9 sources de référence ; §11 points ouverts A1–A8, C13, C26–C29 |
| 5 | `state.json` | État opérationnel machine (source de vérité) | non indiqué (pas de champ statut dans le schéma) | schema_version "2.0" | 2026-11-24 | Dépend de `reference/state.schema.json` ; relation avec `current_sprint.md`, reçus de transition ; GC-12, GC-13 |
| 6 | `_sources/AKORIS_architecture_documentaire.md` | Plan d'architecture et d'organisation du cadre | inconnu (pas de bloc statut dans le document source) | inconnu | inconnu | Source F2, niveau 3 ; cité par `governance_core.md`, `document_map.md` §5, `decision_policy.md`, `state_model.md` |
| 7 | `_sources/AKORIS_consolide.md` | Référence doctrinale du cadre (v1.0) | inconnu (pas de bloc statut dans le document source) | Version consolidée 1.0 | inconnu | Source F3, niveau 2 ; cité par `governance_core.md`, `document_map.md` §5, `decision_policy.md`, `state_model.md`, `transition_policy.md` |
| 8 | `_sources/akoris_documentation_builder.md` | Mandat et méthode du rédacteur documentaire | inconnu (pas de bloc statut dans le document source) | inconnu | inconnu | Source F1, niveau 4 ; cité par `governance_core.md`, `document_map.md` §5 |
| 9 | `implementations/opencode/README.md` | Présentation de l'implémentation OpenCode | Descriptif — non normatif | 0.1 | 2026-11-21 | Dépend de `permission_policy.md`, `agent_permissions.md` ; renvoie vers `document_map.md`, `governance_core.md`, `audit_policy.md`, `state_model.md` |
| 10 | `implementations/opencode/agent_permissions.md` | Constat des permissions observées (pilote demo_web) | Constat — non normatif | 0.4 | 2026-11-20 | Dépend de `permission_policy.md`, `governance_core.md` ; tests T1–T5 non exécutés ; références T4 harmonisation VALIDATOR 2026-11-20 |
| 11 | `implementations/opencode/environment_requirements.md` | Prérequis d'environnement observés | Descriptif — prérequis observés, non certification | 0.1 | 2026-11-21 | Dépend de `agent_permissions.md`, `permission_policy.md` §7 |
| 12 | `implementations/opencode/frontmatter_reference.md` | Référence de frontmatter OpenCode observé | Référence descriptive — portée limitée | 0.1 | 2026-11-21 | Dépend de `agent_permissions.md`, `permission_policy.md` §2.1 |
| 13 | `implementations/opencode/limitations.md` | Limites de l'implémentation observée | Descriptif — fondé sur le constat du pilote | 0.1 | 2026-11-21 | Dépend de `agent_permissions.md`, `permission_policy.md` §2.1, §7 |
| 14 | `prompts/akoris_auditor_bootstrap.md` | Prompt d'amorçage AUDITOR | Livrable vague 6 — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `terminology.md` §2, `audit_policy.md` §3 |
| 15 | `prompts/akoris_builder_bootstrap.md` | Prompt d'amorçage BUILDER | Livrable vague 6 — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `terminology.md` §2, `governance_core.md` GC-13, GC-14, `transition_policy.md`, `state_model.md` |
| 16 | `prompts/akoris_documentation_builder.md` | Prompt d'amorçage DOCUMENTATION BUILDER | Livrable vague 6 — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `terminology.md` §2, `README.md` §5, `document_map.md` |
| 17 | `prompts/akoris_orchestrator_bootstrap.md` | Prompt d'amorçage ORCHESTRATOR | Livrable vague 6 — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `terminology.md` §2, `governance_core.md` GC-04 à GC-09 |
| 18 | `protocol/audit_policy.md` | Politique d'audit (readiness_review, sprint_audit) | Proposition — à valider par le VALIDATOR | 0.3 | 2026-11-21 | Dépend de `decision_policy.md`, `permission_policy.md`, `state_model.md`, `transition_policy.md` ; décisions C13, C19, C22, C26–C31 |
| 19 | `protocol/change_control.md` | Contrôle des changements, classification, impact | Proposition — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `decision_policy.md`, `state_model.md` ; décisions A1, A3, A7 |
| 20 | `protocol/decision_policy.md` | Valeurs de décision, gravités, preuves, réserves | Proposition — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `governance_core.md`, `state_model.md` ; décisions A1, A2 |
| 21 | `protocol/getting_started.md` | Manuel complet et pédagogique d'AKORIS | Validé par le VALIDATOR — 2026-11-21 (livrable V7) | inconnu (pas de bloc version visible) | 2026-11-21 | Dépend de tout le socle ; vague 7 |
| 22 | `protocol/governance_core.md` | Socle de gouvernance, 54 règles communes (GC-01 à GC-54) | Proposition — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `terminology.md` ; cité par tous les documents du protocole |
| 23 | `protocol/permission_policy.md` | Trois niveaux de permission, matrice, vérification effective | Proposition — à valider par le VALIDATOR | 0.3 | 2026-11-20 | Dépend de `state_model.md` ; décisions A8, harmonisation T4 VALIDATOR 2026-11-20 |
| 24 | `protocol/profile_lite.md` | Profil de gouvernance Lite (faible risque) | inconnu (pas de bloc statut lu dans ce fichier) | inconnu | inconnu | Dépend de `governance_core.md`, `profile_standard.md` ; vague 2 |
| 25 | `protocol/profile_reinforced.md` | Profil de gouvernance Reinforced (risque élevé) | inconnu (pas de bloc statut lu dans ce fichier) | inconnu | inconnu | Dépend de `governance_core.md`, `profile_standard.md` ; vague 2 |
| 26 | `protocol/profile_standard.md` | Profil de gouvernance Standard (profil par défaut) | inconnu (pas de bloc statut lu dans ce fichier) | inconnu | inconnu | Dépend de `governance_core.md` ; vague 2 |
| 27 | `protocol/recovery_policy.md` | Politique de reprise, blocage, incident, rollback | Proposition — à valider par le VALIDATOR | 0.2 | 2026-11-20 | Dépend de `state_model.md`, `transition_policy.md`, `decision_policy.md` ; décision C34 |
| 28 | `protocol/state_model.md` | Modèle d'état, états projet/sprint/transition, invariants | Proposition — à valider par le VALIDATOR | 0.2 | 2026-11-20 | Dépend de `governance_core.md` ; décisions A2, A7, C22, C28 ; schémas `reference/state.schema.json` |
| 29 | `protocol/transition_policy.md` | Transitions, autorisations, reçus, consommation, expiration | Proposition — à valider par le VALIDATOR | 0.2 | 2026-11-20 | Dépend de `state_model.md` ; décisions A2, C22, C24, C26, C27 |
| 30 | `reference/document_map.md` | Carte documentaire, index du corpus, dépendances | Proposition — à valider par le VALIDATOR | 0.4 | 2026-11-20 | Dépend de `terminology.md` ; §5 sources externes ; §8 sources uniques ; §9 dépendances |
| 31 | `reference/state.schema.json` | Schéma technique de `state.json` pour AKORIS v2.0 | Technique — Schéma AKORIS v2.0 (décision C28) | 2.0 | 2026-11-20 | Dépend de `state_model.md` ; décision A2 ; `additionalProperties: false` |
| 32 | `reference/terminology.md` | Vocabulaire unique du cadre AKORIS | Proposition — à valider par le VALIDATOR | 0.3 | 2026-11-20 | Dépend de F1, F2, F3, GS1 ; §11 arbitrages A1, A2, A4, A5, A7 |
| 33 | `reference/traceability_map.md` | Carte de traçabilité (exigence → tâche → test → preuve → décision) | Validé par le VALIDATOR — 2026-11-21 (livrable V7) | 0.1 | 2026-11-21 | Dépend de tout le protocole ; vague 7 |
| 34 | `reference/versioning_policy.md` | Politique de versionnement (5 catégories A7) | Validé par le VALIDATOR — 2026-11-21 (livrable V7) | 0.1 | 2026-11-21 | Dépend de `state_model.md`, `terminology.md`, `document_map.md`, `governance_core.md`, `change_control.md`, `transition_policy.md` ; décisions A2, A7, C25, C27, C28 |
| 35 | `templates/auditor_report_template.md` | Modèle de rapport d'audit AUDITOR | Livrable vague 6 — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `audit_policy.md` §17, `decision_policy.md` §5 |
| 36 | `templates/builder_report_template.md` | Modèle de rapport de sprint BUILDER | Livrable vague 6 — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `document_map.md` §4.5, `audit_policy.md` §17, `transition_policy.md` |
| 37 | `templates/change_request_template.md` | Modèle de demande de changement | Livrable vague 6 — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `change_control.md` §3, §5, §10, `terminology.md` §5 |
| 38 | `templates/decision_template.md` | Modèle de décision du VALIDATOR | Livrable vague 6 — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `decision_policy.md` §3, §11, `terminology.md` §4 |
| 39 | `templates/orchestrator_report_template.md` | Modèle de rapport ORCHESTRATOR | Livrable vague 6 — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `document_map.md` §4.5, `governance_core.md`, `decision_policy.md` |
| 40 | `templates/reserve_template.md` | Modèle de réserve | Livrable vague 6 — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `decision_policy.md` §7.2, `terminology.md` §4 |
| 41 | `templates/transition_receipt_template.md` | Modèle de reçu de transition | Livrable vague 6 — à valider par le VALIDATOR | 0.1 | 2026-11-20 | Dépend de `transition_policy.md` §5.3, §5.7 (décision C26) |
| 42 | `livrables/C0/mandat_builder.md` | Mandat opérationnel BUILDER DOCUMENTAIRE C0 | Autorisé (décision VALIDATOR GO_WITH_RESERVES HVG0) | C0-revise-v1 | 2026-11-24 | Dépend de `plan_de_consolidation.md` ; 5 réserves R1–R5 |
| 43 | `livrables/C0/transition/notification_builder.md` | Notification de transition vers BUILDER DOCUMENTAIRE | inconnu (livrable de transition C0) | inconnu | 2026-11-24 | Dépend de TR-2026-0001, mandat C0-revise-v1 |
| 44 | `livrables/C0/transition/reception_transition.md` | Réception de transition C0 | inconnu (livrable de transition C0) | inconnu | 2026-11-24 | Dépend de TR-2026-0001, décision D-001-HVG0 |
| 45 | `livrables/C0/transition/recu_transition_C0.md` | Reçu de transition C0 (déjà déposé) | inconnu (livrable de transition C0) | inconnu | 2026-11-24T10:40:00Z | Dépend de TR-2026-0001, état `consumed`, `receipt_reference` RC-2026-0001-GOWR |

---

## 3. Répartition des métadonnées manquantes

| Champ | Nombre de documents avec valeur manquante | Valeur utilisée |
|---|---|---|
| Version manquante | 8 (fichiers 1, 4, 6, 7, 8, 21, 24, 25, 26, 42–45) | `inconnu` ou `non indiqué` |
| Date manquante | 8 (fichiers 4, 6, 7, 8, 24, 25, 26, 42–45) | `inconnu` ou `non indiqué` |
| Statut documentaire manquant | 6 (fichiers 3, 6, 7, 8, 24, 25, 26, 42–45) | `inconnu` ou `non vérifiable` |

> **Principe** : aucune valeur manquante n'est inventée. Les documents sans en-tête de version/date/statut portent la valeur `inconnu` ou `non indiqué`, selon le cas.

---
*Fin de C0-03. Tableau figé à la date d'exécution : 2026-11-24.*