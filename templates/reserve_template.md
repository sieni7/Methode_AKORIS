# Modèle — Réserve

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **LIVRABLE VAGUE 6 — à valider par le VALIDATOR** |
| Nature | Modèle générique — ne contient aucune décision de projet |
| Références | [Politique de décision](../protocol/decision_policy.md) §7.2 · [Terminologie](../reference/terminology.md) §4 |

> Toute valeur entre crochets est **à renseigner**. Une réserve sans responsable ni échéance n'est pas une réserve : c'est une intention.

## 1. Identification

| # | Attribut obligatoire | Valeur |
|---|---|---|
| 1 | Identifiant | [unique, stable — à renseigner] |
| 2 | Description | [ce qui n'est pas conforme — à renseigner] |
| 3 | Gravité | [`S2` / `S3` — à renseigner et justifier] |
| 4 | Impact | [conséquence si la réserve n'est pas traitée] |
| 5 | Responsable | [acteur affecté — à renseigner] |
| 6 | Tâche de résolution | [action attendue — à renseigner] |
| 7 | Sprint de résolution | [À renseigner] |
| 8 | Échéance | [AAAA-MM-JJ] |
| 9 | Méthode de vérification | [comment la clôture sera prouvée] |
| 10 | Décision humaine | [acte d'acceptation de la réserve — VALIDATOR, date] |

Les dix attributs ci-dessus sont définis dans [DP](../protocol/decision_policy.md) §7.2.

## 2. Preuves et traçabilité

| Élément | Valeur |
|---|---|
| Références de preuve | [à renseigner — statut selon DP §5.1] |
| Preuve critique concernée | [oui / non — à préciser] |
| Transition associée | [`transition_id` ou « aucune »] |
| Décision d'origine | [référence — voir decision_template.md](decision_template.md) |
| Changement associé | [le cas échéant — voir change_request_template.md](change_request_template.md) |
| Rapport d'audit | [référence — voir auditor_report_template.md](auditor_report_template.md) |

## 3. Limites d'admissibilité

Une réserve ne peut couvrir ni une anomalie S0 ou S1, ni un changement de périmètre, ni une preuve manquante sur un critère critique, ni une violation de permission P0 ou P1. Voir [DP](../protocol/decision_policy.md) §7.1 et §10.

Le niveau de risque qualitatif est apprécié par le VALIDATOR et justifié ; aucune échelle chiffrée n'est définie (C25).

## 4. Suivi et clôture

| Champ | Valeur |
|---|---|
| État de la réserve | [ouverte / en cours de résolution / prête à clore / close — à renseigner] |
| Date de clôture | [À renseigner] |
| Preuve de clôture | [résultat de la méthode de vérification] |
| Validation de la clôture | [VALIDATOR — date] |
| Trace conservée dans | [debt_report/ — projet gouverné] |

La clôture est une décision humaine tracée : elle n'est pas déduite de la simple expiration de l'échéance.
