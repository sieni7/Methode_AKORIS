# Modèle — Demande de changement

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **LIVRABLE VAGUE 6 — à valider par le VALIDATOR** |
| Nature | Modèle générique — ne contient aucune décision de projet |
| Références | [Contrôle des changements](../protocol/change_control.md) §3, §5, §10 · [Terminologie](../reference/terminology.md) §5 |

> Toute valeur entre crochets est **à renseigner**. Ce modèle ne fournit aucune donnée réelle. Un changement approuvé n'autorise pas l'exécution : celle-ci exige un mandat et une transition.

## 1. Identification

| Champ | Valeur |
|---|---|
| Identifiant | [`CHG-AAAA-NNNN` / `URG-AAAA-NNNN` — à renseigner] |
| Type | [changement planifié / urgence] |
| Date d'ouverture | [AAAA-MM-JJ] |
| Demandeur | [À renseigner] |
| État du cycle | [proposed / under_analysis / awaiting_decision / approved / rejected / deferred / implemented / verified / closed / cancelled] |
| Classe | [éditorial / mineur / majeur / critique — appréciation à justifier] |
| Réversibilité | [R0 / R1 / R2 / R3] |

Les identifiants sont uniques et jamais réutilisés, y compris pour un changement abandonné. Voir [CC](../protocol/change_control.md) §3.

## 2. Origine et description

| Champ | Valeur |
|---|---|
| Origine de la demande | [qui demande, et pourquoi] |
| Description du changement | [À renseigner] |
| Élément affecté | [périmètre / exigence / règle métier / architecture / donnée / sécurité / mandat / sprint / décision validée / profil] |
| Justification | [À renseigner] |
| Niveau de risque qualitatif | [faible / modéré / élevé / critique — appréciation humaine, aucune échelle chiffrée (C25)] |
| Justification du niveau | [À renseigner] |

## 3. Analyse d'impact — huit dimensions

| # | Dimension | Analyse | N/A justifiée ? |
|---|---|---|---|
| 1 | Métier | [À renseigner] | [oui / non] |
| 2 | Fonctionnel | [À renseigner] | [oui / non] |
| 3 | Technique | [À renseigner] | [oui / non] |
| 4 | Sécurité | [À renseigner] | [oui / non] |
| 5 | Données | [À renseigner] | [oui / non] |
| 6 | Planning | [À renseigner] | [oui / non] |
| 7 | Tests | [À renseigner] | [oui / non] |
| 8 | Réversibilité | [À renseigner] | [oui / non] |

Une dimension non renseignée est déclarée `N/A` avec justification, jamais laissée vide. Voir [CC](../protocol/change_control.md) §5.

## 4. Options examinées

| Option | Description | Avantages | Inconvénients | Réversibilité |
|---|---|---|---|---|
| A | [À renseigner] | [À renseigner] | [À renseigner] | [R0–R3] |
| B | [À renseigner] | [À renseigner] | [À renseigner] | [R0–R3] |

## 5. Documents et mandats affectés

| Document ou objet | Effet attendu | Nouvelle version |
|---|---|---|
| [À renseigner] | [À renseigner] | [À renseigner] |
| `current_sprint.md` | [À renseigner] | [À renseigner] |
| `state.json` | [À renseigner] | [À renseigner] |

Si le périmètre, le sprint, l'action, l'architecture, les critères, le profil ou la version du mandat changent : ancienne autorisation invalidée, nouveau mandat, nouvelle transition, nouveau `GO`. Voir [CC](../protocol/change_control.md) §6 et [TP](../protocol/transition_policy.md) §8.

## 6. Décision

| Champ | Valeur |
|---|---|
| Décision proposée | [parmi `GO`, `GO_WITH_RESERVES`, `NO_GO`, `HOLD`, `CANCELLED` — avis, non décision] |
| Décision du VALIDATOR | [à compléter par le VALIDATOR] |
| Auteur | VALIDATOR |
| Date | [À renseigner] |
| Motif | [À renseigner] |
| Effet sur le mandat | [À renseigner] |

`HOLD` suspend la décision et laisse le changement en `awaiting_decision` avec `decision = HOLD` (C31). Voir [DP](../protocol/decision_policy.md) §3.

## 7. Mise en œuvre et vérification

| Champ | Valeur |
|---|---|
| Responsable de la mise en œuvre | [À renseigner] |
| Nouveau `mandate_version` | [À renseigner] |
| Nouveau `transition_id` | [À renseigner] |
| Mise en œuvre livrée | [date et référence] |
| Vérification de l'effet réel | [méthode et preuve] |
| Auditeur de vérification | [À renseigner] |
| Clôture tracée | [date et référence] |

Emplacement du registre : `docs/governance/changes/` (projet gouverné). Le registre n'existe pas encore dans le périmètre documentaire.
