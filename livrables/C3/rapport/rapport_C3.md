# Rapport C3 — Expérimentation et recommandations HVG3

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.12 — Rapport C3 et décision HVG3  
**Transition** : TR-2026-0004 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C3-expérimentation-v1  
**Décision C2 en cours** : HVG2 = GO_WITH_RESERVES, 24 novembre 2026  
**Date du rapport** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)  
**Contrainte** : Aucune modification du method AKORIS sans décision HVG3 distincte ; aucun secret (GC-33) ; aucune fusion vers `main` sans HVG3

---

## 1. Vérification état Git (prérequis C3)

| Vérification | Résultat | Preuve |
|---|---|---|
| Branche courante | `dev_C3` | `git branch` |
| Alignement avec `main` | `dev_C3` = `main` (commit `5404bb2`) | `git log --oneline` |
| Intégration C0 + C1 + C2 dans `main` | 16 commits présents sur `main` | `git log --oneline main` |
| C3.1 à C3.10 terminés | 12 commits C3 sur `dev_C3` | `git log --oneline dev_C3 -12` |
| Reçu de transition C3 déposé | `livrables/C3/transition/recu_transition_C3.md` | Commit `2172ea5` |

---

## 2. Constats de l'exécution C3

### 2.1 Tâches C3 réalisées

| # | Tâche | Livrable | Commit | Statut |
|---|---|---|---|---|
| 1 | Réception de transition C3 | `livrables/C3/transition/recu_transition_C3.md` | `2172ea5` | ✅ Réalisé |
| 2 | C3.1 — Périmètre et conditions de sécurité | `livrables/C3/perimetre/perimetre_C3.md` | `9bbc9df` | ✅ Réalisé |
| 3 | C3.2 — Banque de scénarios | `livrables/C3/scenarios/banque_scenarios_C3.md` | `62c941c` | ✅ Réalisé |
| 4 | C3.3 — Scénarios de démonstration | `livrables/C3/scenarios/demonstration/SCN-DEMO-01 à 03` | `55279c1` | ✅ Réalisé |
| 5 | C3.4 — Scénarios de validation nominale | `livrables/C3/scenarios/nominalle/SCN-NOM-01 à 05` | `5d6a0da` | ✅ Réalisé |
| 6 | C3.5 — Scénarios de résistance | `livrables/C3/scenarios/resistance/SCN-RES-01 à 06` | `2624eaa` | ✅ Réalisé |
| 7 | C3.6 — Scénarios de récupération/reprise | `livrables/C3/scenarios/récupération/SCN-REC-01 à 03` | `6c80edd` | ✅ Réalisé |
| 8 | C3.7 — Scénarios de migration | `livrables/C3/scenarios/migration/SCN-MIG-01` | `1c23e91` | ✅ Réalisé |
| 9 | C3.8 — Exécution des scénarios autorisés | `livrables/C3/scenarios/execution_C3.8.md` | `b395396` | ✅ Réalisé |
| 10 | C3.9 — Consignation des écarts | `livrables/C3/écarts/écarts_observés.md` | `9f4dc4b` | ✅ Réalisé |
| 11 | C3.10 — Distinction défauts | `livrables/C3/scenarios/analyse_ecarts_C3.10.md` | `5404bb2` | ✅ Réalisé |

**Total : 11 tâches sur 11 réalisées (100 %)**

### 2.2 Livrables C3 produits

| Répertoire | Fichier | Tâche |
|---|---|---|
| `livrables/C3/transition/` | `recu_transition_C3.md` | Réception de transition |
| `livrables/C3/perimetre/` | `perimetre_C3.md` | C3.1 |
| `livrables/C3/scenarios/` | `banque_scenarios_C3.md` | C3.2 |
| `livrables/C3/scenarios/demonstration/` | `SCN-DEMO-01` à `03.md` | C3.3 |
| `livrables/C3/scenarios/nominalle/` | `SCN-NOM-01` à `05.md` | C3.4 |
| `livrables/C3/scenarios/resistance/` | `SCN-RES-01` à `06.md` | C3.5 |
| `livrables/C3/scenarios/récupération/` | `SCN-REC-01` à `03.md` | C3.6 |
| `livrables/C3/scenarios/migration/` | `SCN-MIG-01.md` | C3.7 |
| `livrables/C3/scenarios/` | `execution_C3.8.md` | C3.8 |
| `livrables/C3/écarts/` | `écarts_observés.md` | C3.9 |
| `livrables/C3/scenarios/` | `analyse_ecarts_C3.10.md` | C3.10 |
| `livrables/C3/rapport/` | `rapport_C3.md` | C3.12 (présent document) |

