# Rapport C0 — Constats, incertitudes et recommandations

**Chantier** : C0 — Inventaire et état de référence du corpus AKORIS  
**Mandat** : C0-revise-v1  
**Transition** : TR-2026-0001  
**Décision VALIDATOR** : GO_WITH_RESERVES (HVG0), 2026-11-24  
**Date du rapport** : 2026-11-24  
**Branche d'exécution** : `dev_C0` (depuis `main` vérifié)  
**Contrainte** : Aucune correction spontanée des documents sources

---

## 1. Constats

### 1.1 Inventaire du corpus

Le corpus AKORIS contient 45 fichiers documentaires répartis dans 8 répertoires :

- Racine : 5 fichiers (`00_cartographie.md`, `README.md`, `changelog.md`, `plan_de_consolidation.md` [untracked], `state.json` [untracked])
- `_sources/` : 3 fichiers sources historiques (F1, F2, F3)
- `implementations/opencode/` : 5 fichiers de constat d'implémentation OpenCode
- `prompts/` : 4 prompts d'amorçage des rôles
- `protocol/` : 12 documents normatifs (socle, profils, politiques)
- `reference/` : 5 référentiels (carte, terminologie, traçabilité, versionnement, schéma)
- `templates/` : 7 modèles de livrables
- `livrables/C0/` : 4 fichiers de transition C0 (préexistants) + livrables C0 en production

39 fichiers sont trackés dans le commit initial `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea`. 6 fichiers sont untracked. Aucun document source n'a été modifié (lecture seule respectée).

Aucun fichier `.gitignore` n'est présent à la racine (réserve R5).

### 1.2 Métadonnées

Chaque document dispose d'un relevé de rôle, statut, version, date et relations. 12 documents ont une version manquante, 12 une date manquante, et 18 un statut documentaire non vérifiable. Aucune valeur manquante n'est inventée ; les valeurs `inconnu`, `non indiqué`, `non vérifiable` sont portées telles quelles.

### 1.3 Classification par nature

| Catégorie | Nombre | Pourcentage |
|---|---|---|
| Normatifs | 13 | 28,9 % |
| Opérationnels | 21 | 46,7 % |
| Explicatifs | 8 | 17,8 % |
| Historiques / sources | 3 | 6,7 % |

4 documents portent une catégorie secondaire justifiée (conformité à la réserve R2).

### 1.4 Statuts documentaires

| Statut | Nombre | Pourcentage |
|---|---|---|
| Approuvé | 3 | 6,7 % |
| Proposé | 24 | 53,3 % |
| Non vérifié | 18 | 40,0 % |

Les 3 documents approuvés sont les livrables V7 validés par le VALIDATOR le 2026-11-21 : `protocol/getting_started.md`, `reference/traceability_map.md`, `reference/versioning_policy.md`. Aucun document n'est obsolète ou retiré.

### 1.5 Décisions

26 décisions formellement validées ont été identifiées (arbitrages A1 à A8, C13 à C34, et D-001-HVG0). 5 propositions, 7 recommandations, 3 décisions non confirmées et 2 décisions historiques de statut inconnu complètent le registre.

La décision C0 en cours est `D-001-HVG0` = `GO_WITH_RESERVES` (VALIDATOR, 2026-11-24), avec 5 réserves R1-R5.

### 1.6 Doublons, contradictions, divergences

- 20 doublons identifiés (D1 à D20), dont les plus coûteux : D2 (rôles), D3 (sources uniques), D5 (schéma state.json), D10 (valeurs de décision), D14 (permissions).
- 25 contradictions identifiées (C1 à C25), dont C1 (3 vs 5 valeurs de décision), C3 (state.json v1.0 vs v2.0), C5 (trois chemins racine du socle), C8 (reçu de transition), C10 (niveau des permissions). C8 et C10 ont été révisées dans le cadre des arbitrages VALIDATOR.
- 15 divergences terminologiques (T1 à T15) et 14 confusions terminologiques documentées (CF-1 à CF-14).

Signalement uniquement — aucune correction apportée.

### 1.7 Sources historiques

5 sources historiques identifiées (S1 à S5), avec niveaux d'autorité déclarés de 2 à 5. Aucune autorité normative n'est attribuée par défaut (conformité à la réserve R3). Le pilote (`demo_web`) implémente une version antérieure (v1.0, sans profils, 3 valeurs de décision, state.json plat) et est déclaré non conforme à la Norme AKORIS v2.0.

---

## 2. Incertitudes

Les incertitudes ci-dessous ne sont pas résolues dans ce rapport ; elles sont transmises telles quelles au chantier C1.

### 2.1 Lacunes (25)

Les principales lacunes incluent :
- Registre des décisions (`decision_log.md`) annoncé mais non créé (L1)
- Validation JSON Schema de `state.json` non reproduite avec un validateur nommé (L2)
- Procédure de migration pilote v1.0 → Norme v2.0 non définie (L3, A16 différé)
- Matrice complète des permissions non fournie (L4)
- Tables de transition des états de projet et de sprint non validées (L5, L6)
- Aucun seuil quantitatif de gravité d'anomalie (L7, C25)
- Aucun test T1 à T5 exécuté (L11)
- Protection de `main` non certifiée (`unknown`, L12)
- Registres de changements, incidents, revues de préparation, reçus ORCHESTRATOR non créés dans le périmètre documentaire (L13 à L16)
- Aucun `.gitignore` (L24)

### 2.2 Questions ouvertes (24)

