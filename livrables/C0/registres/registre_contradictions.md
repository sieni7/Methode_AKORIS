# C0-06 — Registre des contradictions

**Tâche** : C0-06 — Identifier doublons, contradictions, divergences  
**Sous-tâche** : Contradictions (instructions opposées dans différents documents)  
**Date d'exécution** : 2026-11-24  
**Contrainte** : Signalement uniquement — aucune correction de document source

---

## 1. Méthode

Une contradiction est une instruction opposée ou incompatible entre deux ou plusieurs documents. Les contradictions ci-dessous sont issues principalement de `00_cartographie.md` §5 (C1 à C20, dont C8 et C10 révisées en §5.4).

---

## 2. Contradictions bloquantes (empêchent de rédiger)

| ID | Contradiction | Sources en conflit | Bloque | Statut / résolution documentaire |
|---|---|---|---|---|
| C1 | Valeurs de décision : 3 ou 5 ? `GO / NO GO / GO WITH RESERVES` **vs** `GO / GO_WITH_RESERVES / NO_GO / HOLD / CANCELLED` | `getting_started.md` 5.5 + pilote **vs** `AKORIS_consolide.md` §8.1 | `decision_policy.md` | Tranché par A1 (5 valeurs, underscore) — `decision_policy.md` §3 |
| C2 | Orthographe canonique des identifiants : espaces vs underscore (`GO WITH RESERVES` / `GO_WITH_RESERVES`) | `getting_started.md` **vs** `AKORIS_consolide.md` | `decision_policy.md`, modèles | Tranché par A1 (underscore) |
| C3 | Deux schémas `state.json` incompatibles : v1.0 plat (`current_agent`, `protocol_version`, `human_validation_required`, `authorization.token`) vs v2.0 imbriqué (`protocol`, `agent`, `governance`, `checkpoints`, `blockers`, `reserves`, `change_control`, `permission_violations`) | `AKORIS_consolide.md` §7 **vs** `getting_started.md` 06.5 + `state.json` | `state_model.md` | Tranché par A2 (v2.0 normative) — `state_model.md` §6.1 |
| C4 | Profils absents de l'opérationnel : F3 en fait le cœur du cadre ; `getting_started` et le pilote n'en ont aucune trace | `AKORIS_consolide.md` §4 **vs** pilote | `profile_*.md`, `governance_core.md` | Tranché par A3 (profils activés) |
| C5 | Trois chemins racine pour le socle : `governance/` (F3, 4 fichiers) · `protocol/` racine projet (F2, 11 fichiers) · `documentation/protocol/` (F1) | F3 · F2 · F1 | `document_map.md` | À ARBITRER (A4) — pas encore tranché de manière définitive sur le chemin racine |

---

## 3. Contradictions majeures (déforment le sens)

| ID | Contradiction | Détail | Statut |
|---|---|---|---|
| C6 | Collision `README.md` | F2 §6.1 = README projet (installation) ; F1 §6 = README documentation | À ARBITRER (A4) — `documentation/README.md` tranché |
| C7 | Cycle de transition : 9 ou 5 états ? | F3 : `draft, awaiting_human_go, authorized, consumed, in_progress, completed, rejected, expired, cancelled` · `getting_started` 06.8 : sans `draft`, `consumed`, `expired`, `rejected` | À ARBITRER (A2) — v2.0 retient 9 états |
| C8 | Preuve de consommation d'une autorisation | F3 sépare autorisation / consommation / exécution mais ne décrit aucun mécanisme. `getting_started` 06.9 + `agents.md` §7 imposent un **reçu de transition**. | **RÉVISÉ** — voir §5.4 de la cartographie : le reçu est un composant central (`transition_policy.md`) |
| C9 | Cadre générique ou lié à l'outil | `getting_started` structuré autour des « trois onglets OpenCode » ; F3 agnostique ; F2 parle d'« onglet A/B/C » | **TRANCHÉ** (A8) — socle agnostique, OpenCode implémentation de référence |
| C10 | Niveau réel des permissions | F3 §12 : « dans un environnement partagé, les permissions sont principalement procédurales sauf preuve technique contraire ». Le pilote contient une preuve technique **partielle** (frontmatter OpenCode). | **RÉVISÉ** — voir §5.4 : `permission_policy.md` doit porter une procédure de vérification effective |
| C11 | Liste des rôles : 3 ou 4 ? | F3, F2, `getting_started` = 3 agents + VALIDATOR ; `akoris_documentation_builder.md` ajoute DOCUMENTATION BUILDER | À ARBITRER (A5) — tranché : 4 rôles, le 4e documentaire hors boucle |

---

## 4. Contradictions mineures

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
| C20 | Maquette fournie en Vague 0 incomplète : l'arborescence de la consigne omet `protocol/profile_*.md`, `templates/` et `reference/`, alors que les vagues 2 et 6 les rédigent. Corrigé en §8.1 de la cartographie ; à confirmer |

---

## 5. Contradictions supplémentaires identifiées lors de C0

| ID | Contradiction | Sources en conflit | Observation |
|---|---|---|---|
| C21 | Statut du document `00_cartographie.md` : en-tête dit « PROPOSITION — à valider par le VALIDATOR » (v0.1) ; `document_map.md` §3 le qualifie de « TRAVAIL » (vague 0) | `00_cartographie.md` en-tête ; `document_map.md` §3 | Statut documentaire en double lecture |
| C22 | Version de `document_map.md` : en-tête fixé à `Version 0.4` par décision explicite (I4) ; le changelog indique 0.4 à la clôture vague 5, puis des notes de maintenance indiquent 27/34, 31/34, 34/34 sans réécriture de l'en-tête | `changelog.md` §3.1 (I4) ; `changelog.md` notes de maintenance vague 6 et 7 ; `document_map.md` en-tête | L'en-tête n'est pas mis à jour malgré l'évolution du compteur |
| C23 | Décompte des 34 documents : `README.md` §10 dit « 34 documents cibles produits » ; `document_map.md` §2 dit « 34 documents produits sur 34 » ; `00_cartographie.md` §2 dit « 0 sur 34 existe » (photographie historique) | `README.md` §10 ; `document_map.md` §2 ; `00_cartographie.md` §2 | Divergence entre photographie historique et état actuel |
| C24 | `state.json` du dépôt (v2.0) vs structure v1.0 du pilote : le fichier `state.json` présent dans le dépôt suit la structure v2.0 imbriquée, mais le pilote utilise encore v1.0 plat | `state.json` (dépôt) ; `state_model.md` §6.1 ; `AKORIS_consolide.md` §7 | Écart documenté (A2) mais pas de procédure de migration |
| C25 | Champ `profile` dans `state.json` : l'état enregistre le profil actif (`standard`) mais pas sa version ; `versioning_policy.md` §2 précise que la version du profil est portée par l'en-tête du document `profile_*.md` | `state.json` ; `versioning_policy.md` §2 (décision A10) ; `state_model.md` §6.4 | Relation état/version de profil non modélisée (`À ARBITRER`) |

---
*Fin du registre des contradictions. Signalement uniquement — aucune correction apportée. Total : 25 contradictions identifiées (C1 à C25, dont C8 et C10 révisées).*