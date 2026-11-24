# C0-02 — Inventaire des fichiers et répertoires

**Tâche** : C0-02 — Inventorier fichiers et répertoires  
**Date d'exécution** : 2026-11-24  
**Périmètre** : `C:\Methode_AKORIS` (racine + `_sources`, `implementations`, `prompts`, `protocol`, `reference`, `templates`, `livrables/C0`)  
**Contrainte** : Pas de modification source — inventaire en lecture seule

---

## 1. Arborescence des répertoires

```
C:\Methode_AKORIS/
├── 00_cartographie.md
├── changelog.md
├── plan_de_consolidation.md      (non suivi / untracked)
├── README.md
├── state.json                    (non suivi / untracked)
├── .git/                         (répertoire Git, non listé dans l'inventaire documentaire)
├── _sources/
│   ├── AKORIS_architecture_documentaire.md
│   ├── AKORIS_consolide.md
│   └── akoris_documentation_builder.md
├── implementations/
│   └── opencode/
│       ├── README.md
│       ├── agent_permissions.md
│       ├── environment_requirements.md
│       ├── frontmatter_reference.md
│       └── limitations.md
├── livrables/
│   └── C0/
│       ├── mandat_builder.md
│       ├── transition/
│       │   ├── notification_builder.md
│       │   ├── reception_transition.md
│       │   └── recu_transition_C0.md
│       ├── inventaire/           (répertoires de livrables créés, vides à l'origine)
│       ├── metadonnees/
│       ├── classification/
│       ├── decisions/
│       ├── registres/
│       ├── lacunes/
│       ├── sources_historique/
│       ├── stats_doc/
│       ├── reference/
│       ├── rapport/
│       └── perimetre-C1/
├── prompts/
│   ├── akoris_auditor_bootstrap.md
│   ├── akoris_builder_bootstrap.md
│   ├── akoris_documentation_builder.md
│   └── akoris_orchestrator_bootstrap.md
├── protocol/
│   ├── audit_policy.md
│   ├── change_control.md
│   ├── decision_policy.md
│   ├── getting_started.md
│   ├── governance_core.md
│   ├── permission_policy.md
│   ├── profile_lite.md
│   ├── profile_reinforced.md
│   ├── profile_standard.md
│   ├── recovery_policy.md
│   ├── state_model.md
│   └── transition_policy.md
├── reference/
│   ├── document_map.md
│   ├── state.schema.json
│   ├── terminology.md
│   ├── traceability_map.md
│   └── versioning_policy.md
└── templates/
    ├── auditor_report_template.md
    ├── builder_report_template.md
    ├── change_request_template.md
    ├── decision_template.md
    ├── orchestrator_report_template.md
    ├── reserve_template.md
    └── transition_receipt_template.md
```

> **Note** : Les sous-répertoires de `livrables/C0/` (inventaire, metadonnees, classification, decisions, registres, lacunes, sources_historique, stats_doc, reference, rapport, perimetre-C1) sont créés pour recevoir les livrables C0. Aucun n'est listé dans le commit initial car ils appartiennent à l'espace de livraison C0, non au corpus source.

---

## 2. Liste exhaustive des fichiers par répertoire

### 2.1 Racine (5 fichiers)

| # | Fichier | État Git | Taille approximative | Rôle identifié |
|---|---|---|---|---|
| 1 | `00_cartographie.md` | Tracké (commit initial) | ~30 Ko | Cartographie documentaire (v0.1, PROPOSITION) |
| 2 | `changelog.md` | Tracké (commit initial) | ~18 Ko | Journal du cadre documentaire |
| 3 | `plan_de_consolidation.md` | **Untracked** (nouveau) | ~11 Ko | Plan de consolidation C0-C5 |
| 4 | `README.md` | Tracké (commit initial) | ~13 Ko | Point d'entrée documentation AKORIS |
| 5 | `state.json` | **Untracked** (nouveau) | ~3,6 Ko | État opérationnel (source de vérité machine) |

### 2.2 `_sources/` (3 fichiers — sources historiques)

| # | Fichier | État Git | Rôle |
|---|---|---|---|
| 6 | `AKORIS_architecture_documentaire.md` | Tracké | Plan d'architecture documentaire (source F2, niveau 3) |
| 7 | `AKORIS_consolide.md` | Tracké | Référence doctrinale du cadre (source F3, niveau 2) |
| 8 | `akoris_documentation_builder.md` | Tracké | Mandat et méthode du rédacteur documentaire (source F1, niveau 4) |

### 2.3 `implementations/opencode/` (5 fichiers — constat d'implémentation)

| # | Fichier | État Git | Rôle |
|---|---|---|---|
| 9 | `README.md` | Tracké | Présentation de l'implémentation OpenCode |
| 10 | `agent_permissions.md` | Tracké | Constat des permissions observées (v0.4) |
| 11 | `environment_requirements.md` | Tracké | Prérequis d'environnement observés |
| 12 | `frontmatter_reference.md` | Tracké | Référence de frontmatter OpenCode |
| 13 | `limitations.md` | Tracké | Limites de l'implémentation observée |

### 2.4 `prompts/` (4 fichiers — amorçage des rôles)

| # | Fichier | État Git | Rôle |
|---|---|---|---|
| 14 | `akoris_auditor_bootstrap.md` | Tracké | Prompt AUDITOR (vague 6) |
| 15 | `akoris_builder_bootstrap.md` | Tracké | Prompt BUILDER (vague 6) |
| 16 | `akoris_documentation_builder.md` | Tracké | Prompt DOCUMENTATION BUILDER (vague 6) |
| 17 | `akoris_orchestrator_bootstrap.md` | Tracké | Prompt ORCHESTRATOR (vague 6) |

