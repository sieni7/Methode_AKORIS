# Modèle — Rapport ORCHESTRATOR

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **LIVRABLE VAGUE 6 — à valider par le VALIDATOR** |
| Nature | Modèle générique — ne contient aucune décision de projet |
| Références | [Carte documentaire](../reference/document_map.md) §4.5 · [Socle](../protocol/governance_core.md) · [Décision](../protocol/decision_policy.md) |

> Toute valeur entre crochets est **à renseigner**. Ce modèle ne fournit aucune donnée réelle. Les statuts épistémiques sont définis dans le [socle](../protocol/governance_core.md) GC-18 ; les statuts de contrôle et de preuve dans la [politique de décision](../protocol/decision_policy.md) §5.

## 1. Identification

| Champ | Valeur |
|---|---|
| Type de rapport | [cadrage / analyse / suivi — à préciser] |
| Date | [AAAA-MM-JJ] |
| Auteur | ORCHESTRATOR |
| Sprint | [À renseigner] |
| Transition concernée | [`transition_id` ou « aucune »] |
| Version du mandat | [À renseigner] |
| Profil actif | [Lite / Standard / Reinforced — à renseigner] |

## 2. Cadrage

| Élément | Contenu |
|---|---|
| Objectif du cadrage | [À renseigner] |
| Périmètre proposé | [À renseigner] |
| Périmètre exclu | [À renseigner] |
| Checkpoint concerné | [CP1 / CP2 / CP3 / aucun] |
| Sources de référence | [À renseigner] |

## 3. État observé

| Objet | État | Source consultée | Statut épistémique |
|---|---|---|---|
| Projet | [à renseigner] | `state.json` → `project.status` | [`FAIT` / `INCONNU` / …] |
| Sprint | [à renseigner] | `state.json` → `sprint.current_status` | [à renseigner] |
| Transition | [à renseigner] | `state.json` → `transition.status` | [à renseigner] |
| Dernière décision | [à renseigner] | `state.json` → `last_decision` | [à renseigner] |

`state.json` est la source de vérité de l'état courant ; `state.md` en est une vue générée, jamais une source concurrente (A2).

## 4. Sources consultées

| Chemin | Section | Rôle dans l'analyse |
|---|---|---|
| [À renseigner] | [À renseigner] | [À renseigner] |

## 5. Faits vérifiés et inconnues

| # | Énoncé | Statut | Preuve ou référence |
|---|---|---|---|
| F1 | [À renseigner] | [`FAIT` / `HYPOTHÈSE` / `RECOMMANDATION` / `À ARBITRER` / `INCONNU`] | [À renseigner] |

Une hypothèse n'est jamais présentée comme un fait. Un contrôle non réalisé est `NOT_CHECKED`, jamais `PASS`.

## 6. Analyse

| Point | Observation | Conséquence possible |
|---|---|---|
| [À renseigner] | [À renseigner] | [À renseigner] |

Les recommandations ci-dessous sont des avis : elles ne deviennent des décisions que par acte du VALIDATOR tracé.

## 7. Changements, réserves et blocages

| Objet | Identifiant | État | Lien |
|---|---|---|---|
| Changement | [`CHG-AAAA-NNNN` / `URG-AAAA-NNNN` / aucun] | [À renseigner] | [change_request_template.md](change_request_template.md) |
| Réserve | [À renseigner] | [À renseigner] | [reserve_template.md](reserve_template.md) |
| Blocage | [À renseigner] | [À renseigner] | [recovery_policy.md](../protocol/recovery_policy.md) §3 |

## 8. Décision attendue du VALIDATOR

| Champ | Valeur |
|---|---|
| Question posée | [À renseigner] |
| Options examinées | [À renseigner] |
| Recommandation ORCHESTRATOR | [À renseigner — non décision] |
| Valeur proposée | [parmi `GO`, `GO_WITH_RESERVES`, `NO_GO`, `HOLD`, `CANCELLED` — voir DP §3] |
| Périmètre de la décision | [À renseigner] |
| Date attendue | [À renseigner] |
| Décision retenue | [À renseigner par le VALIDATOR — laisser vide tant qu'il n'a pas décidé] |

`HOLD` constate qu'une décision ne peut pas être prise ; il n'est pas un refus. Voir [DP](../protocol/decision_policy.md) §3 et §8.2.

## 9. Traçabilité

| Élément | Référence |
|---|---|
| Preuves classées | [À renseigner — statut selon DP §5.1] |
| Reçu de transition | [À renseigner — le cas échéant] |
| Divergence état/reçu | [aucune / décrite : à renseigner] |
| Contrôles non réalisés | [À renseigner — `NOT_CHECKED`] |
