# Modèle — Rapport BUILDER

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **LIVRABLE VAGUE 6 — à valider par le VALIDATOR** |
| Nature | Modèle générique — ne contient aucune décision de projet |
| Références | [Carte documentaire](../reference/document_map.md) §4.5 · [Audit](../protocol/audit_policy.md) §17 · [Transitions](../protocol/transition_policy.md) |

> Toute valeur entre crochets est **à renseigner**. Ce modèle ne fournit aucune donnée réelle. Une affirmation d'agent n'est pas une preuve : voir [socle](../protocol/governance_core.md) GC-22.

## 1. Mandat et transition

| Champ | Valeur |
|---|---|
| Sprint | [À renseigner] |
| `mandate_version` | [À renseigner] |
| `transition_id` | [À renseigner] |
| Statut de la transition | [À renseigner] |
| `authorized_at` / `authorized_by` | [À renseigner] |
| `decision_id` | [À renseigner] |
| Reçu déposé | [emplacement — `sprint_report/` — et date] |
| `expires_at` | [À renseigner si le mandat l'exige ; sinon « non requis »] |

## 2. Périmètre

| Élément | Contenu |
|---|---|
| Périmètre autorisé | [À renseigner] |
| Périmètre exclu | [À renseigner] |
| Modifications hors périmètre | [aucune / à décrire] |
| Changement déclaré | [`CHG-AAAA-NNNN` / `URG-AAAA-NNNN` / aucun] |

## 3. Tâches réalisées et non réalisées

| # | Tâche du mandat | État | Preuve |
|---|---|---|---|
| 1 | [À renseigner] | [réalisée / non réalisée / partielle] | [référence] |

Une tâche partielle est déclarée avec sa part non couverte ; elle n'est pas comptée comme réalisée.

## 4. Fichiers modifiés

| Chemin | Nature de la modification | Lien avec le mandat |
|---|---|---|
| [À renseigner] | [création / modification / suppression] | [À renseigner] |

## 5. Commits

| Identifiant | Branche | Date | Description |
|---|---|---|---|
| [À renseigner] | [branche dédiée] | [À renseigner] | [À renseigner] |

Un commit absent, réécrit ou non traçable est une rupture de traçabilité : le signaler.

## 6. Tests et résultats

| # | Test | Commande | Date | Résultat | Sortie conservée |
|---|---|---|---|---|---|
| 1 | [À renseigner] | [À renseigner] | [À renseigner] | [`PASS` / `FAIL` / `PARTIAL` / `N/A` / `NOT_CHECKED`] | [référence] |

`NOT_CHECKED` ne vaut jamais `PASS`. Un test non exécuté n'est pas présenté comme réussi. Les statuts sont définis dans [DP](../protocol/decision_policy.md) §5.2.

## 7. Preuves

| Preuve | Statut | Critère concerné | Référence |
|---|---|---|---|
| [À renseigner] | [`directly_verified` / `reproduced` / `cross_checked` / `declared_only` / `partial` / `missing` / `invalid`] | [À renseigner] | [À renseigner] |

Une preuve `declared_only` ne valide jamais un critère critique. Voir [DP](../protocol/decision_policy.md) §5.1.

## 8. Anomalies et écarts

| # | Objet | Gravité | Description | Traitement proposé |
|---|---|---|---|---|
| 1 | [À renseigner] | [S0 / S1 / S2 / S3] | [À renseigner] | [À renseigner] |

La qualification précède la décision. Voir [DP](../protocol/decision_policy.md) §4.

## 9. Réserves et blocages

| Objet | Identifiant | Description | Lien |
|---|---|---|---|
| Réserve | [À renseigner] | [À renseigner] | [reserve_template.md](reserve_template.md) |
| Blocage | [À renseigner] | [À renseigner] | [recovery_policy.md](../protocol/recovery_policy.md) §3 |

## 10. Conclusion et transmission

| Champ | Valeur |
|---|---|
| Résultat produit | [À renseigner] |
| Limites déclarées | [À renseigner] |
| Éléments non vérifiés | [À renseigner] |
| Transmission à | [ORCHESTRATOR / AUDITOR — à préciser] |
| Décision attendue | [À renseigner — le VALIDATOR décide seul] |

Ce rapport est une source d'information pour l'audit ; il ne modifie ni `state.json` ni le mandat et ne s'auto-accepte pas.
