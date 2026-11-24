# C0-09 — Tableau des statuts documentaires

**Tâche** : C0-09 — Distinguer statuts documentaires  
**Date d'exécution** : 2026-11-24  
**Contrainte** : Pas de document sans statut attribué ; pas de confusion avec statut de version  
**Statuts possibles** : approuvé / proposé / obsolète / retiré / non vérifié

---

## 1. Définitions des statuts

| Statut | Définition |
|---|---|
| **Approuvé** | Document validé par le VALIDATOR, statut formellement actifié |
| **Proposé** | Document en attente de validation par le VALIDATOR (en-tête `PROPOSITION — à valider par le VALIDATOR`) |
| **Obsolète** | Document remplacé par une version plus récente, conservé comme trace historique |
| **Retiré** | Document supprimé du corpus actif (aucun dans ce'inventaire) |
| **Non vérifié** | Document dont le statut ne peut pas être établi à partir des sources accessibles (pas de bloc statut, pas de validation tracée) |

---

## 2. Tableau des statuts par document

| # | Fichier | Statut documentaire | Justification |
|---|---|---|---|
| 1 | `00_cartographie.md` | Proposé | En-tête : `STATUT | PROPOSITION — à valider par le VALIDATOR` (v0.1, 2026-11-20) |
| 2 | `changelog.md` | Non vérifié | En-tête : `STATUT | Journal de maintenance — non normatif` (v0.3) ; pas de validation VALIDATOR tracée |
| 3 | `plan_de_consolidation.md` | Non vérifié | Pas de bloc d'en-tête standard avec statut ; version 0.1.0-draft ; pas de validation VALIDATOR tracée |
| 4 | `README.md` | Non vérifié | En-tête sans bloc `Version`/`Date`/`Statut` standard ; pas de validation VALIDATOR tracée |
| 5 | `state.json` | Non vérifié | Pas de champ statut dans le fichier ; état opérationnel, pas de validation documentaire tracée |
| 6 | `_sources/AKORIS_architecture_documentaire.md` | Non vérifié | Pas de bloc `Version`/`Date`/`Statut` dans le document source ; source historique |
| 7 | `_sources/AKORIS_consolide.md` | Non vérifié | Pas de bloc `Version`/`Date`/`Statut` dans le document source ; déclare « Version consolidée : 1.0 » en en-tête mais pas de statut documentaire |
| 8 | `_sources/akoris_documentation_builder.md` | Non vérifié | Pas de bloc `Version`/`Date`/`Statut` dans le document source ; source historique |
| 9 | `implementations/opencode/README.md` | Non vérifié | En-tête : `STATUT | Descriptif — non normatif` (v0.1) ; pas de validation VALIDATOR |
| 10 | `implementations/opencode/agent_permissions.md` | Non vérifié | En-tête : `STATUT | CONSTAT — non normatif` (v0.4) ; pas de validation VALIDATOR |
| 11 | `implementations/opencode/environment_requirements.md` | Non vérifié | En-tête : `STATUT | Descriptif — prérequis observés, non certification` (v0.1) |
| 12 | `implementations/opencode/frontmatter_reference.md` | Non vérifié | En-tête : `STATUT | Référence descriptive — portée limitée` (v0.1) |
| 13 | `implementations/opencode/limitations.md` | Non vérifié | En-tête : `STATUT | Descriptif — fondé sur le constat du pilote` (v0.1) |
| 14 | `prompts/akoris_auditor_bootstrap.md` | Proposé | En-tête : `STATUT | LIVRABLE VAGUE 6 — à valider par le VALIDATOR` (v0.1) |
| 15 | `prompts/akoris_builder_bootstrap.md` | Proposé | En-tête : `STATUT | LIVRABLE VAGUE 6 — à valider par le VALIDATOR` (v0.1) |
| 16 | `prompts/akoris_documentation_builder.md` | Proposé | En-tête : `STATUT | LIVRABLE VAGUE 6 — à valider par le VALIDATOR` (v0.1) |
| 17 | `prompts/akoris_orchestrator_bootstrap.md` | Proposé | En-tête : `STATUT | LIVRABLE VAGUE 6 — à valider par le VALIDATOR` (v0.1) |
| 18 | `protocol/audit_policy.md` | Proposé | En-tête : `STATUT | PROPOSITION — à valider par le VALIDATOR` (v0.3) |
| 19 | `protocol/change_control.md` | Proposé | En-tête : `STATUT | PROPOSITION — à valider par le VALIDATOR` (v0.1) |
| 20 | `protocol/decision_policy.md` | Proposé | En-tête : `STATUT | PROPOSITION — à valider par le VALIDATOR` (v0.1) |
| 21 | `protocol/getting_started.md` | Approuvé | Statut : `VALIDÉ PAR LE VALIDATOR — 2026-11-21` (livrable V7) |
| 22 | `protocol/governance_core.md` | Proposé | En-tête : `STATUT | PROPOSITION — à valider par le VALIDATOR` (v0.1) |
| 23 | `protocol/permission_policy.md` | Proposé | En-tête : `STATUT | PROPOSITION — à valider par le VALIDATOR` (v0.3) |
| 24 | `protocol/profile_lite.md` | Non vérifié | Pas de bloc `Version`/`Date`/`Statut` lu dans ce fichier ; vague 2 |
| 25 | `protocol/profile_reinforced.md` | Non vérifié | Pas de bloc `Version`/`Date`/`Statut` lu dans ce fichier ; vague 2 |
| 26 | `protocol/profile_standard.md` | Non vérifié | Pas de bloc `Version`/`Date`/`Statut` lu dans ce fichier ; vague 2 |
| 27 | `protocol/recovery_policy.md` | Proposé | En-tête : `STATUT | PROPOSITION — à valider par le VALIDATOR` (v0.2) |
| 28 | `protocol/state_model.md` | Proposé | En-tête : `STATUT | PROPOSITION — à valider par le VALIDATOR` (v0.2) |
| 29 | `protocol/transition_policy.md` | Proposé | En-tête : `STATUT | PROPOSITION — à valider par le VALIDATOR` (v0.2) |
| 30 | `reference/document_map.md` | Proposé | En-tête : `STATUT | PROPOSITION — à valider par le VALIDATOR` (v0.4) |
| 31 | `reference/state.schema.json` | Non vérifié | Pas de champ statut (fichier JSON) ; Schéma AKORIS v2.0 (décision C28) mais pas de validation documentaire tracée |
| 32 | `reference/terminology.md` | Proposé | En-tête : `STATUT | PROPOSITION — à valider par le VALIDATOR` (v0.3) |
| 33 | `reference/traceability_map.md` | Approuvé | Statut : `VALIDÉ PAR LE VALIDATOR — 2026-11-21` (livrable V7, v0.1) |
| 34 | `reference/versioning_policy.md` | Approuvé | Statut : `VALIDÉ PAR LE VALIDATOR — 2026-11-21` (livrable V7, v0.1) |
| 35 | `templates/auditor_report_template.md` | Proposé | En-tête : `STATUT | LIVRABLE VAGUE 6 — à valider par le VALIDATOR` (v0.1) |
| 36 | `templates/builder_report_template.md` | Proposé | En-tête : `STATUT | LIVRABLE VAGUE 6 — à valider par le VALIDATOR` (v0.1) |
| 37 | `templates/change_request_template.md` | Proposé | En-tête : `STATUT | LIVRABLE VAGUE 6 — à valider par le VALIDATOR` (v0.1) |
| 38 | `templates/decision_template.md` | Proposé | En-tête : `STATUT | LIVRABLE VAGUE 6 — à valider par le VALIDATOR` (v0.1) |
| 39 | `templates/orchestrator_report_template.md` | Proposé | En-tête : `STATUT | LIVRABLE VAGUE 6 — à valider par le VALIDATOR` (v0.1) |
| 40 | `templates/reserve_template.md` | Proposé | En-tête : `STATUT | LIVRABLE VAGUE 6 — à valider par le VALIDATOR` (v0.1) |
| 41 | `templates/transition_receipt_template.md` | Proposé | En-tête : `STATUT | LIVRABLE VAGUE 6 — à valider par le VALIDATOR` (v0.1) |
| 42 | `livrables/C0/mandat_builder.md` | Non vérifié | Mandat C0, autorisation GO_WITH_RESERVES HVG0 ; pas de statut documentaire en-tête standard |
| 43 | `livrables/C0/transition/notification_builder.md` | Non vérifié | Notification de transition C0 ; pas de statut documentaire en-tête standard |
| 44 | `livrables/C0/transition/reception_transition.md` | Non vérifié | Réception de transition C0 ; pas de statut documentaire en-tête standard |
| 45 | `livrables/C0/transition/recu_transition_C0.md` | Non vérifié | Reçu de transition C0 (déjà déposé) ; pas de statut documentaire en-tête standard |

---

## 3. Répartition des statuts

| Statut | Nombre de documents | Pourcentage |
|---|---|---|
| Approuvé | 3 (`getting_started.md`, `traceability_map.md`, `versioning_policy.md`) | 6,7 % |
| Proposé | 24 | 53,3 % |
| Obsolète | 0 | 0 % |
| Retiré | 0 | 0 % |
| Non vérifié | 18 | 40,0 % |
| **Total** | **45** | **100 %** |

---

## 4. Notes sur les statuts

- Aucun document n'est marqué `obsolète` ou `retiré` dans le corpus actuel.
- Les 3 documents approuvés sont tous des livrables V7 validés par le VALIDATOR le 2026-11-21 (conformément à `README.md` §10 et aux en-têtes des fichiers concernés).
- Les 24 documents proposés portent tous la mention `PROPOSITION — à valider par le VALIDATOR` ou `LIVRABLE VAGUE 6 — à valider par le VALIDATOR` dans leur en-tête.
- Les 18 documents non vérifiés n'ont pas de bloc de statut standard ou n'ont pas de validation VALIDATOR tracée accessible. Cela inclut les 3 sources historiques (_sources/), les fichiers d'implémentation (constats non normatifs), les fichiers de profil (pas de bloc statut lu), `state.json`, `state.schema.json`, `changelog.md`, `plan_de_consolidation.md`, `README.md`, et les 4 fichiers de transition C0.
- Ce statut documentaire est distinct du statut de version (champ `Version` dans les en-têtes).

---
*Fin du tableau des statuts. Pas de document sans statut attribué. Pas de confusion avec le statut de version. Total : 45 documents classés.*