### 2.5 `protocol/` (12 fichiers — normes)

| # | Fichier | État Git | Rôle |
|---|---|---|---|
| 18 | `audit_policy.md` | Tracké | Politique d'audit (v0.3, vague 5) |
| 19 | `change_control.md` | Tracké | Contrôle des changements (v0.1, vague 4) |
| 20 | `decision_policy.md` | Tracké | Politique de décision (v0.1, vague 4) |
| 21 | `getting_started.md` | Tracké | Manuel de démarrage (vague 7, VALIDÉ VALIDATOR 2026-11-21) |
| 22 | `governance_core.md` | Tracké | Socle de gouvernance (v0.1, vague 1) |
| 23 | `permission_policy.md` | Tracké | Politique des permissions (v0.3, vague 3) |
| 24 | `profile_lite.md` | Tracké | Profil Lite (vague 2) |
| 25 | `profile_reinforced.md` | Tracké | Profil Reinforced (vague 2) |
| 26 | `profile_standard.md` | Tracké | Profil Standard (vague 2) |
| 27 | `recovery_policy.md` | Tracké | Politique de reprise et d'incident (v0.2, vague 4) |
| 28 | `state_model.md` | Tracké | Modèle d'état (v0.2, vague 3) |
| 29 | `transition_policy.md` | Tracké | Politique des transitions (v0.2, vague 3) |

### 2.6 `reference/` (5 fichiers — référentiels)

| # | Fichier | État Git | Rôle |
|---|---|---|---|
| 30 | `document_map.md` | Tracké | Carte documentaire (v0.4, vague 1) |
| 31 | `state.schema.json` | Tracké | Schéma technique state.json v2.0 (maintenance) |
| 32 | `terminology.md` | Tracké | Terminologie AKORIS (v0.3, vague 1) |
| 33 | `traceability_map.md` | Tracké | Carte de traçabilité (v0.1, vague 7, VALIDÉ VALIDATOR 2026-11-21) |
| 34 | `versioning_policy.md` | Tracké | Politique de versionnement (v0.1, vague 7, VALIDÉ VALIDATOR 2026-11-21) |

### 2.7 `templates/` (7 fichiers — modèles de livrables)

| # | Fichier | État Git | Rôle |
|---|---|---|---|
| 35 | `auditor_report_template.md` | Tracké | Modèle rapport AUDITOR (vague 6) |
| 36 | `builder_report_template.md` | Tracké | Modèle rapport BUILDER (vague 6) |
| 37 | `change_request_template.md` | Tracké | Modèle demande de changement (vague 6) |
| 38 | `decision_template.md` | Tracké | Modèle décision VALIDATOR (vague 6) |
| 39 | `orchestrator_report_template.md` | Tracké | Modèle rapport ORCHESTRATOR (vague 6) |
| 40 | `reserve_template.md` | Tracké | Modèle réserve (vague 6) |
| 41 | `transition_receipt_template.md` | Tracké | Modèle reçu de transition (vague 6) |

### 2.8 `livrables/C0/` (4 fichiers — livrables C0 préexistants + nouveaux)

| # | Fichier | État Git | Rôle |
|---|---|---|---|
| 42 | `mandat_builder.md` | Untracked | Mandat opérationnel C0 (présent avant exécution) |
| 43 | `transition/notification_builder.md` | Untracked | Notification de transition vers BUILDER |
| 44 | `transition/reception_transition.md` | Untracked | Réception de transition C0 |
| 45 | `transition/recu_transition_C0.md` | Untracked | Reçu de transition C0 (déjà déposé) |

---

## 3. Compte par répertoire

| Répertoire | Fichiers | Sous-répertoires |
|---|---|---|
| Racine | 5 | 8 (`_sources`, `implementations`, `livrables`, `prompts`, `protocol`, `reference`, `templates`, `.git`) |
| `_sources/` | 3 | 0 |
| `implementations/opencode/` | 5 | 0 |
| `livrables/C0/` | 4 | 11 (`inventaire`, `metadonnees`, `classification`, `decisions`, `registres`, `lacunes`, `sources_historique`, `stats_doc`, `reference`, `rapport`, `perimetre-C1`, `transition`) |
| `prompts/` | 4 | 0 |
| `protocol/` | 12 | 0 |
| `reference/` | 5 | 0 |
| `templates/` | 7 | 0 |
| **Total fichiers documentaires** | **45** | — |

---

## 4. Fichiers racine identifiés

Le mandat C0-02 cite spécifiquement `plan_de_consolidation.md`, `README.md`, `changelog.md`, `00_cartographie.md` comme fichiers racine. L'inventaire confirme leur présence, ergänzt par `state.json` (fichier racine supplémentaire, untracked).

| Fichier racine | Présent | Tracké | Rôle |
|---|---|---|---|
| `plan_de_consolidation.md` | Oui | Non (untracked) | Plan de consolidation C0-C5 |
| `README.md` | Oui | Oui | Point d'entrée documentation |
| `changelog.md` | Oui | Oui | Journal du cadre |
| `00_cartographie.md` | Oui | Oui | Cartographie documentaire |
| `state.json` | Oui | Non (untracked) | État opérationnel machine |

---

## 5. Absence de `.gitignore`

Aucun fichier `.gitignore` n'est présent à la racine du dépôt. Cette absence est constatée (voir réserve R5 : politique d'inclusion/exclusion à documenter).

---
*Fin de C0-02. Inventaire figé à la date d'exécution : 2026-11-24. Nombre total de fichiers documentaires : 45 (39 trackés + 6 untrackés).*