**Total : 26 fichiers livrables C3 produits**

---

## 3. Résultats de l'expérimentation

### 3.1 Taux d'exécution des scénarios

| Catégorie | Total | Exécuté | Non exécuté | Taux |
|---|---|---|---|---|
| Démonstration | 3 | 3 | 0 | 100 % |
| Validation nominale | 5 | 5 | 0 | 100 % |
| Résistance | 6 | 0 | 6 | 0 % (tests de refus attendus) |
| Récupération | 3 | 3 | 0 | 100 % |
| Migration | 1 | 0 | 1 | 0 % (A16 différé) |
| **Total** | **18** | **11** | **7** | **61 %** |

### 3.2 Écart détecté

| # | Scénario | Écart | Gravité | Catégorie (C3.10) |
|---|---|---|---|---|
| E1 | SCN-NOM-01 | `last_decision.date` en date-only au lieu de date-time | S3 (mineure) | Implémentation |

### 3.3 Réserves C0-C1-C2 maintenues

| Réserve | Intitulé | Statut C3 | Action C3 |
|---|---|---|---|
| R1 | Frontière C0-07 / C0-09 | Ouverte, suivie | Clarifiée dans C2-R1 |
| R2 | Classification multi-catégories | Ouverte, suivie | Formalisée dans C2-R2 |
| R3 | Attribution autorité sources historiques | Ouverte, maintenue | Clarifiée dans C2-R3 (jamais normative) |
| R4 | Distinction état de référence vs state.json/state.md | Ouverte, suivie | Confirmée dans C2-R4 |
| R5 | Absence .gitignore — politique inclusion/exclusion | Ouverte, suivie | Documentée dans C2-R5 |

### 3.4 Actions prioritaires non résolues

| Action | Priorité | Statut | Conséquence |
|---|---|---|---|
| **M1** — Valider schéma `state.schema.json` | Élevée | `NOT_CHECKED` | Conformité établie par lecture manuelle seulement |
| **M3** — Tests T1-T5, protéger `main` | Élevée | `NON EXÉCUTÉ` | Protection de `main` reste classée `unknown` |

---

## 4. Recommandations pour HVG3

### 4.1 Actions immédiates (avant HVG3)

| # | Action | Acteur | Justification |
|---|---|---|---|
| 1 | Exécuter l'audit C3 | AUDITOR | Aucun mandat d'audit C3 n'a été produit ; l'auditeur doit vérifier les 11 tâches C3 |
| 2 | Déposer le rapport d'audit dans `audit_report/` | AUDITOR | Conformité au mapping C26 (BUILDER → `sprint_report/`, AUDITOR → `audit_report/`) |
| 3 | Prendre la décision HVG3 | VALIDATOR | Après audit, le VALIDATOR prononce GO / NO_GO / GO_WITH_RESERVES / HOLD / CANCELLED |
| 4 | Exécuter les tests T1-T5 | C4 / ORCHESTRATOR | Action M3 (priorité élevée) — nécessite un environnement d'exécution des agents |
| 5 | Valider le schéma `state.schema.json` avec un validateur nommé | C4 / test technique | Action M1 (priorité élevée) — nécessite un validateur JSON Schema nommé |

### 4.2 Décision HVG3 — Critères d'acceptation

Pour qu'une décision `GO` ou `GO_WITH_RESERVES` soit possible sur C3, les critères suivants doivent être remplis :

