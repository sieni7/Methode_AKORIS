# C0-06 — Registre des doublons

**Tâche** : C0-06 — Identifier doublons, contradictions, divergences  
**Sous-tâche** : Doublons (contenu identique ou très proche sous noms différents, sans source principale désignée)  
**Date d'exécution** : 2026-11-24  
**Contrainte** : Signalement uniquement — aucune correction de document source

---

## 1. Méthode

Un doublon est une information présente dans plusieurs documents **sans source principale désignée**. Les doublons ci-dessous sont issus principalement de `00_cartographie.md` §4 (D1 à D15) et complétés par l'examen direct du corpus.

---

## 2. Registre des doublons

| ID | Information dupliquée | Documents impliqués | Source principale désignée | Nature du doublon | Gravité estimée |
|---|---|---|---|---|---|
| D1 | Objet, acronyme, définition d'AKORIS | `AKORIS_consolide.md` §1 · `AKORIS_architecture_documentaire.md` §1 · `getting_started.md` §0 | `README.md` + `terminology.md` | Définition cadre | Moyenne |
| D2 | Rôles et responsabilités | `AKORIS_consolide.md` §3 · `AKORIS_architecture_documentaire.md` §6.3/§13 · `getting_started.md` Bloc 05 · `agents.md` (pilote) | `governance_core.md` | Rôles ORCHESTRATOR/BUILDER/AUDITOR/VALIDATOR | Élevée |
| D3 | Sources de référence uniques | `AKORIS_consolide.md` §5.1 · `AKORIS_architecture_documentaire.md` §9 · `getting_started.md` 06.4 | `reference/document_map.md` | Sources uniques par information | Élevée |
| D4 | États projet/sprint/transition | `AKORIS_consolide.md` §6 · `AKORIS_architecture_documentaire.md` §4.6 · `getting_started.md` 06.6-06.8 · `state.json` | `state_model.md` + `transition_policy.md` | États et invariants | Élevée |
| D5 | Schéma `state.json` | `AKORIS_consolide.md` §7 · `getting_started.md` 06.5 · `state.json` réel | `state_model.md` + `state.schema.json` | Structure d'état | Élevée |
| D6 | Arborescence projet | `AKORIS_consolide.md` §17 · `AKORIS_architecture_documentaire.md` §3 · `getting_started.md` 06.3 · pilote | `document_map.md` | Arborescence fichiers | Moyenne |
| D7 | Checkpoints CP1/CP2/CP3 | `AKORIS_consolide.md` §14 · `AKORIS_architecture_documentaire.md` §14 · `getting_started.md` 01.5/04.7/08 | `getting_started.md` | Checkpoints | Moyenne |
| D8 | Cycle nominal de sprint | `AKORIS_consolide.md` §15 · `AKORIS_architecture_documentaire.md` §14 · `getting_started.md` §5 | `getting_started.md` | Cycle de sprint | Moyenne |
| D9 | Règles Git / fusion `main` | `AKORIS_consolide.md` §16 · `AKORIS_architecture_documentaire.md` §4.10 · `getting_started.md` 06.13 | `permission_policy.md` | Règles Git | Moyenne |
| D10 | Valeurs et conditions de décision | `AKORIS_consolide.md` §8 · `AKORIS_architecture_documentaire.md` §4.7 · `getting_started.md` 5.5 | `decision_policy.md` | Valeurs de décision | Élevée |
| D11 | Contenu des rapports | `AKORIS_consolide.md` §11.2 · `AKORIS_architecture_documentaire.md` §15 · `getting_started.md` 05.7 · `templates/` | `templates/*` | Modèles de rapports | Moyenne |
| D12 | Ordre d'implémentation | `AKORIS_architecture_documentaire.md` §11 · `akoris_documentation_builder.md` §8 | Cette cartographie (C0) | Ordre de rédaction | Faible |
| D13 | Architecture cible | `AKORIS_architecture_documentaire.md` §3 · `akoris_documentation_builder.md` §6 | Cette cartographie (C0) | Architecture cible | Faible |
| D14 | Permissions | `AKORIS_consolide.md` §12-13 · `AKORIS_architecture_documentaire.md` §4.10 · `getting_started.md` 05.6 · `agents.md` §6 (pilote) · frontmatter `.opencode/agents/` | `permission_policy.md` + `implementations/opencode/agent_permissions.md` | Matrice de permissions | Très élevée |
| D15 | Reçu de transition | `getting_started.md` 06.9 · `agents.md` §7 (pilote) · `AKORIS_consolide.md` §6.4 (`receipt_reference`) | `transition_policy.md` | Mécanisme de reçu | Élevée |

---

## 3. Doublons supplémentaires identifiés lors de C0

| ID | Information dupliquée | Documents impliqués | Observation |
|---|---|---|---|
| D16 | Règle de non-duplication (« Une information, un fichier ») | `README.md` §8 (règle 1) · `00_cartographie.md` §10 · `governance_core.md` GC-50/GC-51 · `akoris_documentation_builder.md` §10 | Même règle énoncée dans 4 documents |
| D17 | Séparation `state.json` / `state.md` (source vs vue générée) | `AKORIS_consolide.md` §7 · `AKORIS_architecture_documentaire.md` §6.4/§6.5 · `governance_core.md` (implicit via GC) · `state_model.md` §1 · `terminology.md` §8 | Même distinction dans 5 documents |
| D18 | Cinq valeurs de décision (GO, GO_WITH_RESERVES, NO_GO, HOLD, CANCELLED) | `AKORIS_consolide.md` §8.1 · `decision_policy.md` §3 · `state_model.md` (via $defs) · `state.schema.json` ($defs decisionValue) · `terminology.md` §4 | Même énumération dans 5 documents |
| D19 | Règle GC-13 / GC-14 (BUILDER ne modifie pas state.json, state.md, rapport d'audit, décision validée ; ne fusionne pas main) | `governance_core.md` GC-13/GC-14 · `AKORIS_consolide.md` §3.2 · `mandat_builder.md` §3 · `prompts/akoris_builder_bootstrap.md` §4 | Même contrainte dans 4 documents |
| D20 | Autorité finale du VALIDATOR | `AKORIS_consolide.md` §2 (principe 15) · §3.4 · `governance_core.md` GC-04 · `decision_policy.md` §1 · `terminology.md` §2 | Même principe dans 5 documents |

---

## 4. Doublons les plus coûteux

Les doublons D2, D3, D5, D14 sont identifiés dans `00_cartographie.md` §4 comme les plus coûteux : toute évolution y crée immédiatement une divergence. Ajout : D10 (valeurs de décision) et D18 (énumération des 5 valeurs) sont également à fort risque de divergence.

---
*Fin du registre des doublons. Signalement uniquement — aucune correction apportée. Total : 20 doublons identifiés (D1 à D20).*