# Profil Standard

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | Projet logiciel réel — **profil par défaut** |
| Autorité | Niveau d'exigence |
| Vague | 2 |

**Sources citées :** `F3` = `AKORIS_consolide.md` §4.2 · `F2` = `AKORIS_architecture_documentaire.md` §4.4 · `GC` = `protocol/governance_core.md` · décisions VALIDATOR A1, A3, A6.

---

## 0. Nature du profil

Le profil Standard est le **profil par défaut** d'un projet logiciel réel. Il s'applique lorsqu'aucun motif ne justifie ni l'allègement du profil Lite, ni le renforcement du profil Reinforced.

Il ne modifie aucun principe du socle : il fixe le **niveau d'exigence** en documentation, preuve, validation et audit.

**Disponibilité (A3).** Les trois profils restent dans la doctrine AKORIS. Leur disponibilité dans l'implémentation de référence est déclarée séparément, et elle n'est **pas établie** à ce jour : voir §10.

---

## 1. Usage et niveau de risque

| Élément | Valeur |
|---|---|
| Usage type | Application ou outil logiciel destiné à un usage réel |
| Exposition | Modérée à significative |
| Réversibilité attendue | R1 à R2 (correction simple à migration) |
| Données | Aucune donnée sensible par défaut |
| Obligations réglementaires | Aucune obligation lourde par défaut |
| Profil de référence | Oui — sert de base aux profils Lite et Reinforced |

> **INCONNU.** Aucune échelle de risque chiffrée n'est définie dans les sources. Le choix du profil relève d'une appréciation qualitative du VALIDATOR, tracée dans `state.json`. Un projet ne peut pas choisir Lite pour éviter un contrôle rendu nécessaire par son niveau de risque.

---

## 2. Critères de sélection

Le profil Standard est retenu lorsque le projet :

- produit un logiciel réellement utilisé, au-delà du prototype ;
- justifie une architecture et des décisions techniques tracées ;
- nécessite une vérification indépendante à chaque incrément ;
- ne présente pas les caractéristiques de risque du profil Reinforced ;
- ne peut pas être livré sans revue humaine avant fusion.

En cas de doute entre Standard et Reinforced, le niveau supérieur s'applique.

---

## 3. Exigences documentaires

| Document | Statut | Source de référence |
|---|---|---|
| Cadrage validé (CP1) | Obligatoire | `contexte.md` |
| Exigences fonctionnelles et non fonctionnelles pertinentes | Obligatoire | `docs/requirements/` |
| Architecture | Obligatoire | `docs/architecture/` |
| ADR structurants | Obligatoire | `docs/adr/` |
| Roadmap | Obligatoire | `sprints/roadmap.md` |
| État central | Obligatoire | `state.json` |
| Mandat de sprint | Obligatoire | `current_sprint.md` |
| Critères d'acceptation | Obligatoire | `docs/acceptance_criteria/` |
| Règles métier validées | Obligatoire | `docs/business_rules/` |
| Registre des risques | Recommandé | `docs/risks/` |
| Rapports de sprint et d'audit | Obligatoire | `sprint_report/`, `audit_report/` |
| Registre des réserves | Obligatoire | `debt_report/` |

Aucun document n'est produit « pour la forme » : un document obligatoire non renseigné est une non-conformité, pas un document vide.

---

## 4. Exigences de preuve

| Type de critère | Preuve minimale admise |
|---|---|
| Critère critique | `directly_verified` ou `reproduced` |
| Critère fonctionnel | `directly_verified`, `reproduced` ou `cross_checked` |
| Critère non fonctionnel | `directly_verified` ou mesure reproductible |
| Élément déclaratif | `declared_only` admis, jamais pour un critère critique |

Règles applicables : `GC-22` à `GC-28`. Une preuve `NOT_CHECKED` ne vaut jamais `PASS`.

---

## 5. Validations humaines

| Objet | Validateur | Condition |
|---|---|---|
| Profil de gouvernance | VALIDATOR | Avant CP1, puis verrouillé |
| CP1 — Cadrage | VALIDATOR | Avant toute conception |
| CP2 — Conception et planification | VALIDATOR | Avant toute préparation opérationnelle |
| CP3 — Préparation opérationnelle | VALIDATOR | Avant la première transition |
| Chaque transition | VALIDATOR | Autorisation explicite et identifiée |
| Résultat de sprint | VALIDATOR | Après audit, avant fusion |
| Réserves | VALIDATOR | Acceptation explicite |
| Fusion vers `main` | VALIDATOR | Décision distincte de l'acceptation |
| Déploiement | VALIDATOR | Décision distincte |

