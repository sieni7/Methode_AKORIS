# Proposition de périmètre C1 — Soumise au VALIDATOR

**Chantier** : C0 — Inventaire et état de référence du corpus AKORIS  
**Tâche** : C0-12 — Proposer périmètre C1 au VALIDATOR  
**Date de la proposition** : 2026-11-24  
**Mandat** : C0-revise-v1  
**Décision C0 en cours** : GO_WITH_RESERVES (HVG0), 2026-11-24, 5 réserves R1-R5  
**Contrainte** : Pas de décision HVG1 prise ici — uniquement proposition. Respect de la lecture seule de C0.

---

## 1. Objet

Cette proposition définit le périmètre du chantier C1 (Consolidation normative et documentaire) de manière cohérente avec les résultats de l'inventaire C0. Elle est soumise au VALIDATOR pour la décision HVG1 (seuil C1). Aucune décision HVG1 n'est prise dans ce document.

---

## 2. Lien avec les constats C0

Le périmètre C1 est directement dérivé des constats C0, consignés dans `livrables/C0/rapport/rapport_C0.md` et `livrables/C0/reference/référence_c0.md`. Chaque domaine C1 correspond à un ou plusieurs constats, lacunes, questions ou divergences identifiés en C0.

| Domaine C1 | Constats C0 à l'origine | Livrables C0 de référence |
|---|---|---|
| C1A — Hiérarchie documentaire, statuts, autorité, prévalence | Classification (1.3), statuts (1.4), doublons (1.6), contradictions (1.6) | `tableau_classification.md`, `tableau_statu.md`, `registre_doublons.md`, `registre_contradictions.md` |
| C1B — Modèle d'état, `state.json`, `state.md`, mandats, reçus, cycle de vie | Décisions (1.5), contradictions C3/C8, lacunes L1/L2/L3 | `registre_decision.md`, `registre_contradictions.md`, `liste_lacunes.md` |
| C1C — Permissions, rôles, périmètres, interdictions, exceptions, limites | Contradictions C10/C14, lacunes L4/L12, questions Q8/Q19 | `registre_contradictions.md`, `liste_lacunes.md`, `questions_questions.md` |
| C1D — Décisions, preuves, rapports, registres, contestations, questions, historique | Décisions (1.5), lacunes L1/L7/L8, questions Q8/Q9/Q10 | `registre_decision.md`, `liste_lacunes.md`, `questions_questions.md` |
| C1E — Versions et évolution (SemVer A15, protocole/schéma/document) | Métadonnées (1.2), divergences T10/T11, lacune L3, question Q11 | `tableau_metadonnees.md`, `registre_divergences.md`, `liste_lacunes.md` |
| C1F — Git/GitHub (tâches, branches, commits, audit, fusion, vérification) | Inventaire (1.1), lacune L24, réserve R5 | `arborescence_fichiers.md`, `etat_git.md`, `liste_lacunes.md` |

---

## 3. Périmètre détaillé par domaine

### C1A — Hiérarchie documentaire, statuts, autorité et prévalence des sources

**Objectif** : Établir la hiérarchie documentaire, les statuts documentaires, l'autorité et la prévalence des sources du cadre AKORIS.

**Contenus proposés** :
- Hiérarchie d'autorité complète des sources (niveaux 1 à 6, avec décisions humaines au niveau 1)
- Tableau des statuts documentaires actualisé (approuvé / proposé / obsolète / retiré / non vérifié)
- Règle de prévalence en cas de divergence entre sources
- Traitement des 20 doublons (D1-D20) : désignation d'une source principale unique par information
- Traitement des 25 contradictions (C1-C25) : arbitrage par décision VALIDATOR de chacune

**Lien C0** : Constats 1.3, 1.4 ; registres doublons/contradictions/divergences.

### C1B — Modèle d'état, `state.json`, `state.md`, mandats, reçus, cycle de vie des transitions

**Objectif** : Consolider le modèle d'état, la structure de `state.json`, la vue `state.md`, les mandats, les reçus de transition et le cycle de vie des transitions.

**Contenus proposés** :
- Validation de la structure v2.0 de `state.json` (A2) avec schéma `reference/state.schema.json`
- Définition de la table de transition des états de projet (proposition C0, §2.2 de `state_model.md`)
- Définition de la table de transition des états de sprint (proposition C0, §3.2 de `state_model.md`)
- Procédure de migration pilote v1.0 → Norme v2.0 (lacune L3, A16 différé)
- Consolidation du mécanisme de reçu de transition (C8 révisé, `transition_policy.md`)

**Lien C0** : Constats 1.5, 1.6 (C3, C8) ; lacunes L1, L2, L3.

### C1C — Permissions, rôles, périmètres, interdictions, exceptions, limites

**Objectif** : Définir la matrice des permissions, les rôles, les périmètres, les interdictions, les exceptions et les limites, avec distinction entre permissions déclarées et permissions techniquement imposées.

**Contenus proposés** :
- Matrice complète des permissions (rôles × ressources × niveau), statuts `technical_enforced` / `procedural_only` / `post_checked` / `not_available` / `unknown`
- Procédure de vérification effective des permissions (tests T1 à T5)
- Clarification du niveau des permissions (C10 révisé)
- Protection de `main` : test T5 et décision sur le statut `unknown` (C29)

**Lien C0** : Constats 1.6 (C10, C14) ; lacunes L4, L12 ; registre contradictions.

### C1D — Décisions, preuves, rapports, registres, contestations, questions et historique

