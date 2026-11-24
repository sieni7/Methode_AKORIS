# AKORIS — Cartographie documentaire

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Auteur | DOCUMENTATION BUILDER |
| Portée | État de l'existant, contradictions, cible, ordre de rédaction |
| Ne contient pas | Règles du protocole, décisions de projet, contenu définitif des documents |

> **Bandeau historique (2026-11-21).** Ce fichier est une photographie historique et un document de travail. La définition de T4 en §11.4 (« sous AUDITOR, tenter une édition de `src/**` ») décrit l'état antérieur aux arbitrages ; la définition courante figure dans [permission_policy.md](protocol/permission_policy.md). Aucun test T1 à T5 n'a été exécuté du fait de cette mention, et aucune permission n'est certifiée. Le contenu historique ci-dessous n'est pas réécrit.

> Ce document est une **cartographie**, pas un document normatif.
> Les éléments marqués `RECOMMANDATION` ne sont pas des décisions validées.
> Les éléments marqués `À ARBITRER` ne doivent pas être rédigés avant arbitrage.

> **Note de maintenance — 2026-11-20.** Les constats ci-dessous conservent la photographie historique de la cartographie initiale : « aucun document de la cible n'existe », « 0 sur 34 », etc. Depuis, la vague 6 a produit quatre prompts (`prompts/`) et sept modèles (`templates/`) ; l'état actuel est décrit dans la [carte documentaire](reference/document_map.md) §3 et §4.4–4.5. Les contradictions ouvertes, dont D5 et D6, ne sont pas tranchées dans cette note.

---

## 0. Objet

Établir l'état exact du corpus documentaire AKORIS avant toute rédaction, afin de :

- éviter de créer des documents sur des bases contradictoires ;
- identifier une source de référence unique par information ;
- fixer un ordre de rédaction piloté par les dépendances ;
- rendre explicites les décisions qui appartiennent au VALIDATOR.

---

## 1. Synthèse

