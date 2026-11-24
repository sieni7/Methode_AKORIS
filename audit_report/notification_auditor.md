# Notification de mandat d'audit C0 — AKORIS

**Transition** : TR-2026-0001  
**Mandat** : C0-audit-mandate (mandat d'audit indépendant)  
**Destinataire** : AUDITOR DOCUMENTAIRE  
**Émetteur** : ORCHESTRATOR  
**Date** : 2026-11-24  
**Ordre VALIDATOR** : Décision GO_WITH_RESERVES (HVG0), référence TR-2026-0001  

## 1. Mandat formel

Je te transmets ci-après le mandat d'audit indépendant portant sur l'intégralité de la livraison du chantier C0 — Inventaire et état de référence du corpus AKORIS — telle que produite par le BUILDER DOCUMENTAIRE sur la branche `dev_C0`.

Conformément à la décision VALIDATOR GO_WITH_RESERVES (HVG0) du 24 novembre 2026, cet audit vise à vérifier la conformité, l'intégrité et la traçabilité de la production C0.

**Important** : Cet ordre n'est ni une acceptation de C0, ni une autorisation de fusion vers `main`, ni une autorisation de démarrage de C1. La décision HVG0-B demeurera exclusivement réservée au VALIDATOR humain après réception et examen du rapport d'audit.

## 2. Étendue de l'audit

Tu devras examiner les 12 domaines de contrôle définis dans le mandat (C0-1 à C0-12), conformément aux critères et méthodes spécifiés. Pour chaque contrôle, tu fourniras :
- L'identifiant du contrôle
- Le critère vérifié
- La méthode employée
- La preuve consultée et sa référence précise
- Le résultat observé (PASS / FAIL / NOT_CHECKED)
- Les écarts éventuels
- L'impact et le niveau de gravité
- Une conclusion motivée

**Rappel impératif** : `NOT_CHECKED` ne vaut jamais `PASS`. Un contrôle non réalisé ne peut pas être présenté comme vérifié.

## 3. Fichiers et preuves accessibles

Tu as accès aux fichiers et preuves suivants dans le cadre de cet audit :

| Catégorie | Fichiers et ressources |
|---|---|
| **État global** | `state.json` — décision dernièrement prise (D-001-HVG0 GO_WITH_RESERVES), 5 réserves R1-R5, état du projet |
| **Mandat C0** | `livrables/C0/mandat_builder.md` — mandat opérationnel complet (12 tâches, critères d'acceptation, preuves, contraintes) |
| **Transition et réception** | `livrables/C0/transition/recu_transition_C0.md` — reçu de transition déposé<br>`livrables/C0/transition/notification_builder.md` — notification de transition vers BUILDER |
| **Plan de référence** | `plan_de_consolidation.md` — plan directeur AKORIS v0.1.0-draft, engagement C0 |
| **Inventaire (modèles)** | `livrables/C0/` sous-répertoires : inventaire/, metadonnees/, registres/, classification/, decisions/, lacunes/, stats_doc/, rapport/, perimetre-C1/ — définissant les formats et critères attendus |
| **Git et branche** | Branche `dev_C0` issu de `main` (commit `f3b2eb7`) ; historique des commits ; état actuel du dépôt |
| **Lecteur de référence** | Tous les fichiers de référence : `reference/`, `protocol/`, `template/` |

**Fichiers hors portée (non à modifier) :**
- Aucun fichier source documentaire existants dans la racine ou `_sources/`
- `plan_de_consolidation.md` en l'état (non modifier)
- `state.json` — tu peux le lire mais ne pas y apporter de modifications (conformément aux restrictions d'audit)
- Tout fichier qui n'aurait pas été produit dans le cadre de C0

## 4. Restrictions pendant l'audit

Jusqu'à décision ultérieure du VALIDATOR, les règles suivantes s'appliquent :

- **Aucun merge vers `main`** : la branche `dev_C0` reste isolée
- **Aucun démarrage de C1** : tu ne déclencheras pas le chantier C1
- **Aucune correction des livrables ou documents sources** : tu constate seulement, tu ne corriges pas
- **Aucune modification de `state.json` ou `state.md`** : lecture seule pour toi aussi
- **Aucune nouvelle autorisation Git implicite** : tu travailles avec les autorisations qui existent déja, documentées dans le mandat

**Toute anomalie critique, divergence de mandat ou preuve manquante susceptible de compromettre l'audit doit être signalée à l'ORCHESTRATOR et portée à l'attention du VALIDATOR.**

## 5. Livrable attendu

Tu produiras un rapport dans :

`audit_report/C0_audit_report.md`

Le rapport devra comporter :
- Synthèse exécutive
- Périmètre et méthode
- Matrice des contrôles (C0-1 à C0-12 avec résultats)
- Preuves examinées
- Non-conformités et observations
- Analyse des réserves R1 à R5
- Limites de l'audit
- Verdict global motivé (PASS / PASS_WITH_RESERVES / FAIL / HOLD)
- Recommandations au VALIDATOR

## 6. Début d'audit

Vous pouvez maintenant commencer votre travail d'examen indépendant sur la livraison C0. Vous avez accès aux fichiers listés ci-dessus dans le but de réaliser les 12 contrôles définis.

**Principe de gouvernance** : L'IA propose (ici, le mandat est préparé). Les contrôles vérifient (tu vas examiner). L'humain décide (le VALIDATOR prononcera HVG0-B après réception de ton rapport).

Tu es maintenant officiellement engagé dans l'audit indépendant C0. Bonne examination.

---

*Notification générée par l'ORCHESTRATOR le 24 novembre 2026, suite à la décision VALIDATOR GO_WITH_RESERVES (TR-2026-0001).*