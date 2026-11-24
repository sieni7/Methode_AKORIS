# Modèle — Rapport AUDITOR

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **LIVRABLE VAGUE 6 — à valider par le VALIDATOR** |
| Nature | Modèle générique — recommandation, jamais décision |
| Références | [Politique d'audit](../protocol/audit_policy.md) §17 · [Décision](../protocol/decision_policy.md) §5 · [Décision C19](../reference/terminology.md) §4 |

> Toute valeur entre crochets est **à renseigner**. Ce modèle ne fournit aucune donnée réelle. Le rapport est un livrable d'AUDITOR : il ne modifie ni `state.json`, ni le mandat, ni les décisions validées.

## 1. Identification et type de contrôle

| Champ | Valeur |
|---|---|
| Type de contrôle | [`readiness_review` / `sprint_audit` — à choisir] |
| Objet du contrôle | [aptitude à démarrer / résultat livré — à préciser] |
| Date | [AAAA-MM-JJ] |
| Auteur | AUDITOR |
| Sprint | [À renseigner] |
| Emplacement du rapport | [`docs/governance/readiness/` / `audit_report/` — selon le type] |
| Transition concernée | [`transition_id` — à renseigner] |
| Reçu | [À renseigner — `audit_report/` pour AUDITOR] |

`readiness_review` et `sprint_audit` sont deux contrôles distincts et non substituables (C19). Le terme « audit » seul est ambigu dans un document normatif.

## 2. Mandat et périmètre audité

| Champ | Valeur |
|---|---|
| `mandate_version` | [À renseigner] |
| Périmètre audité | [À renseigner] |
| Périmètre exclu | [À renseigner] |
| Checkpoint concerné | [CP1 / CP2 / CP3 / aucun] |
| Profil actif | [Lite / Standard / Reinforced] |

## 3. Méthode

| # | Étape | État | Référence |
|---|---|---|---|
| 1 | Transition vérifiée | [À renseigner] | [TP §5.4] |
| 2 | Mandat lu | [À renseigner] | [À renseigner] |
| 3 | Exigences et critères lus | [À renseigner] | [À renseigner] |
| 4 | Dépôt inspecté directement | [À renseigner] | [À renseigner] |
| 5 | Commits examinés | [À renseigner] | [À renseigner] |
| 6 | Tests reproduits | [À renseigner] | [À renseigner] |
| 7 | Cas limites et négatifs | [À renseigner] | [À renseigner] |
| 8 | Modifications hors périmètre | [À renseigner] | [À renseigner] |
| 9 | Preuves classées | [À renseigner] | [DP §5.1] |
| 10 | Rapport produit | [À renseigner] | [le présent document] |

Séquence complète : [audit_policy.md](../protocol/audit_policy.md) §6.1.

## 4. Fichiers et commits examinés

| Chemin ou identifiant | Nature de l'examen | Observation |
|---|---|---|
| [À renseigner] | [lecture / comparaison / reproduction] | [À renseigner] |

## 5. Critères et tâches vérifiés

| # | Critère ou tâche | Statut de contrôle | Preuve associée |
|---|---|---|---|
| 1 | [À renseigner] | [`PASS` / `FAIL` / `PARTIAL` / `N/A` / `NOT_CHECKED`] | [référence] |

`N/A` exige une justification. `NOT_CHECKED` ne vaut jamais `PASS`.

## 6. Tests reproduits

| # | Test | Commande exacte | Date | Environnement | Sortie conservée | Résultat |
|---|---|---|---|---|---|---|
| 1 | [À renseigner] | [À renseigner] | [À renseigner] | [différences déclarées] | [référence] | [statut] |

Un test non exécuté n'est jamais `PASS` ; une sortie non conservée n'est pas une preuve reproductible.

## 7. Preuves et statut

| # | Preuve | Statut | Critère concerné | Référence |
|---|---|---|---|---|
| 1 | [À renseigner] | [`directly_verified` / `reproduced` / `cross_checked` / `declared_only` / `partial` / `missing` / `invalid`] | [À renseigner] | [À renseigner] |

Une preuve `declared_only` ne valide pas un critère critique ; une preuve `missing` ou `invalid` interdit le `PASS`.

## 8. Écarts et anomalies qualifiées

| # | Objet | Gravité | Violation éventuelle | Observation |
|---|---|---|---|---|
| 1 | [À renseigner] | [S0 / S1 / S2 / S3] | [P0 / P1 / P2 / P3 / aucune] | [À renseigner] |

Toute anomalie est qualifiée avant décision ; S0 et S1 ne peuvent pas être couvertes par une réserve.

## 9. Éléments non vérifiés et limites

| Élément | Motif | Effet sur la conclusion |
|---|---|---|
| [À renseigner] | [À renseigner] | [À renseigner] |

Limites permanentes à rappeler si pertinent : permissions `unknown`, protection de `main` `unknown`, T1 à T5 `NON EXÉCUTÉS`. Une configuration déclarée n'est pas une restriction éprouvée.

## 10. Comparaison avec le rapport BUILDER

| Affirmation BUILDER | Conclusion AUDITOR | Preuve |
|---|---|---|
| [À renseigner] | [confirmée / partiellement confirmée / non confirmée / contredite] | [référence] |

Les désaccords sont conservés dans les deux rapports ; aucune version n'est corrigée pour les faire disparaître.

## 11. Recommandation

| Champ | Valeur |
|---|---|
| Recommandation AUDITOR | [À renseigner — avis, non décision] |
| Valeur envisageable | [parmi `GO`, `GO_WITH_RESERVES`, `NO_GO`, `HOLD`, `CANCELLED` — DP §3] |
| Réserves proposées | [le cas échéant — voir reserve_template.md](reserve_template.md) |
| Décision du VALIDATOR | [À laisser vide — seul le VALIDATOR décide] |
| Éléments à arbitrer | [À renseigner] |

Structure normative : [audit_policy.md](../protocol/audit_policy.md) §17.1. Un `HOLD` laisse le changement concerné en `awaiting_decision` avec `decision = HOLD` (C31).