Aucune validation n'est déduite d'une autre : accepter un sprint n'autorise ni le sprint suivant, ni la fusion, ni le déploiement (`GC-07`).

---

## 6. Audit

| Élément | Exigence Standard |
|---|---|
| Fréquence | **Chaque sprint** |
| Objet | Mandat, code livré, commits, tests, preuves, critères |
| Méthode | Inspection directe du dépôt, reproduction des tests pertinents |
| Indépendance | **Procédurale par défaut** (`GC-37`) |
| Rapport | Obligatoire, avec éléments non vérifiés déclarés |
| Désaccords | Conservés, jamais lissés |
| Audit de préparation | Obligatoire avant CP3 |

L'auditeur ne corrige pas ce qu'il audite (`GC-15`). Le rapport de BUILDER est une source d'information, pas la source première de vérité.

---

## 7. Transitions et autorisations

- Chaque passage d'un rôle à un autre exige une transition identifiée (`TR-AAAA-NNNN`).
- La transition est autorisée par le VALIDATOR, puis consommée par le destinataire, qui dépose un **reçu**.
- Une transition consommée, expirée ou annulée n'est jamais réactivée (`GC-46`).
- Toute divergence entre l'état et un reçu est une **incohérence bloquante** jusqu'à réconciliation (A2).
- Le détail du mécanisme est défini dans `protocol/transition_policy.md`.

---

## 8. Changements et réserves

| Objet | Exigence Standard |
|---|---|
| Changements majeurs | Procédure complète, analyse d'impact, nouvelle version de mandat |
| Changements mineurs | Tracés, analyse d'impact allégée |
| Changements éditoriaux | Tracés, sans analyse d'impact |
| Réserves | Identifiées, qualifiées, affectées, planifiées, validées |
| Réserve masquant une anomalie S0/S1 | Interdite |
| Changement de profil | Procédure de changement, décision VALIDATOR |

Le détail est défini dans `protocol/change_control.md` et `protocol/decision_policy.md`.

---

## 9. Livrables attendus par sprint

1. Mandat versionné (`current_sprint.md`).
2. Transition autorisée et reçu déposé.
3. Code livré sur une branche dédiée, commits traçables.
4. Rapport de sprint avec preuves.
5. Rapport d'audit indépendant.
6. Recommandation d'ORCHESTRATOR.
7. Décision du VALIDATOR.
8. Réserves éventuelles enregistrées dans `debt_report/`.

---

## 10. Disponibilité dans l'implémentation de référence

| Élément | Constat |
|---|---|
| Profil déclaré dans `state.json` | **Absent** du pilote `demo_web` (`schema_version 1.0`) |
| Valeurs de décision | **3** au lieu de 5 (`GO`, `NO GO`, `GO WITH RESERVES`) |
| Mécanisme de reçu | **Présent** (`agents.md` §7, `getting_started` 06.9) |
| Permissions techniques | **Partielles** — voir `implementations/opencode/agent_permissions.md` |
| Conclusion | Le pilote est **antérieur** au présent profil, et **non conforme** à ce titre |

Cette déclaration est un **constat**, pas un jugement : elle permet de distinguer ce qui est exigé de ce qui est réellement obtenu. Un projet déclaré non conforme ne peut pas prétendre au profil Standard tant que l'écart n'est pas résolu ou explicitement accepté.

---

## 11. Limites du profil

Le profil Standard **ne couvre pas** :

- la classification des données ;
- l'analyse de sécurité formalisée ;
- la stratégie de sauvegarde et de restauration ;
- la stratégie de rollback ;
- les preuves reproductibles de bout en bout ;
- le contrôle des dépendances ;
- les autorisations expirantes ;
- l'analyse des risques résiduels.

Ces éléments relèvent du profil Reinforced. Un projet Standard qui en aurait besoin doit changer de profil, pas contourner l'exigence.

---

## 12. Ce que le profil n'autorise pas

- Considérer une acceptation comme une autorisation de fusion.
- Considérer un rapport positif comme une autorisation de poursuivre.
- Regrouper les checkpoints.
- Remplacer l'audit par une auto-évaluation du BUILDER.
- Déclarer `technical_enforced` une permission non vérifiée.

---

## 13. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 2) |