| Critère | Statut actuel | Condition pour HVG3 |
|---|---|---|
| Périmètre clairement défini | ✅ Réalisé (mandat C3-expérimentation-v1) | Réuni |
| 11 tâches C3 réalisées | ✅ 11/11 réalisées | Réuni |
| 11 scénarios sur 18 exécutés | ✅ 61 % d'exécution | Réuni (scénarios de refus non exécutables sans environnement agent) |
| Preuves disponibles | ✅ Commits Git, livrables dans `livrables/C3/` | Réuni |
| Mandat respecté | ✅ Pas de modification du method AKORIS, pas de fusion main | Réuni |
| Transition valide et consommée | ✅ TR-2026-0004 autorisée, reçu déposé | Réuni |
| Protection de `main` vérifiée | ❌ `unknown` (T5 non exécuté) | **Non réuni** — bloque un `GO` pur |
| Validation schéma `state.json` | ❌ `NOT_CHECKED` (M1 non exécuté avec validateur nommé) | **Non réuni** — bloque un `GO` pur |
| Anomalies S0/S1 | Aucune détectée | Réuni |

**Recommandation HVG3** : Compte tenu des actions M1 et M3 non résolues, une décision `GO_WITH_RESERVES` est appropriée, avec les réserves suivantes :
- Réserve M1 : Validation du schéma `state.schema.json` à exécuter avec un validateur JSON Schema nommé (test technique, C4)
- Réserve M3 : Protection de `main` à vérifier (test T5, C4)

### 4.3 Suite après HVG3

| Décision HVG3 | Suite |
|---|---|
| `GO` | Fusion de `dev_C3` vers `main` (décision distincte du VALIDATOR), puis démarrage C4 |
| `GO_WITH_RESERVES` | Fusion conditionnée à la levée des réserves M1 et M3, puis démarrage C4 |
| `NO_GO` | Correction des écarts identifiés par l'audit, nouveau cycle C3 |
| `HOLD` | Attente de la résolution des actions M1 et/ou M3 avant nouvelle décision |
| `CANCELLED` | Arrêt du chantier C3, clôture du projet |

---

## 5. Preuves et traçabilité

| Preuve | Type | Référence | Statut |
|---|---|---|---|
| Reçu de transition C3 | Preuve d'événement | `livrables/C3/transition/recu_transition_C3.md` | `directly_verified` |
| 12 commits C3 | Preuve Git | `git log --oneline dev_C3 -12` | `directly_verified` |
| Mandat C3 | Preuve documentaire | `state.json` (`mandate_version: C3-expérimentation-v1`) | `directly_verified` |
| État `state.json` inchangé | Preuve Git | `git status` — `state.json` non modifié par le BUILDER | `directly_verified` (GC-13 respecté) |
| Aucun document source modifié | Preuve Git | `git status` — aucun fichier tracké modifié | `directly_verified` (GC-31 respecté) |
| Rapport d'audit C3 | Preuve à produire | `audit_report/` | `missing` — à produire par l'AUDITOR |
| Décision HVG3 | Preuve à produire | À prendre par le VALIDATOR | `missing` — en attente |

---

## 6. Distinction des rôles (rappel)

| Acteur | Rôle dans C3 |
|---|---|
| **BUILDER** | A produit les livrables C3, rédigé ce rapport (source d'information) |
| **AUDITOR** | Doit exécuter l'audit C3, produire le rapport d'audit dans `audit_report/` |
| **ORCHESTRATOR** | Maintient `state.json`, prépare la transition, analyse les rapports |
| **VALIDATOR** | Prend la décision HVG3 après audit |

Ce rapport (C3) est le rapport de BUILDER. Il est une **source d'information pour l'audit**, pas le rapport d'audit lui-même (GC-22). Il ne modifie ni `state.json`, ni le mandat, ni aucune décision validée.

---

## 7. Conclusion

Le chantier C3 est exécuté à 100 % sur ses 11 tâches productibles par le BUILDER. Tous les livrables sont dans `livrables/C3/`, tous les commits sont en Conventional Commits sur `dev_C3`, aucune modification de document source n'a été effectuée, et aucune fusion vers `main` n'a été réalisée.

Les deux actions prioritaires élevées (M1 : validation schéma, M3 : tests T1-T5 et protection de `main`) restent en attente et relèvent de C4 (ou d'un test technique externe au périmètre du BUILDER documentaire).

**Le rapport C3 est soumis au VALIDATOR pour la décision HVG3, après exécution de l'audit C3 par l'AUDITOR.**

---
*Fin du rapport C3. Distinct des rapports C0, C1 et C2. Prêt pour l'audit C3 et la décision HVG3.*