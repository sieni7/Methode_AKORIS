# C0-07 — Carte des dépendances

**Tâche** : C0-07 — Identifier lacunes, questions et dépendances  
**Sous-tâche** : Dépendances entre documents et entre documents et externalités  
**Date d'exécution** : 2026-11-24  
**Contrainte** : Ne pas résoudre les dépendances — les repérer uniquement

---

## 1. Méthode

Une dépendance est un lien de reliance entre deux documents, ou entre un document et une entité externe (pilote, schéma JSON, décision humaine, etc.). Les dépendances sont listées sans être résolues.

---

## 2. Dépendances entre documents (du corpus AKORIS)

### 2.1 Dépendances documentées dans `document_map.md` §9

```
terminology
    │
    ├── governance_core ──────────────┐
    │        │                        │
    │        ├── profile_standard     │
    │        │        ├── profile_lite
    │        │        └── profile_reinforced
    │        │                        │
    │        └── state_model ─────────┤
    │                 ├── transition_policy
    │                 ├── permission_policy ── implementations/opencode/*
    │                 ├── decision_policy ── change_control
    │                 │        └── recovery_policy
    │                 └── audit_policy
    │
    ├── document_map
    └── README
         prompts/* ── dépendent de tout le socle
         templates/* ── dépendent des politiques
         getting_started ── dépend de tout
```

**Conséquence documentée** : un document ne se rédige jamais avant ses dépendances. C'est ce qui fixe l'ordre des vagues.

---

## 3. Dépendances détaillées par document (extrait des fiches `document_map.md` §4)

| Document | Dépend de | Observations |
|---|---|---|
| `governance_core.md` | `terminology.md` | Socle, règle de base |
| `profile_standard.md` | `governance_core.md` | Vague 2 |
| `profile_lite.md` | `profile_standard.md` | Vague 2 |
| `profile_reinforced.md` | `profile_standard.md` | Vague 2 |
| `state_model.md` | `governance_core.md` | Vague 3 |
| `transition_policy.md` | `state_model.md` | Vague 3 |
| `permission_policy.md` | `state_model.md` | Vague 3 |
| `decision_policy.md` | `governance_core.md` | Vague 4 |
| `change_control.md` | `decision_policy.md` | Vague 4 |
| `recovery_policy.md` | `state_model.md` | Vague 4 |
| `audit_policy.md` | `decision_policy.md`, `permission_policy.md` | Vague 5 |
| `getting_started.md` | tout le socle | Vague 7 |
| `prompts/*` | tout le socle | Vague 6 |
| `templates/*` | les politiques | Vague 6 |
| `document_map.md` | `terminology.md` | Vague 1 |
| `traceability_map.md` | tout le protocole | Vague 7 |
| `versioning_policy.md` | `state_model.md`, A7 | Vague 7 |

---

## 4. Dépendances avec sources historiques (_sources/)

| Document cible | Dépend de (source historique) | Nature de la dépendance |
|---|---|---|
| `governance_core.md` | `AKORIS_consolide.md` (F3), `AKORIS_architecture_documentaire.md` (F2), `akoris_documentation_builder.md` (F1) | Sources citées en tête de document |
| `decision_policy.md` | `AKORIS_consolide.md` §8, §9 ; `AKORIS_architecture_documentaire.md` §4.7 | Sources citées |
| `state_model.md` | `AKORIS_consolide.md` §6, §7 ; `AKORIS_architecture_documentaire.md` §4.6 | Sources citées |
| `transition_policy.md` | `AKORIS_consolide.md` §6, §10.5 ; `AKORIS_architecture_documentaire.md` | Sources citées |
| `permission_policy.md` | `AKORIS_consolide.md` §12, §13 ; `AKORIS_architecture_documentaire.md` §4.10 | Sources citées |
| `audit_policy.md` | `AKORIS_consolide.md` §11, §14, §15 ; `AKORIS_architecture_documentaire.md` §4.9, §8.5, §8.9, §10.5 | Sources citées |
| `00_cartographie.md` | `AKORIS_consolide.md` (F3), `AKORIS_architecture_documentaire.md` (F2), `akoris_documentation_builder.md` (F1) | Sources citées |
| `versioning_policy.md` | `AKORIS_architecture_documentaire.md` §16 (F2) | Source citée (F2) |

---

## 5. Dépendances avec le projet gouverné (hors périmètre documentaire)

| Document AKORIS | Dépend de (projet gouverné) | Nature |
|---|---|---|
| `state_model.md` | `state.json` (schéma v2.0) | Structure d'état |
| `transition_policy.md` | `state.json` (champ `transition`) | État de transition |
| `permission_policy.md` | `implementations/opencode/agent_permissions.md` | Constat de configuration réelle |
| `reference/document_map.md` §6 | `state.json`, `state.md`, `current_sprint.md`, `contexte.md`, `agents.md`, `docs/*`, `sprints/*`, `sprint_report/`, `audit_report/`, `debt_report/` | Documents du projet gouverné (hors périmètre) |
| `traceability_map.md` §2 | `docs/**`, `current_sprint.md`, `state.json`, `sprint_report/`, `audit_report/`, `docs/governance/**` du projet gouverné | Données propres à un projet (hors périmètre, aucune valeur renseignée) |

---

## 6. Dépendances avec externalités

| Dépendance | Entité externe | Nature | Statut |
|---|---|---|---|
| Schéma JSON | `https://json-schema.org/draft/2020-12/schema` | Référence méta-schéma de `state.schema.json` | Externe |
| OpenCode V2 | Documentation OpenCode (agents, permissions) | Référence pour le frontmatter et le schéma de permissions | Externe, non certifiée |
| Projet pilote `demo_web` | `C:\demo_web - Copie\*` | Matériel d'implémentation, preuves, manuel v1 | Niveau 5, non doctrinal |
| Projet pilote `demo_web` (variante allégée) | `C:\demo_web` | `state.json`, `rapports/`, `transitions/` | Niveau 5, non doctrinal |
| Dépôt Git distant | `remotes/origin/main` | Branche distante synchronisée | Externe au working tree local |

---

## 7. Dépendances critiques non résolues (liens avec les lacunes)

| Dépendance | Liée à la lacune | Pourquoi non résolue |
|---|---|---|
| Registre des décisions (`decision_log.md`) | L1 | Fichier annoncé, non créé |
| Validation JSON Schema de `state.json` | L2 | Aucun validateur nommé, pas de preuve d'exécution |
| Procédure de migration v1.0 → v2.0 | L3 | À ARBITRER (A16 différé) |
| Matrice complète des permissions | L4 | Matrice proposée, non exhaustive |
| Identifiants d'exigence et de tâche | L7 | Aucun format normatif |
| Durée de conservation des preuves/réçus | L12 | Non définie (INCONNU) |

---
*Fin de la carte des dépendances. Aucune dépendance résolue. Total : dépendances documentées (document_map §9), fiches dépendances (document_map §4), dépendances sources historiques, dépendances projet gouverné, dépendances externalités, dépendances critiques non résolues.*