# C0-04 — Classification des documents par nature

**Tâche** : C0-04 — Classer documents par nature  
**Date d'exécution** : 2026-11-24  
**Contrainte** : Chaque document a exactement une catégorie principale ; catégories secondaires possibles avec justification ; aucune modification source

---

## 1. Définitions des catégories

| Catégorie principale | Définition |
|---|---|
| **Normatifs** | Documents qui édictent des règles, obligations, politiques, socle, états, invariants applicables au cadre AKORIS |
| **Opérationnels** | Documents qui décrivent comment exécuter, démarrer, rapporter, auditer — guides, manuels, prompts, modèles, constat d'implémentation |
| **Explicatifs** | Documents qui présentent, introduisent, naviguent, expliquent le cadre sans édicter de règle (point d'entrée, vocabulaire, carte, journal) |
| **Historiques / sources** | Documents sources qui ont alimenté la rédaction, antérieurs au corpus produit, sans autorité normative par défaut |

---

## 2. Tableau de classification

| # | Fichier | Catégorie principale | Catégorie(s) secondaire(s) | Justification |
|---|---|---|---|---|
| 1 | `00_cartographie.md` | Explicatif | Historique / sources | Diagnostic de l'existant, document de travail (TRAVAIL), photographie historique ; pas de règle normative |
| 2 | `changelog.md` | Explicatif | sans objet | Journal de maintenance, non normatif ; centralise des historiques existants |
| 3 | `plan_de_consolidation.md` | Opérationnel | Normatif (plan de gouvernance) | Plan de travail C0–C5 avec règles Git, points HVG, registre de suivi ; catégorie secondaire normatif car il porte des règles de livraison |
| 4 | `README.md` | Explicatif | Normatif (règles de maintenance) | Point d'entrée et parcours de lecture ; §8 porte 8 règles de maintenance documentaire (catégorie secondaire normatif limitée) |
| 5 | `state.json` | Opérationnel | sans objet | État opérationnel machine, source de vérité du projet en cours |
| 6 | `_sources/AKORIS_architecture_documentaire.md` | Historique / sources | Explicatif | Source F2, plan d'architecture antérieur au corpus produit ; niveau 3 d'autorité |
| 7 | `_sources/AKORIS_consolide.md` | Historique / sources | Explicatif | Source F3, référence doctrinale v1.0, antérieure au corpus produit ; niveau 2 d'autorité |
| 8 | `_sources/akoris_documentation_builder.md` | Historique / sources | Opérationnel (méthode) | Source F4, mandat et méthode du rédacteur, antérieur au corpus produit ; niveau 4 d'autorité |
| 9 | `implementations/opencode/README.md` | Explicatif | Opérationnel (constat) | Présentation descriptive de l'implémentation OpenCode ; non normatif |
| 10 | `implementations/opencode/agent_permissions.md` | Opérationnel | Explicatif | Constat technique des permissions observées ; non normatif (« ne définit aucune règle de gouvernance ») |
| 11 | `implementations/opencode/environment_requirements.md` | Explicatif | Opérationnel (prérequis) | Prérequis d'environnement observés, non certification |
| 12 | `implementations/opencode/frontmatter_reference.md` | Explicatif | Opérationnel (référence outil) | Référence descriptive du frontmatter OpenCode observé |
| 13 | `implementations/opencode/limitations.md` | Explicatif | Opérationnel (limites) | Limites de l'implémentation observée, fondé sur le constat du pilote |
| 14 | `prompts/akoris_auditor_bootstrap.md` | Opérationnel | sans objet | Prompt opérationnel d'amorçage du rôle AUDITOR |
| 15 | `prompts/akoris_builder_bootstrap.md` | Opérationnel | sans objet | Prompt opérationnel d'amorçage du rôle BUILDER |
| 16 | `prompts/akoris_documentation_builder.md` | Opérationnel | sans objet | Prompt opérationnel d'amorçage du rôle DOCUMENTATION BUILDER |
| 17 | `prompts/akoris_orchestrator_bootstrap.md` | Opérationnel | sans objet | Prompt opérationnel d'amorçage du rôle ORCHESTRATOR |
| 18 | `protocol/audit_policy.md` | Normatif | Opérationnel (méthode) | Politique d'audit source unique ; §17 définit le rapport attendu (opérationnel) |
| 19 | `protocol/change_control.md` | Normatif | sans objet | Politique de contrôle des changements, source unique |
| 20 | `protocol/decision_policy.md` | Normatif | sans objet | Politique de décision, source unique des valeurs de décision |
| 21 | `protocol/getting_started.md` | Opérationnel | Normatif (synthèse) | Manuel pédagogique complet ; synthèse orientée références ; validé VALIDATOR 2026-11-21 |
| 22 | `protocol/governance_core.md` | Normatif | sans objet | Socle commun obligatoire, 54 règles GC-01 à GC-54 |
| 23 | `protocol/permission_policy.md` | Normatif | Opérationnel (matrice) | Politique des permissions, source unique ; matrice des permissions (opérationnel) |
| 24 | `protocol/profile_lite.md` | Normatif | sans objet | Profil de gouvernance Lite, niveau d'exigence |
| 25 | `protocol/profile_reinforced.md` | Normatif | sans objet | Profil de gouvernance Reinforced, niveau d'exigence |
| 26 | `protocol/profile_standard.md` | Normatif | sans objet | Profil de gouvernance Standard, profil par défaut |
| 27 | `protocol/recovery_policy.md` | Normatif | sans objet | Politique de reprise et d'incident, source unique |
| 28 | `protocol/state_model.md` | Normatif | sans objet | Modèle d'état, états, invariants, structure de `state.json` |
| 29 | `protocol/transition_policy.md` | Normatif | Opérationnel (reçu) | Politique des transitions et reçus ; mécanisme de reçu (opérationnel) |
| 30 | `reference/document_map.md` | Explicatif | Normatif (index) | Carte documentaire, index du corpus ; §8 sources uniques portee normative limitée |
| 31 | `reference/state.schema.json` | Normatif | Technique | Schéma technique v2.0 de `state.json`, décision C28 |
| 32 | `reference/terminology.md` | Explicatif | Normatif (terminologique) | Vocabulaire unique, source unique du vocabulaire ; statut normatif terminologique |
| 33 | `reference/traceability_map.md` | Explicatif | Normatif (index de traçabilité) | Carte de traçabilité, renvois aux sources uniques ; valide VALIDATOR 2026-11-21 |
| 34 | `reference/versioning_policy.md` | Normatif | sans objet | Politique de versionnement, source normative des catégories de versions ; validé VALIDATOR 2026-11-21 |
| 35 | `templates/auditor_report_template.md` | Opérationnel | sans objet | Modèle générique de rapport d'audit |
| 36 | `templates/builder_report_template.md` | Opérationnel | sans objet | Modèle générique de rapport de sprint |
| 37 | `templates/change_request_template.md` | Opérationnel | sans objet | Modèle générique de demande de changement |
| 38 | `templates/decision_template.md` | Opérationnel | sans objet | Modèle générique de décision du VALIDATOR |
| 39 | `templates/orchestrator_report_template.md` | Opérationnel | sans objet | Modèle générique de rapport ORCHESTRATOR |
| 40 | `templates/reserve_template.md` | Opérationnel | sans objet | Modèle générique de réserve |
| 41 | `templates/transition_receipt_template.md` | Opérationnel | sans objet | Modèle générique de reçu de transition |
| 42 | `livrables/C0/mandat_builder.md` | Opérationnel | sans objet | Mandat C0, cadre de travail du BUILDER DOCUMENTAIRE |
| 43 | `livrables/C0/transition/notification_builder.md` | Opérationnel | sans objet | Notification de transition C0 |
| 44 | `livrables/C0/transition/reception_transition.md` | Opérationnel | sans objet | Réception de transition C0 |
| 45 | `livrables/C0/transition/recu_transition_C0.md` | Opérationnel | sans objet | Reçu de transition C0 (preuve d'événement) |

---

## 3. Compte par catégorie

| Catégorie principale | Nombre de documents | Pourcentage |
|---|---|---|
| Normatifs | 13 (fichiers 18–23, 25–30, 31, 34) | 28,9 % |
| Opérationnels | 21 (fichiers 3, 5, 9–17, 35–45) | 46,7 % |
| Explicatifs | 8 (fichiers 1–2, 4, 8, 9, 11–13, 30, 32–33) | 17,8 % |
| Historiques / sources | 3 (fichiers 6–8) | 6,7 % |
| **Total** | **45** | **100 %** |

> **Note sur les documents avec catégorie secondaire** : 4 documents portent une catégorie secondaire justifiée (`00_cartographie.md`, `README.md`, `plan_de_consolidation.md`, `protocol/getting_started.md`, `protocol/audit_policy.md`, `protocol/permission_policy.md`, `protocol/transition_policy.md`, `reference/document_map.md`, `reference/terminology.md`, `reference/traceability_map.md`). La catégorie principale reste unique par document.

---
*Fin de C0-04. Classification figée à la date d'exécution : 2026-11-24. Conformité à la réserve R2 (catégorie principale + secondaires justifiées).*