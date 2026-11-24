# Modèle — Décision du VALIDATOR

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **LIVRABLE VAGUE 6 — à valider par le VALIDATOR** |
| Nature | Modèle générique — la décision appartient au VALIDATOR |
| Références | [Politique de décision](../protocol/decision_policy.md) §3, §11 · [Terminologie](../reference/terminology.md) §4 |

> Toute valeur entre crochets est **à renseigner**. Une recommandation d'agent n'est pas une décision : le champ « Décision du VALIDATOR » reste vide tant que l'acte humain n'a pas eu lieu.

## 1. Identification

| Champ | Valeur |
|---|---|
| Identifiant de décision | [À renseigner] |
| Objet | [checkpoint / sprint / changement / réserve / fusion / déploiement / clôture] |
| Référence de l'objet | [À renseigner] |
| Date d'instruction | [AAAA-MM-JJ] |
| Auteur de la proposition | [ORCHESTRATOR / AUDITOR — à préciser] |

## 2. Contexte et question

| Champ | Valeur |
|---|---|
| Contexte | [À renseigner] |
| Question posée | [À renseigner] |
| Critères applicables | [références aux documents sources] |
| Transition associée | [`transition_id` ou « aucune »] |

## 3. Options et impacts

| Option | Description | Impacts | Réversibilité | Documents affectés |
|---|---|---|---|---|
| A | [À renseigner] | [À renseigner] | [R0 / R1 / R2 / R3] | [À renseigner] |
| B | [À renseigner] | [À renseigner] | [À renseigner] | [À renseigner] |

Les niveaux R0 à R3 sont définis dans [change_control.md](../protocol/change_control.md) §5.1. Aucune échelle de risque chiffrée n'est définie (C25) : le niveau qualitatif est apprécié par le VALIDATOR et justifié.

## 4. Éléments de preuve

| # | Preuve | Statut | Référence |
|---|---|---|---|
| 1 | [À renseigner] | [`directly_verified` / `reproduced` / `cross_checked` / `declared_only` / `partial` / `missing` / `invalid`] | [À renseigner] |

Une décision fondée exige une preuve acceptable pour chaque critère obligatoire ; un critère critique couvert par `declared_only` impose `HOLD`.

## 5. Recommandation éventuelle

| Champ | Valeur |
|---|---|
| Recommandation | [À renseigner — avis uniquement] |
| Auteur | [ORCHESTRATOR / AUDITOR] |
| Motif | [À renseigner] |
| Valeur envisagée | [parmi `GO`, `GO_WITH_RESERVES`, `NO_GO`, `HOLD`, `CANCELLED`] |

## 6. Décision du VALIDATOR

| Champ | Valeur |
|---|---|
| Valeur retenue | [`GO` / `GO_WITH_RESERVES` / `NO_GO` / `HOLD` / `CANCELLED` — à compléter par le VALIDATOR] |
| Auteur | VALIDATOR |
| Date et heure | [À renseigner] |
| Motif | [À renseigner] |
| Périmètre de la décision | [À renseigner] |
| Réserves associées | [le cas échéant — voir reserve_template.md](reserve_template.md) |
| Effet attendu | [état résultant — à renseigner] |
| Preuves citées | [références] |
| Références | [documents, sections] |

`HOLD` signifie que la décision ne peut pas être prise ; il n'est pas un refus et n'est pas convertissable par lassitude. `CANCELLED` met fin à l'objet et n'est pas un `NO_GO`. Voir [DP](../protocol/decision_policy.md) §3 et §8.

## 7. Suite

| Champ | Valeur |
|---|---|
| Changement à instruire | [le cas échéant — voir change_request_template.md](change_request_template.md) |
| Nouvelle transition requise | [oui / non — à préciser] |
| Décision distincte nécessaire | [fusion / déploiement / sprint suivant / aucune] |
| Trace conservée dans | [À renseigner] |

Aucune décision n'en implique une autre par défaut : l'acceptation d'un sprint n'autorise ni fusion, ni déploiement, ni sprint suivant.