Les questions incluent notamment :
- Q1 à Q7 : arbitrages A1 à A7 (valeurs de décision, schéma state.json, profils, chemin racine, rôles, statut getting_started v1, versionnement)
- Q8 : échelle de risque chiffrée (C25)
- Q11 : procédure de migration v1.0 → v2.0
- Q18/Q19 : exécution des tests T1 à T5 et vérification de la protection de `main`
- Q20 : divergence interne de `state_model.md` sur l'existence du schéma de validation

### 2.3 Divergences non résolues

Les divergences suivantes sont signalées mais non corrigées :
- C5 : trois chemins racine concurrents pour le socle (`governance/`, `protocol/`, `documentation/protocol/`)
- C6 : collision `README.md` (projet vs documentation)
- C7 : 5 vs 9 états de transition
- C21 : double lecture du statut de `00_cartographie.md` (PROPOSITION vs TRAVAIL)
- C22 : en-tête de `document_map.md` fixé à v0.4 malgré l'évolution du compteur
- C23 : divergence du décompte des 34 documents entre photographie historique et état actuel
- C24 : state.json v2.0 dans le dépôt vs v1.0 du pilote, sans procédure de migration
- C25 : relation état / version de profil non modélisée
- T10/T11 : trois listes coexistantes de catégories de versions

### 2.4 Dépendances non résolues

Plusieurs dépendances critiques sont identifiées sans résolution :
- Registre des décisions (`decision_log.md`) dépend d'une décision de création
- Validation JSON Schema dépend d'un validateur nommé et d'une preuve d'exécution
- Procédure de migration dépend d'une décision humaine (A16)

---

## 3. Recommandations pour C1

### 3.1 Périmètre proposé pour C1

Le périmètre C1 doit s'appuyer sur les constats C0 pour traiter les divergences, lacunes et incertitudes identifiées. Il est proposé comme suit :

| Domaine C1 | Contenu proposé | Lien avec constats C0 |
|---|---|---|
| C1A | Hiérarchie documentaire, statuts, autorité et prévalence des sources | Constats 1.3, 1.4 ; registres doublons/contradictions/divergences |
| C1B | Modèle d'état, `state.json`, `state.md`, mandats, reçus, cycle de vie des transitions | Constats 1.5, 1.6 (C3, C8) ; lacunes L1, L2, L3 |
| C1C | Permissions, rôles, périmètres, interdictions, exceptions, limites | Constats 1.6 (C10, C14) ; lacunes L4, L12 ; registre contradictions |
| C1D | Décisions, preuves, rapports, registres, contestations, questions, historique | Constats 1.5 ; lacunes L1, L7, L8, Q8, Q9, Q10 |
| C1E | Versions et évolution : consolider les règles SemVer déjà approuvées (A15) ; distinguer versions protocole/schéma et révisions documentaires | Constats 1.2 ; divergences T10, T11 ; lacunes L3 |
| C1F | Git/GitHub : tâches atomiques, branches, commits conventionnels, audit, acceptation, autorisation de fusion, vérification post-fusion | Constats 1.1 (absence .gitignore, R5) ; lacunes L24 |

### 3.2 Traitement des divergences de C0

Chaque divergence identifiée en C0 doit faire l'objet en C1 d'une proposition documentée (sans correction silencieuse) :

- D1-D20 (doublons) → désigner une source principale unique par information
- C1-C25 (contradictions) → arbitrer chaque contradiction par décision VALIDATOR
- T1-T15 (divergences terminologiques) → harmoniser la terminologie ou documenter la coexistence
- C24 (state.json v1.0 vs v2.0) → définir ou écarter formellement la procédure de migration

### 3.3 Priorités

**Priorité haute** :
1. Registre des décisions (`decision_log.md`) — lacune L1, bloquante pour la traçabilité des décisions
2. Validation JSON Schema de `state.json` — lacune L2, bloquante pour la vérifiabilité de l'état
3. Procédure de migration v1.0 → v2.0 — lacune L3, A16 différé
4. Arbitrage des contradictions bloquantes C1, C3, C5 — impact direct sur la rédaction C1

**Priorité moyenne** :
5. Matrice complète des permissions — lacune L4
6. Protection de `main` (T5) — lacune L12, C29
7. Tests T1 à T5 — lacune L11

**Priorité basse** :
8. Documentation des fichiers `.gitignore` / ignorés — lacune L24, réserve R5
9. Harmonisation des trois listes de catégories de versions — divergence T10/T11, A14

### 3.4 Contraintes pour C1

- Respecter la contrainte lecture seule de C0 : aucune modification de document source sans décision HVG0 distincte et nouveau mandat
- Ne pas fusionner vers `main` sans décision HVG0 distincte du VALIDATOR
- Ne pas modifier `state.json` ni `state.md` (GC-13)
- Ne pas attribuer d'autorité normative aux sources historiques (réserve R3)
- Ne pas déduire HVG1 : seule une proposition de périmètre est produite ici
- Maintenir la distinction entre état de référence C0 (markdown, figé) et `state.json`/`state.md` (réserve R4)

### 3.5 Lien vers les constats C0

Ce périmètre C1 est directement dérivé des constats C0 : inventaire (section 1.1), métadonnées (1.2), classification (1.3), statuts (1.4), décisions (1.5), doublons/contradictions/divergences (1.6), sources historiques (1.7), lacunes (2.1), questions ouvertes (2.2), divergences non résolues (2.3), dépendances non résolues (2.4).

---
*Fin du rapport C0. Aucune correction spontanée des documents sources. Distinct de l'état de référence (référence_c0.md) et des preuves annexes.*