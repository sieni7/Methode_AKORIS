# Mandat d'Audit Indépendant C0 — AKORIS

**Transition** : TR-2026-0001  
**Mandat** : C0-revise-v1  
**Destinataire** : AUDITOR DOCUMENTAIRE  
**Émetteur** : ORCHESTRATOR  
**Date** : 2026-11-24  
**Ordre VALIDATOR** : Décision GO_WITH_RESERVES (HVG0), référence TR-2026-0001  

## 1. Objet de l'audit

L'audit indépendant porte sur l'intégralité de la livraison du chantier C0 — Inventaire et état de référence du corpus AKORIS — telle que produite par le BUILDER DOCUMENTAIRE sur la branche `dev_C0`.

L'audit vise à vérifier la conformité, l'intégrité et la traçabilité de la production C0, conformément au mandat C0-revise-v1 et au plan de consolidation AKORIS (plan_de_consolidation.md v0.1.0-draft).

**Non-valeur de cette décision** : cet ordre n'est ni une acceptation de C0, ni une autorisation de fusion vers `main`, ni une autorisation de démarrage de C1. Ces décisions demeureront distinctes et subséreront à la décision HVG0-B du VALIDATOR humain.

## 2. Étendue et contrôles requis

L'AUDITOR devra examiner les 12 domaines suivants, produire un contrôle pour chacun et noter le résultat selon les statuts `PASS`, `FAIL` ou `NOT_CHECKED` (toujours, `NOT_CHECKED` ne vaut jamais `PASS`):

| # | Domaine de contrôle | Critère clé |
|---|---|---|
| **C0-1** | **Conformité au mandat** | Couverture effective des 12 tâches C0-01 à C0-12 ; présence de tous les livrables attendus (11 livrables C0 + réception de transition) |
| **C0-2** | **Intégrité Git** | Branche `dev_C0` depuis commit initial `f3b2eb7` ; 10 commits annoncés traçables à leurs identifiants tâches ; push distant état ; état actuel du dépôt |
| **C0-3** | **Lecture seule** | Absence de modification des documents sources entre `main` et `dev_C0` ; méthode de comparaison explicite et preuves |
| **C0-4** | **Inventaire** | Cohérence des 45 fichiers annoncés (39 suivis + 6 non suivis) ; traçabilité du périmètre inventorié ; classement par catégorie |
| **C0-5** | **Métadonnées et classification** | Cohérence, exhaustivité ; justification des catégories principales/secondielles ; traitement des `inconnu`/`non indiqué`/`non vérifiable`/`sans objet` |
| **C0-6** | **Décisions** | Vérification individuelle des 26 décisions déclarées formellement validées et de leurs preuves ; aucune décision réputée validée sur affirmation seule |
| **C0-7** | **Registres** | Pertinence et traçabilité des doublons, contradictions, divergences terminologiques signalés |
| **C0-8** | **Lacunes et questions** | Couverture, justification ; absence de réponses ou corrections non autorisées |
| **C0-9** | **Sources historiques et statutsdocumentaires** | Respect des distinctions d'autorité (pas d'attribution normative par défaut) et de statut documentaire |
| **C0-10** | **Référence C0 et rapport** | Cohérence entre constats, données inventoriées et état de référence figé (référence_c0.md) |
| **C0-11** | **Proposition C1** | Traçabilité des recommandations vers les constats C0 ; absence de démarrage anticipé de C1 |
| **C0-12** | **Réserves R1 à R5** | État de chaque réserve ; preuve de traitement éventuel ; risque résiduel ; recommandation |

## 3. Contraintes et restrictions

**Pendant l'audit, jusqu'à décision ultérieure du VALIDATOR :**

- Aucun merge vers `main`
- Aucun démarrage de C1
- Aucune correction des livrables ou documents sources par l'AUDITOR
- Aucune modification de `state.json` ou `state.md` par l'AUDITOR
- Aucune nouvelle autorisation Git implicite

**Toute anomalie critique, divergence de mandat ou preuve manquante susceptible de compromettre l'audit doit être signalée à l'ORCHESTRATOR et portée à l'attention du VALIDATOR.**

## 4. Format du rapport attendu

L'AUDITOR produira un rapport dans :

`audit_report/C0_audit_report.md`

Le rapport devra comporter :

- **Synthèse exécutive** : vue d'ensemble du résultat global
- **Périmètre et méthode** : description de l'étendue et des méthodes d'audit employées
- **Matrice des contrôles** : tableau récapitulant tous les contrôles C0-1 à C0-12 avec leurs résultats
- **Preuves examinées** : référence précise de chaque preuve consultée (fichiers, commits, état Git, registres, etc.)
- **Non-conformités et observations** : écarts identifiés, écarts par rapport au mandat C0-revise-v1
- **Analyse des réserves R1 à R5** : état de chaque réserve, risque résiduel, recommandation
- **Limites de l'audit** : périmètre non couvert, éléments inaccessibles, hypothèses nécessaires
- **Verdict global motivé** : l'un des suivants `PASS`, `PASS_WITH_RESERVES`, `FAIL` ou `HOLD`
- **Recommandations au VALIDATOR** : propositions pour décision HVG0-B

## 5. Règles de notation des contrôles

| Statut | Signification |
|---|---|
| `PASS` | Contrôle vérifié et conforme au mandat |
| `FAIL` | Non-conformité établie |
| `NOT_CHECKED` | Contrôle non réalisé ou preuve insuffisante |

**Règle impérative** : `NOT_CHECKED` ne vaut jamais `PASS`. Un contrôle non réalisé ne peut pas être présenté comme vérifié.

## 6. Restrictions additionnelles

- L'AUDITOR travaille indépendamment du BUILDER
- L'AUDITOR ne corrige pas les livrables ni ne modifie les documents sources
- L'AUDITOR ne peut pas attribuer de décision HVG0-B ; cette décision demeure exclusivement réservée au VALIDATOR humain
- L'AUDITOR ne peut pas non plus lancer BUILDER ni exécuter des tâches C0

## 7. Remise du mandat et démarrage

Avant le démarrage de l'AUDITOR, l'ORCHESTRATOR devra :

1. ✅ Formaliser ce mandat d'audit (document présent)
2. ✅ Identifier les fichiers et preuves accessibles à l'AUDITOR (état Git, livrables C0 dans `dev_C0`, state.json, registre des réserves, etc.)
3. ✅ Vérifier la cohérence de la transition et de son destinataire (TR-2026-0001, du `authorized`/`consumed` au `GO_WITH_RESERVES`)
4. ✅ Transmettre le mandat à l'AUDITOR (courant présent)
5. ⏳ Attendre son rapport sans influencer son verdict

## 8. Chemin d'accès du rapport

Le rapport final sera déposé à l'emplacement :

`audit_report/C0_audit_report.md`

Les fichiers d'appui, preuves et registres pourront être consultés dans :

`livrables/C0/` (inventaire, métadonnées, registres, décisions, classification, lacunes, statuts documentaires, référence C0, proposition C1)  
`state.json` (état global, décision dernièrement prise, réserves)  
`dev_C0` (branche de livraison, commits traçables, état final)  
`audit_report/` (répertoire de travail de l'audit)

---

**Fin du mandat d'audit C0.** Ce document autorise l'instruction de l'audit indépendant. L'AUDITOR pourra maintenant commencer son travail d'examen sur la livraison C0, dans le respect des contraintes et de l'indépendance requises. Le verdict de l'audit sera transmis au VALIDATOR pour décision HVG0-B.

*Orchestrateur — 24 novembre 2026*