**Objectif** : Consolider le registre des décisions, les preuves, les rapports, les registres de contestation, les questions ouvertes et l'historique.

**Contenus proposés** :
- Création du registre des décisions (`decision_log.md`, lacune L1)
- Règles de preuve et statuts de preuve (directly_verified, reproduced, cross_checked, declared_only, partial, missing, invalid)
- Seuil quantitatif de gravité d'anomalie (C25, lacune L7) — à arbitrer par le VALIDATOR
- Règle de quorum ou de délégation de décision (lacune L8) — à arbitrer
- Décision en cas d'absence prolongée du VALIDATOR (lacune L9) — à arbitrer

**Lien C0** : Constats 1.5 ; lacunes L1, L7, L8 ; questions Q8, Q9, Q10.

### C1E — Versions et évolution

**Objectif** : Consolider les règles de versionnement déjà approuvées (A15) ; distinguer versions protocole/schéma et révisions documentaires.

**Contenus proposés** :
- Application prospective des règles SemVer pour le protocole et le schéma (A15)
- Révision simple pour les documents (A15)
- Clarification de la relation entre version du protocole, version du schéma et version du document (divergence T10/T11, A14)
- Champ de version du profil dans `state.json` : aucun champ ajouté (décision A10 confirmée)
- Procédure de migration v1.0 → v2.0 : à arbitrer (A16 différé)

**Lien C0** : Constats 1.2 ; divergences T10, T11 ; lacunes L3 ; questions Q11.

### C1F — Git/GitHub

**Objectif** : Définir les règles Git/GitHub : tâches atomiques, branches, commits conventionnels, audit, acceptation, autorisation de fusion et vérification post-fusion.

**Contenus proposés** :
- Règles de création de branche et de nommage des commits (Conventional Commits)
- Procédure d'audit des changements avant fusion
- Autorisation de fusion distincte de l'acceptation du sprint (DP §9, GC-07)
- Vérification post-fusion sur `main`
- Documentation de la politique d'inclusion/exclusion (`.gitignore`, réserve R5, lacune L24)

**Lien C0** : Constats 1.1 (absence de `.gitignore`) ; lacune L24 ; réserve R5.

---

## 4. Traitement des 5 réserves C0 dans le périmètre C1

| Réserve | Intitulé | Traitement proposé dans C1 |
|---|---|---|
| R1 | Frontière C0-07 / C0-09 — distinction lacunes/questions/dépendances vs statuts documentaires | Maintenir la séparation dans les livrables C1 ; aucun chevauchement entre `liste_lacunes.md`, `questions_questions.md`, `dependances_carte.md` et `tableau_statu.md` |
| R2 | Classification multi-catégories | Conserver catégorie principale + secondaires justifiées dans tous les documents C1 |
| R3 | Attribution autorité sources historiques | Aucune autorité normative par défaut aux sources historiques dans C1 ; niveau d'autorité déclaré seulement |
| R4 | État de référence vs state.json/state.md | Maintenir la distinction : état de référence C0 (markdown, figé) vs états opérationnels (`state.json`/`state.md`) |
| R5 | Fichiers .gitignore et ignorés | Documenter la politique d'inclusion/exclusion dans C1F |

---

## 5. Priorités proposées pour C1

| Priorité | Domaine | Justification (constat C0) |
|---|---|---|
| Haute | C1B — Modèle d'état et `state.json` | Lacunes L1, L2, L3 bloquantes pour la traçabilité et la vérifiabilité de l'état |
| Haute | C1A — Hiérarchie et statuts | Doublons D2, D3, D5, D10, D14 et contradictions C1, C3, C5 à forte charge de divergence |
| Haute | C1C — Permissions | Protection de `main` inconnue (L12, C29) ; matrice des permissions incomplète (L4) |
| Moyenne | C1D — Décisions et registre | Registre des décisions manquant (L1) ; aucun seuil de gravité (L7, C25) |
| Moyenne | C1E — Versionnement | Divergences T10/T11 sur les catégories de versions ; migration v1.0 → v2.0 non définie (L3) |
| Basse | C1F — Git/GitHub | Absence de `.gitignore` (L24, R5) ; règles de fusion et de branche à formaliser |

---

## 6. Contraintes pour C1

- Respect de la lecture seule de C0 : aucune modification de document source sans décision HVG0 distincte et nouveau mandat
- Pas de fusion vers `main` sans décision HVG0 distincte du VALIDATOR
- Pas de modification de `state.json` ni de `state.md` (GC-13)
- Pas d'autorité normative attribuée aux sources historiques (réserve R3)
- Pas de décision HVG1 dans ce document : seule une proposition de périmètre est produite
- Périmètre suffisamment précis pour permettre la décision HVG1

---

## 7. Ce qui est exclu du périmètre C1 (à ce stade)

- Décision HVG1 (seuil C1) — relève du VALIDATOR, pas de cette proposition
- Corrections spontanées de divergences ou lacunes détectées en C0
- Modification de documents sources sans décision HVG0 distincte
- Fusion vers `main` sans décision HVG0 distincte
- Attribution d'autorité normative aux sources historiques
- Exécution des tests T1 à T5 (relevant de C2, pas de C1)

---

## 8. Prochaine étape

Cette proposition est soumise au VALIDATOR. Après décision HVG1 distincte, le chantier C1 pourra démarrer sur la base de ce périmètre, éventuellement ajusté par le VALIDATOR.

---
*Fin de la proposition de périmètre C1. Pas de décision HVG1 prise ici. Distinct du rapport C0 et de l'état de référence.*