1. `documentation/` ne contient **que des sources** : 3 fichiers, aucun document produit, aucun sous-dossier.
2. La cible consolidée compte **34 fichiers structurants** ; **0 sur 34** existe.
3. Les trois sources sont cohérentes sur l'intention, mais divergent sur des points d'exécution (décisions, schéma d'état, profils, transitions).
4. Le projet pilote `demo_web` implémente une **version antérieure** du cadre : sans profils, 3 valeurs de décision, `state.json` v1.0, 5 états de transition.
5. Le **mécanisme de reçu de transition** est un composant réel et central du dispositif v1 : il doit devenir une politique à part entière.
6. Les permissions du pilote sont **déclarées dans un schéma valide**, mais leur application effective **n'est pas prouvée** et présente une faille de contournement connue.
7. **7 arbitrages** restent ouverts (A1→A7) ; A8 est tranché.
8. La rédaction peut démarrer sur le socle (vague 1) sans attendre A1→A7, mais **pas** sur l'état, les décisions et les profils.

---

## 2. Inventaire

### 2.1 Dossier `documentation/` (périmètre de production)

| ID | Fichier | Taille | Horodatage | Version déclarée |
|---|---|---|---|---|
| F1 | `akoris_documentation_builder.md` | 17 283 o | 20/11 07:51 | aucune |
| F2 | `AKORIS_architecture_documentaire.md` | 23 960 o | 20/11 07:39 | aucune |
| F3 | `AKORIS_consolide.md` | 22 900 o | 20/11 07:01 | « Version consolidée 1.0 » |

Aucun sous-dossier. Aucun dépôt Git. Aucun `getting_started.md` dans ce dossier.

### 2.2 Documents de référence externes (hors `documentation/`)

Projet pilote `C:\demo_web - Copie` :

| Élément | Taille | Nature |
|---|---|---|
| `getting_started.md` | 51,6 Ko | Manuel AKORIS v1 mono-profil (Blocs 00→08), lié à OpenCode |
| `agents.md` | 11,7 Ko | Contrats des 4 rôles, matrice de permissions, transitions, reçu, rapports, décisions, dette, blocages |
| `contexte.md` | 5,1 Ko | Synthèse de projet |
| `current_sprint.md` | 15,5 Ko | Mandat de sprint réel |
| `state.json` / `state.md` | 1,4 Ko | État opérationnel réel (`schema_version 1.0`) |
| `templates/` | 4 fichiers | `orchestrator`, `builder`, `auditor`, `debt_report` |
| `.opencode/agents/` | 3 fichiers | Bootstraps opérationnels réels avec frontmatter de permissions |
| `opencode.json` | 99 o | `$schema` + `instructions` uniquement |
| `docs/` | ~20 fichiers | ADR-001→009, requirements, architecture, risks, security, business_rules, readiness |
| `sprint_report/`, `audit_report/`, `debt_report/`, `sprints/` | — | Registres réels |

Variante allégée : `C:\demo_web` (`state.json`, `rapports/`, `transitions/`).

> **Règle de non-duplication (FAIT) :** le contenu de `docs/` du pilote (ADR, exigences, risques) appartient **au projet demo_web**, pas au cadre AKORIS. Il ne doit jamais être promu en règle du protocole. Il sert uniquement de **jeu d'essai** et de **preuve d'implémentation**.

### 2.3 Ce qui n'existe pas

Aucun document de la cible n'existe : ni `README.md` de documentation, ni `protocol/`, ni `prompts/`, ni `templates/`, ni `reference/`, ni `implementations/`, ni `changelog.md`.

---

## 3. Rôle et autorité des sources

Hiérarchie appliquée (prompt §4) :

| Niveau | Source | Usage |
|---|---|---|
| 1 | Décision humaine validée (VALIDATOR) | Prime sur tout |
| 2 | `AKORIS_consolide.md` (v1.0) | Doctrine du cadre |
| 3 | `AKORIS_architecture_documentaire.md` | Plan d'architecture |
| 4 | `akoris_documentation_builder.md` + conventions de projet | Méthode de production |
| 5 | `getting_started.md` du pilote | **À ARBITRER** (A6) — matériau, pas doctrine |
| 6 | Propositions du DOCUMENTATION BUILDER | Jamais présentées comme validées |

| Fichier | Rôle retenu | Autorité | Statut |
|---|---|---|---|
| F3 `AKORIS_consolide.md` | Référence doctrinale : principes, rôles, profils, états, décisions, preuves, changements, audit, permissions, checkpoints | 2 | FAIT |
| F2 `AKORIS_architecture_documentaire.md` | Plan : arborescence, rôle de chaque fichier, mandats, contexte par agent | 3 | FAIT |
| F1 `akoris_documentation_builder.md` | Mandat du rédacteur : méthode, interdictions, format de rapport | 4 | FAIT |
| `getting_started.md` (pilote) | Manuel v1 opérationnel, monolithique | 5 | HYPOTHÈSE — A6 |
| `agents.md` (pilote) | Contrats + matrice de permissions + reçu | 4 (projet) | FAIT |

**Observation :** F3 est le document le plus ancien du dossier et pourtant le plus autoritaire. La récence ne vaut pas autorité : ce point doit rester explicite dans `document_map.md`.

---

## 4. Doublons

Doublon = information présente dans plusieurs documents **sans source principale désignée**.

| ID | Information | Emplacements | Traitement proposé |
|---|---|---|---|
| D1 | Objet, acronyme, définition | F3 §1 · F2 §1 · `getting_started` §0 | `README.md` + `terminology.md` |
| D2 | Rôles et responsabilités | F3 §3 · F2 §6.3/§13 · `getting_started` Bloc 05 · `agents.md` | `governance_core.md` |
| D3 | Sources de référence uniques | F3 §5.1 · F2 §9 · `getting_started` 06.4 | `reference/document_map.md` |
| D4 | États projet/sprint/transition | F3 §6 · F2 §4.6 · `getting_started` 06.6-06.8 · `state.json` | `state_model.md` + `transition_policy.md` |
| D5 | Schéma `state.json` | F3 §7 · `getting_started` 06.5 · `state.json` réel | `state_model.md` + `state.schema.json` |
| D6 | Arborescence projet | F3 §17 · F2 §3 · `getting_started` 06.3 · pilote | `document_map.md` |
| D7 | Checkpoints CP1/CP2/CP3 | F3 §14 · F2 §14 · `getting_started` 01.5/04.7/08 | `getting_started.md` |
| D8 | Cycle nominal de sprint | F3 §15 · F2 §14 · `getting_started` §5 | `getting_started.md` |
| D9 | Règles Git / fusion `main` | F3 §16 · F2 §4.10 · `getting_started` 06.13 | `permission_policy.md` |
| D10 | Valeurs et conditions de décision | F3 §8 · F2 §4.7 · `getting_started` 5.5 | `decision_policy.md` |
| D11 | Contenu des rapports | F3 §11.2 · F2 §15 · `getting_started` 05.7 · `templates/` | `templates/*` |
| D12 | Ordre d'implémentation | F2 §11 · F1 §8 | Cette cartographie |
| D13 | Architecture cible | F2 §3 · F1 §6 | Cette cartographie |
| D14 | **Permissions** | F3 §12-13 · F2 §4.10 · `getting_started` 05.6 · `agents.md` §6 · frontmatter `.opencode/agents/` | `permission_policy.md` + `implementations/opencode/agent_permissions.md` |
| D15 | **Reçu de transition** | `getting_started` 06.9 · `agents.md` §7 · F3 §6.4 (`receipt_reference`) | `transition_policy.md` |

**Doublons les plus coûteux :** D2, D3, D5, D14 — toute évolution y crée immédiatement une divergence.

---

## 5. Contradictions

### 5.1 Bloquantes — empêchent de rédiger

| ID | Contradiction | Sources en conflit | Bloque |
|---|---|---|---|
| C1 | **Valeurs de décision : 3 ou 5 ?** `GO / NO GO / GO WITH RESERVES` **vs** `GO / GO_WITH_RESERVES / NO_GO / HOLD / CANCELLED` | `getting_started` 5.5 + pilote **vs** F3 §8.1 | `decision_policy.md` |
| C2 | **Orthographe canonique** des identifiants : espaces vs underscore (`GO WITH RESERVES` / `GO_WITH_RESERVES`) | `getting_started` **vs** F3 | `decision_policy.md`, modèles |
| C3 | **Deux schémas `state.json` incompatibles** : v1.0 plat (`current_agent`, `protocol_version`, `human_validation_required`, `authorization.token`) vs v2.0 imbriqué (`protocol`, `agent`, `governance`, `checkpoints`, `blockers`, `reserves`, `change_control`, `permission_violations`) | F3 §7 **vs** `getting_started` 06.5 + `state.json` | `state_model.md` |
| C4 | **Profils absents de l'opérationnel** : F3 en fait le cœur du cadre ; `getting_started` et le pilote n'en ont aucune trace | F3 §4 **vs** pilote | `profile_*.md`, `governance_core.md` |
| C5 | **Trois chemins racine** pour le socle : `governance/` (F3, 4 fichiers) · `protocol/` racine projet (F2, 11 fichiers) · `documentation/protocol/` (F1) | F3 · F2 · F1 | `document_map.md` |

### 5.2 Majeures — déforment le sens

| ID | Contradiction | Détail | Statut |
|---|---|---|---|
| C6 | Collision `README.md` | F2 §6.1 = README projet (installation) ; F1 §6 = README documentation | À ARBITRER (A4) |
| C7 | **Cycle de transition : 9 ou 5 états ?** | F3 : `draft, awaiting_human_go, authorized, consumed, in_progress, completed, rejected, expired, cancelled` · `getting_started` 06.8 : sans `draft`, `consumed`, `expired`, `rejected` | À ARBITRER (A2) |
| **C8** | **Preuve de consommation d'une autorisation** | F3 sépare autorisation / consommation / exécution mais **ne décrit aucun mécanisme**. `getting_started` 06.9 + `agents.md` §7 imposent un **reçu de transition** déposé par B et C dans leurs répertoires, parce qu'ORCHESTRATOR est seul rédacteur de `state.json`. | **RÉVISÉ — voir §5.4** |
| C9 | Cadre générique ou lié à l'outil | `getting_started` structuré autour des « trois onglets OpenCode » ; F3 agnostique ; F2 parle d'« onglet A/B/C » | **TRANCHÉ (A8)** |
| **C10** | **Niveau réel des permissions** | F3 §12 : « dans un environnement partagé, les permissions sont principalement procédurales sauf preuve technique contraire ». Le pilote contient une preuve technique **partielle** (frontmatter OpenCode). | **RÉVISÉ — voir §5.4** |
| C11 | Liste des rôles : 3 ou 4 ? | F3, F2, `getting_started` = 3 agents + VALIDATOR ; F1 ajoute DOCUMENTATION BUILDER | À ARBITRER (A5) |

### 5.3 Mineures

| ID | Contradiction |
|---|---|
| C12 | Tables des sources divergentes : F3 §5.1 contient `use_cases` sans `incidents` ; F2 §9 contient `incidents` sans `use_cases` ; seule F2 mentionne `sprints/` |
| C13 | Emplacements des audits de préparation : `docs/governance/readiness/` (F2 §8.9) vs `docs/governance/initialization_readiness_report.md` (pilote) |
| C14 | Jeu de modèles : F2 liste 7 modèles ; le pilote en a 4, dont `debt_report_template.md` absent de la cible |
| C15 | Versionnement ambigu : protocole 1.0 · `schema_version` 1.0 (réel) vs 2.0 (F3) |
| C16 | F3 §18 (charge 35–160 h) est un contenu de planification dans un document doctrinal |
| C17 | Ordres de rédaction divergents entre F2 §11 et F1 §8 |
| C18 | F3 §19 énumère 10 « décisions structurantes retenues » **sans identifiant ni registre** — en contradiction avec son propre principe 6 (traçabilité) |
| C19 | Le mot « audit » désigne deux activités : audit de **préparation** (Bloc 08) et audit de **sprint** (§11) |
| C20 | **Maquette fournie en Vague 0 incomplète** : l'arborescence de la consigne omet `protocol/profile_*.md`, `templates/` et `reference/`, alors que les vagues 2 et 6 les rédigent. Corrigé en §8.1 ; à confirmer |

### 5.4 Révisions apportées à la demande du VALIDATOR

**C8 — Le reçu de transition est un composant central, pas une hypothèse.**
`agents.md` contient un chapitre `TRANSITION RECEIPT` complet, et `getting_started` 06.9 en décrit le cycle (vérification du jeton → absence de reçu antérieur → dépôt du reçu → horodatage → démarrage). Ce mécanisme existe parce qu'un seul agent écrit `state.json` : il est la **preuve de consommation** que F3 laisse implicite.
→ Conséquence : la politique des transitions ne peut pas rester un paragraphe de `state_model.md`. Elle devient `protocol/transition_policy.md`.

**C10 — Les permissions peuvent être techniquement imposées, mais doivent être vérifiées.**
Le frontmatter `.opencode/agents/*.md` est conforme au schéma OpenCode V2 (`permissions` = liste ordonnée de `{action, resource, effect}`). Cela autorise `technical_enforced` **sous conditions** — voir §11 pour le contrôle réalisé et ses réserves.
→ Conséquence : `permission_policy.md` doit porter une **procédure de vérification effective**, et `audit_policy.md` doit contrôler l'application, pas seulement la déclaration.

---

## 6. Fichiers manquants

### 6.1 Cible structurante — 34 fichiers, 0 existant

| Dossier | Fichiers | Existant |
|---|---|---|
| racine | `README.md`, `changelog.md` | 0 / 2 |
| `protocol/` | `getting_started`, `governance_core`, `profile_lite`, `profile_standard`, `profile_reinforced`, `state_model`, `transition_policy`, `decision_policy`, `change_control`, `audit_policy`, `permission_policy`, `recovery_policy` | 0 / 12 |
| `implementations/opencode/` | `README`, `agent_permissions`, `frontmatter_reference`, `environment_requirements`, `limitations` | 0 / 5 |
| `prompts/` | `akoris_orchestrator_bootstrap`, `akoris_builder_bootstrap`, `akoris_auditor_bootstrap`, `akoris_documentation_builder` | 0 / 4 |
| `templates/` | `orchestrator_report`, `builder_report`, `auditor_report`, `decision`, `change_request`, `reserve`, `transition_receipt` | 0 / 7 |
| `reference/` | `terminology`, `document_map`, `traceability_map`, `versioning_policy` | 0 / 4 |

### 6.2 Compléments recommandés (non couverts par la cible)

| Fichier | Justification |
|---|---|
| `reference/state.schema.json` | F3 §7 exige un état « vérifiable par schéma » ; aucun schéma n'existe |
| `reference/decision_log.md` | Aucun registre des décisions humaines ; comble C18 |
| `reference/identifiers.md` | Préfixes `TR-`, `CHG-`, `URG-`, `S0→S3`, `P0→P3`, `R0→R3` jamais regroupés |
| `protocol/profile_selection.md` | Critères de choix du profil dispersés ; c'est la première décision du projet |
| `templates/debt_report_template.md` | Existe dans le pilote, absent de la cible |
| `reference/pilot_mapping.md` | Correspondance manuel v1 → architecture cible, sans quoi la migration est perdue |

### 6.3 Manques internes aux sources

- Aucune date ni version sur F2 et F1.
- Aucun changelog du cadre, alors que F2 §17 l'exige.
- Aucune matrice de permissions complète (rôles × ressources × niveau).
- Aucune table de transition d'états (état × événement × état cible × acteur), exigée par F2 §11.
- Aucune définition de la frontière entre « audit de préparation » et « audit de sprint » (C19).

---

## 7. Décisions

### 7.1 Tranchées

| ID | Décision | Statut |
|---|---|---|
| **A8** | **Socle AKORIS agnostique de l'outil + OpenCode comme implémentation de référence documentée séparément.** Formulation retenue : « AKORIS définit un cadre de gouvernance agnostique de l'outil. OpenCode constitue une implémentation de référence pouvant fournir des contrôles techniques supplémentaires. » | **TRANCHÉ (VALIDATOR, 2026-11-20)** |

### 7.2 Ouvertes — bloquantes pour les vagues concernées

| ID | Question | Bloque | Recommandation du BUILDER |
|---|---|---|---|
| A1 | Valeurs de décision : 3 (v1) ou 5 (F3) ? Orthographe canonique ? | `decision_policy.md`, modèles | 5 valeurs + underscore — cohérent avec HOLD et CANCELLED, nécessaires au cadre |
| A2 | `state.json` cible : v1.0 plat ou v2.0 imbriqué ? Consommation par champ `consumed_at` ou par **reçu** ? | `state_model.md`, `transition_policy.md` | v2.0 + reçu conservé (C8) |
| A3 | Couche profils : activée, différée ou abandonnée ? | `profile_*.md`, `governance_core.md` | activée ; le pilote serait alors déclaré « non conforme, antérieur » |
| A4 | Chemin racine canonique et nom du README de documentation | `document_map.md`, tous les liens | `documentation/` autonome ; README projet distinct |
| A5 | Rôles : 3 agents + VALIDATOR, ou 4 avec DOCUMENTATION BUILDER ? | `governance_core.md`, `prompts/` | 4 rôles, le 4e étant documentaire et hors boucle d'exécution |
| A6 | Statut de `getting_started.md` v1 : source, matériau ou legacy ? | tout le contenu opérationnel | matériau de rédaction, pas source d'autorité |
| A7 | Schéma de versionnement (protocole / schéma / doc / mandat) | `versioning_policy.md`, `changelog.md` | 4 axes distincts, voir C15 |

---

## 8. Architecture cible

### 8.1 Arborescence consolidée

```text
documentation/
├── README.md
├── 00_cartographie.md          # ce document (document de travail)
├── changelog.md
│
├── protocol/
│   ├── getting_started.md
│   ├── governance_core.md
│   ├── profile_lite.md
│   ├── profile_standard.md
│   ├── profile_reinforced.md
│   ├── state_model.md
│   ├── transition_policy.md    # AJOUT — reçu, consommation, expiration
│   ├── decision_policy.md
│   ├── change_control.md
│   ├── audit_policy.md
│   ├── permission_policy.md
│   └── recovery_policy.md
│
├── implementations/
│   └── opencode/               # AJOUT — implémentation de référence
│       ├── README.md
│       ├── agent_permissions.md
│       ├── frontmatter_reference.md
│       ├── environment_requirements.md
│       └── limitations.md
│
├── prompts/
│   ├── akoris_orchestrator_bootstrap.md
│   ├── akoris_builder_bootstrap.md
│   ├── akoris_auditor_bootstrap.md
│   └── akoris_documentation_builder.md
│
├── templates/
│   ├── orchestrator_report_template.md
│   ├── builder_report_template.md
│   ├── auditor_report_template.md
│   ├── decision_template.md
│   ├── change_request_template.md
│   ├── reserve_template.md
│   └── transition_receipt_template.md
│
└── reference/
    ├── terminology.md
    ├── document_map.md
    ├── traceability_map.md
    └── versioning_policy.md
```

**Écart avec la maquette de la consigne (C20) :** `protocol/profile_*.md`, `templates/` et `reference/` ont été rétablis, car les vagues 2 et 6 les rédigent explicitement. À confirmer.

### 8.2 Fiche par fichier

| Fichier | Rôle | Source principale | Dépend de | Vague |
|---|---|---|---|---|
| `README.md` | Point d'entrée, carte de lecture, profils, prompts | F1 §7 | terminology, document_map | 1 |
| `changelog.md` | Journal du cadre | F2 §17 | A7 | 1 puis 7 |
| `protocol/governance_core.md` | Socle obligatoire commun | F3 §2-3, F2 §4.2 | terminology | 1 |
| `protocol/profile_standard.md` | Profil par défaut | F3 §4.2, F2 §4.4 | governance_core, A1, A3 | 2 |
| `protocol/profile_lite.md` | Faible risque | F3 §4.1, F2 §4.3 | profile_standard | 2 |
| `protocol/profile_reinforced.md` | Risque élevé | F3 §4.3, F2 §4.5 | profile_standard | 2 |
| `protocol/state_model.md` | États, invariants, schéma d'état | F3 §6-7, F2 §4.6 | A2 | 3 |
| `protocol/transition_policy.md` | Transitions, reçus, consommation, expiration | `getting_started` 06.6-06.9, `agents.md` §7 | state_model | 3 |
| `protocol/permission_policy.md` | 3 niveaux de permission, matrice, vérification | F3 §12-13, `agents.md` §6 | state_model, A8, §11 | 3 |
| `implementations/opencode/agent_permissions.md` | Permissions effectivement configurées | frontmatter réel | permission_policy | 3 |
| `implementations/opencode/README.md` | Vue d'ensemble de l'implémentation | — | A8 | 3 |
| `implementations/opencode/frontmatter_reference.md` | Schéma `permissions` OpenCode | doc OpenCode V2 | agent_permissions | 3 |
| `implementations/opencode/environment_requirements.md` | Hypothèses d'environnement | `opencode.json` | A8 | 3 |
| `implementations/opencode/limitations.md` | Limites et garanties non couvertes | §11 | agent_permissions | 3 |
| `protocol/decision_policy.md` | Décisions, gravités, preuves, réserves | F3 §8-9, F2 §4.7 | A1, state_model | 4 |
| `protocol/change_control.md` | Changements, impact, mandat | F3 §10, F2 §4.8 | decision_policy | 4 |
| `protocol/recovery_policy.md` | Blocage, reprise, rollback, incident | F3 §13, F2 §4.11 | state_model, permission_policy | 4 |
| `protocol/audit_policy.md` | Audit indépendant, preuves, permissions | F3 §11, F2 §4.9 | decision_policy, permission_policy | 5 |
| `prompts/*.md` (4) | Bootstraps courts et référentiels | F2 §5, `agents.md` | tout le socle | 6 |
| `templates/*.md` (7) | Modèles génériques | F2 §8.3 | politiques | 6 |
| `protocol/getting_started.md` | Manuel complet et pédagogique | `getting_started` v1, F2 §4.1 | tout | 7 |
| `reference/terminology.md` | Vocabulaire stable | F3 §1, F2 §18 | — | 1 |
| `reference/document_map.md` | Carte des sources et dépendances | F2 §9, F3 §5.1 | terminology | 1 |
| `reference/traceability_map.md` | Exigence → tâche → test → preuve → décision | F2 §16 | tout | 7 |
| `reference/versioning_policy.md` | Versionnement | F2 §16 | A7 | 7 |

### 8.3 Fichiers volontairement non créés

| Fichier | Raison |
|---|---|
| `protocol/profile_selection.md` | Utile, mais peut rester une section de `getting_started.md` tant que les profils ne sont pas activés (A3) |
| `reference/state.schema.json` | À créer avec `state_model.md` si A2 tranche v2.0 ; sinon sans objet |
| `reference/decision_log.md` | À créer dès la première décision du cadre (C18) |
| `templates/debt_report_template.md` | À créer avec les autres modèles si le registre de dette est retenu |

---

## 9. Ordre de rédaction

### Vague 0 — Cartographie *(ce document)*

Statut : **livrée, en attente de validation.**

### Vague 1 — Socle

`README.md` · `governance_core.md` · `document_map.md` · `terminology.md`

> **RECOMMANDATION :** ordre interne `terminology` → `governance_core` → `document_map` → `README`.
> Rédiger le README en premier fige des liens vers des documents dont le vocabulaire n'est pas encore stabilisé.
> Cette inversion est une proposition, pas une décision : l'ordre de la consigne reste applicable si le VALIDATOR le préfère.

### Vague 2 — Profils

`profile_standard.md` → `profile_lite.md` → `profile_reinforced.md`

> Standard d'abord (profil le plus dense), puis Lite par soustraction, Reinforced par addition : garantit la cohérence des trois.
> **Condition : A1 et A3 tranchés.**

### Vague 3 — État, transitions, permissions

`state_model.md` · `transition_policy.md` · `permission_policy.md` · `implementations/opencode/agent_permissions.md`

> Bloc à rédiger **ensemble** : les trois politiques se référencent mutuellement.
> **Conditions : A2, A8 (tranché), et clôture des vérifications du §11.**

### Vague 4 — Décisions et changements

`decision_policy.md` · `change_control.md` · `recovery_policy.md`

> **Condition : A1.**

### Vague 5 — Audit

`audit_policy.md` + contrôles de preuves + contrôles de permissions + règles de désaccord.

### Vague 6 — Prompts et modèles

4 bootstraps · modèles de rapports · décision · changement · réserve · reçu.

### Vague 7 — Consolidation

`getting_started.md` · liens croisés · `changelog.md` · vérification globale · rapport final de cohérence.

> `getting_started.md` est rédigé **en dernier** : c'est le manuel qui agrège et oriente. L'écrire plus tôt produirait le méga-prompt interdit par F1 §14.

---

## 10. Règles de non-duplication

| Information | Source unique |
|---|---|
| État opérationnel | `state.json` |
| Vue lisible de l'état | `state.md` (généré) |
| Mandat courant | `current_sprint.md` |
| Vocabulaire | `reference/terminology.md` |
| Règles communes | `protocol/governance_core.md` |
| Niveau de contrôle | `protocol/profile_*.md` |
| États et invariants | `protocol/state_model.md` |
| Transitions et reçus | `protocol/transition_policy.md` |
| Décisions et preuves | `protocol/decision_policy.md` |
| Changements | `protocol/change_control.md` |
| Audit | `protocol/audit_policy.md` |
| Permissions (règles) | `protocol/permission_policy.md` |
| Permissions (configuration) | `implementations/opencode/agent_permissions.md` |
| Incidents et reprise | `protocol/recovery_policy.md` |
| Rapports | `templates/*` |
| Navigation documentaire | `reference/document_map.md` |

Les autres documents **résument et référencent**, sans recopier.

---

## 11. Contrôle technique des permissions

### 11.1 Ce qui a été constaté (FAIT)

| Élément | Constat |
|---|---|
| `opencode.json` | Contient uniquement `$schema` et `instructions`. **Aucune permission globale.** |
| `.opencode/agents/builder.md` | Frontmatter `permissions:` — 22 règles : 15 `edit`, 1 `subagent`, 6 `shell` |
| Format | **Conforme au schéma OpenCode V2** : liste ordonnée de `{action, resource, effect}`, dernière règle gagnante |
| Ressources protégées en `edit` | `state.json`, `state.md`, `current_sprint.md`, `audit_report/**`, `debt_report/**`, `docs/**`, `sprints/**`, `templates/**`, `data/**`, `agents.md`, `contexte.md`, `getting_started.md`, `README.md`, `opencode.json`, `.opencode/**` |
| Shell bloqué | `git merge *`, `git push --force*`, `git push -f *`, `git checkout main*`, `git switch main*`, `git reset --hard*` |

### 11.2 Réserves (FAIT)

1. **Liste noire, pas liste blanche.** Aucune règle `{action:"*", resource:"*", effect:"deny"}` de base : tout ce qui n'est pas listé est autorisé. Une ressource oubliée est ouverte par défaut.
2. **Contournement par `shell`.** `edit` couvre « Edit, write, and patch tools ». Une écriture par redirection (`Set-Content state.json`, `> state.md`, `tee`) relève de `shell` et **n'est pas bloquée**. La protection de `state.json` est donc incomplète.
3. **Effectivité non démontrée.** Aucun rapport du pilote ne contient de test de refus. Une configuration présente n'est pas une restriction active.
4. **Asymétrie non vérifiée.** Les règles de BUILDER sont visibles ; celles d'ORCHESTRATOR et d'AUDITOR n'ont pas été confrontées à la matrice de `agents.md` §6.

### 11.3 Classification proposée

| Ressource / rôle | Classification | Justification |
|---|---|---|
| `state.json` (BUILDER) | `technical_enforced` **partiel** | Deny sur `edit` ; contournable par `shell` |
| `audit_report/**` (BUILDER) | `technical_enforced` **partiel** | Idem |
| `git merge` (BUILDER) | `technical_enforced` | Règle `shell` explicite |
| `state.json` (ORCHESTRATOR, AUDITOR) | `unknown` | Non vérifié |
| Secrets | `unknown` | Aucune règle constatée |

> `unknown` ne doit jamais être présenté comme une garantie (F3 §12).

### 11.4 Protocole de vérification à exécuter avant la vague 3

| # | Test | Résultat attendu | Résultat à consigner |
|---|---|---|---|
| T1 | Sous l'agent BUILDER, tenter une édition de `state.json` | Refus technique | Preuve de refus |
| T2 | Sous BUILDER, tenter `Set-Content state.json "{}"` | Refus ou succès | Si succès → faille confirmée |
| T3 | Sous ORCHESTRATOR, tenter une édition de `src/**` | Refus (moindre privilège) | Preuve |
| T4 | Sous AUDITOR, tenter une édition de `src/**` | Refus | Preuve |

Chaque test doit produire une **trace horodatée** versée dans `implementations/opencode/agent_permissions.md`. Sans trace, la classification reste `unknown`.

---

## 12. Risques documentaires

| Risque | Impact | Mesure |
|---|---|---|
| Rédiger sur des arbitrages non tranchés | Réécriture complète | Vagues conditionnées (§9) |
| Promouvoir le pilote en doctrine | Le cadre fige une implémentation | A6 + `pilot_mapping.md` |
| Recopier les politiques dans `getting_started.md` | Méga-prompt | Rédaction en vague 7 + contrôle de duplication |
| Surestimer les garanties techniques | Fausse sécurité | §11 + `limitations.md` |
| Divergence des trois profils | Incohérence | Écriture depuis `profile_standard` |
| Perte du mécanisme de reçu | Régression majeure | `transition_policy.md` dédié |

---

## 13. Prochaines étapes

1. **Validation de cette cartographie** par le VALIDATOR.
2. **Arbitrages A1 → A7** (A8 étant tranché).
3. **Exécution des tests T1 → T4** (§11.4), ou acceptation explicite du statut `unknown`.
4. **Lancement de la vague 1**, qui ne dépend d'aucun arbitrage restant.
5. Décision sur le sort des trois sources F1/F2/F3 : conservation à la racine, ou déplacement vers `documentation/_sources/` (nécessite une autorisation explicite).

---

## Annexe A — Journal de la cartographie

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale : inventaire, doublons, contradictions, cible, ordre en 7 vagues |
| 0.1 | 2026-11-20 | Intégration C8 (reçu = composant central), C10 (permissions vérifiables), A8 (socle agnostique + implémentation OpenCode), ajout de `transition_policy.md` et de `implementations/opencode/`, ajout du contrôle technique §11 |
