# C1.1 — Traitement des divergences C0 (propositions documentées)

**Chantier** : C1 — Consolidation normative et documentaire  
**Tâche** : C1.1 — Traiter divergences C0 par propositions documentées (sans correction silencieuse)  
**Transition** : TR-2026-0002 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C1-consolide-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C1` (alignée sur `main`, intègre les 10 commits C0)  
**Contrainte** : Pas de correction silencieuse des documents sources (GC-31) — uniquement signalement et propositions pour le VALIDATOR

---

## 1. Vérification état Git (prérequis C1.1)

| Vérification | Résultat | Preuve |
|---|---|---|
| Branche courante | `dev_C1` | `git branch` |
| Alignement avec `main` | `dev_C1` = `main` (commit `a03794b`) | `git log --oneline` |
| Intégration C0 dans `main` | 10 commits C0 présents sur `main` | `git log --oneline main` |
| C1-A à C1-F terminés | Commits `7da7ebc`, `cc6ebc5`, `fbfc5d1`, `56603d5`, `27fa6cc`, `a03794b` | `git log --oneline -6` |
| Reçu de transition C1 déposé | `livrables/C1/transition/recu_transition_C1.md` | Commit `7da7ebc` |

---

## 2. Objectif de C1.1

Ce livrable convertit les divergences identifiées en C0 (20 doublons, 25 contradictions, 15 divergences terminologiques + 14 confusions terminologiques) en **propositions documentées** destinées au VALIDATOR.

**Règle fondamentale** : aucune divergence n'est corrigée silencieusement dans les documents sources. Chaque divergence fait l'objet d'une proposition documentée qui reste en attente d'arbitrage par le VALIDATOR.

---

## 3. Méthode

Pour chaque divergence C0, ce registre consigne :

| Champ | Contenu |
|---|---|
| ID | Identifiant de la divergence (D1-D20, C1-C25, T1-T15, CF-1-CF-14) |
| Description | Nature de la divergence |
| Documents impliqués | Fichiers concernés |
| Proposition de traitement | Solution proposée (non appliquée, soumise au VALIDATOR) |
| Acteur décisionnel | VALIDATOR |
| Statut | `À ARBITRER` (en attente de décision VALIDATOR) |

---

## 4. Traitement des 20 doublons (D1-D20)

Les doublons sont des informations présentes dans plusieurs documents sans source principale désignée. La proposition consiste à désigner une source principale unique par information.

| ID | Information dupliquée | Proposition de traitement | Source principale proposée | Statut |
|---|---|---|---|---|
| D1 | Objet, acronyme, définition d'AKORIS | Désigner une source unique pour la définition d'AKORIS | `README.md` + `terminology.md` | À ARBITRER |
| D2 | Rôles et responsabilités | Désigner une source unique pour les rôles | `governance_core.md` | À ARBITRER |
| D3 | Sources de référence uniques | Désigner une source unique pour les sources uniques | `reference/document_map.md` | À ARBITRER |
| D4 | États projet/sprint/transition | Désigner une source unique pour les états | `state_model.md` + `transition_policy.md` | À ARBITRER |
| D5 | Schéma `state.json` | Désigner une source unique pour le schéma state.json | `state_model.md` + `state.schema.json` | À ARBITRER |
| D6 | Arborescence projet | Désigner une source unique pour l'arborescence | `document_map.md` | À ARBITRER |
| D7 | Checkpoints CP1/CP2/CP3 | Désigner une source unique pour les checkpoints | `getting_started.md` | À ARBITRER |
| D8 | Cycle nominal de sprint | Désigner une source unique pour le cycle de sprint | `getting_started.md` | À ARBITRER |
| D9 | Règles Git / fusion `main` | Désigner une source unique pour les règles Git | `permission_policy.md` | À ARBITRER |
| D10 | Valeurs et conditions de décision | Désigner une source unique pour les valeurs de décision | `decision_policy.md` | À ARBITRER |
| D11 | Contenu des rapports | Désigner une source unique pour le contenu des rapports | `templates/*` | À ARBITRER |
| D12 | Ordre d'implémentation | Désigner une source unique pour l'ordre d'implémentation | `00_cartographie.md` (C0) | À ARBITRER |
| D13 | Architecture cible | Désigner une source unique pour l'architecture cible | `00_cartographie.md` (C0) | À ARBITRER |
| D14 | Permissions | Désigner une source unique pour les permissions | `permission_policy.md` + `implementations/opencode/agent_permissions.md` | À ARBITRER |
| D15 | Reçu de transition | Désigner une source unique pour le reçu de transition | `transition_policy.md` | À ARBITRER |
| D16 | Règle de non-duplication | Désigner une source unique pour la règle de non-duplication | `governance_core.md` (GC-50, GC-51) | À ARBITRER |
| D17 | Séparation `state.json` / `state.md` | Désigner une source unique pour la séparation source/vue | `state_model.md` §1 | À ARBITRER |
| D18 | Cinq valeurs de décision | Désigner une source unique pour l'énumération des 5 valeurs | `decision_policy.md` §3 | À ARBITRER |
| D19 | Règle GC-13 / GC-14 (BUILDER) | Désigner une source unique pour les contraintes BUILDER | `governance_core.md` GC-13/GC-14 | À ARBITRER |
| D20 | Autorité finale du VALIDATOR | Désigner une source unique pour l'autorité VALIDATOR | `governance_core.md` GC-04 | À ARBITRER |

> **Doublons les plus coûteux (C0 §4)** : D2, D3, D5, D10, D14 — toute évolution y crée immédiatement une divergence. À traiter en priorité dans C1.

---

## 5. Traitement des 25 contradictions (C1-C25)

Les contradictions sont des instructions opposées dans différents documents. Chaque contradiction fait l'objet d'une proposition d'arbitrage.

### 5.1 Contradictions bloquantes (C1-C5)

| ID | Contradiction | Proposition de traitement | Acteur décisionnel | Statut |
|---|---|---|---|---|
| C1 | Valeurs de décision : 3 ou 5 ? | Trancher définitivement : 5 valeurs avec underscore (A1 déjà tranché) | VALIDATOR | À confirmer (A1 tranché) |
| C2 | Orthographe canonique : espaces vs underscore | Trancher : underscore uniquement (A1 déjà tranché) | VALIDATOR | À confirmer (A1 tranché) |
| C3 | Deux schémas `state.json` incompatibles (v1.0 plat vs v2.0 imbriqué) | Trancher : v2.0 normative (A2 déjà tranché), documenter l'écart v1.0 | VALIDATOR | À confirmer (A2 tranché) |
| C4 | Profils absents de l'opérationnel | Trancher : profils activés (A3 déjà tranché) | VALIDATOR | À confirmer (A3 tranché) |
| C5 | Trois chemins racine pour le socle | Trancher le chemin racine canonique (`documentation/` vs `governance/` vs `protocol/`) | VALIDATOR | À ARBITRER (A4 partiellement tranché) |

### 5.2 Contradictions majeures (C6-C11)

| ID | Contradiction | Proposition de traitement | Acteur décisionnel | Statut |
|---|---|---|---|---|
| C6 | Collision `README.md` (projet vs documentation) | Trancher : `documentation/README.md` pour la documentation, README racine pour le projet (A4 déjà tranché) | VALIDATOR | À confirmer (A4 tranché) |
| C7 | Cycle de transition : 9 ou 5 états ? | Trancher : 9 états pour le cadre v2 (A2 déjà tranché) | VALIDATOR | À confirmer (A2 tranché) |
| C8 | Preuve de consommation d'une autorisation | Confirmer : le reçu de transition est un composant central (C8 révisé, `transition_policy.md`) | VALIDATOR | À confirmer (C24 tranché) |
| C9 | Cadre générique ou lié à l'outil | Confirmé : socle agnostique, OpenCode implémentation de référence (A8 déjà tranché) | VALIDATOR | À confirmer (A8 tranché) |
| C10 | Niveau réel des permissions | Clarifier : `permission_policy.md` doit porter une procédure de vérification effective (C10 révisé) | VALIDATOR | À ARBITRER (lié à C1-C, C1-F, M3) |
| C11 | Liste des rôles : 3 ou 4 ? | Trancher : 4 rôles, le 4e documentaire hors boucle (A5 déjà tranché) | VALIDATOR | À confirmer (A5 tranché) |

### 5.3 Contradictions mineures (C12-C25)

| ID | Contradiction | Proposition de traitement | Acteur décisionnel | Statut |
|---|---|---|---|---|
| C12 | Tables des sources divergentes (use_cases/incidents) | Unifier les tables des sources dans `document_map.md` §5 | VALIDATOR | À ARBITRER |
| C13 | Emplacements des audits de préparation | Confirmer : `docs/governance/readiness/` doctrinal, rapport pilote conservé (C13 déjà tranché) | VALIDATOR | À confirmer (C13 tranché) |
| C14 | Jeu de modèles : 7 (cible) vs 4 (pilote) | Déclarer `debt_report_template.md` absent de la cible ou l'ajouter | VALIDATOR | À ARBITRER |
| C15 | Versionnement ambigu (1.0 vs 2.0) | Clarifier : protocole 1.0, schéma 2.0, distincts (A7, A15 déjà tranchés) | VALIDATOR | À confirmer (A7/A15 tranchés) |
| C16 | Charge 35-160h dans document doctrinal | Déplacer le contenu de planification vers un document de planification dédié | VALIDATOR | À ARBITRER |
| C17 | Ordres de rédaction divergents (F2 §11 vs F1 §8) | Unifier l'ordre de rédaction dans le plan de consolidation | VALIDATOR | À ARBITRER |
| C18 | 10 décisions structurantes sans identifiant ni registre | Créer `reference/decision_log.md` (L1 de C0) | VALIDATOR | À ARBITRER (lié à C1-D) |
| C19 | Mot « audit » ambigu (préparation vs sprint) | Confirmer : deux contrôles distincts (C19 déjà tranché) | VALIDATOR | À confirmer (C19 tranché) |
| C20 | Maquette V0 incomplète (omet profile_*.md, templates/, reference/) | Confirmer la correction §8.1 de la cartographie | VALIDATOR | À ARBITRER |
| C21 | Double lecture du statut de `00_cartographie.md` | Trancher le statut définitif (PROPOSITION vs TRAVAIL) | VALIDATOR | À ARBITRER |
| C22 | En-tête de `document_map.md` fixé à v0.4 malgré évolution | Mettre à jour l'en-tête ou documenter le gel explicite | VALIDATOR | À ARBITRER |
| C23 | Décompte des 34 documents divergeant | Reconcilier photographie historique et état actuel | VALIDATOR | À ARBITRER |
| C24 | state.json v2.0 (dépôt) vs v1.0 (pilote) sans migration | Définir ou écarter formellement la procédure de migration (A16 différé) | VALIDATOR | À ARBITRER (A16) |
| C25 | Relation état / version de profil non modélisée | Définir la relation ou déclarer `À ARBITRER` | VALIDATOR | À ARBITRER (lié à C1-E) |

---

## 6. Traitement des 15 divergences terminologiques (T1-T15)

Les divergences terminologiques sont des mêmes concepts nommés différemment, ou des mêmes noms pour des concepts différents.

| ID | Concept | Terme A | Terme B | Documents impliqués | Proposition de traitement | Statut |
|---|---|---|---|---|---|---|
| T1 | Valeur « go avec réserves » | `GO WITH RESERVES` | `GO_WITH_RESERVES` | `getting_started.md` vs `decision_policy.md` | Trancher : underscore uniquement (A1) | À confirmer |
| T2 | Nombre de valeurs de décision | 3 (pilote v1) | 5 (cadre v2) | `getting_started.md` vs `decision_policy.md` | Trancher : 5 valeurs (A1) | À confirmer |
| T3 | Champ d'identification de transition | `token` (v1) | `transition_id` (v2) | `AKORIS_consolide.md` vs `state_model.md` | Trancher : `transition_id` (C22) | À confirmer |
| T4 | Activité « audit » | Audit de préparation | Audit de sprint | `AKORIS_consolide.md` §11 | Confirmer : deux contrôles distincts (C19) | À confirmer |
| T5 | Chemin `README.md` | README projet | README documentation | `AKORIS_architecture_documentaire.md` vs `akoris_documentation_builder.md` | Trancher : `documentation/README.md` (A4) | À confirmer |
| T6 | Nombre d'états de transition | 5 (pilote) | 9 (cadre v2) | `getting_started.md` vs `AKORIS_consolide.md` | Trancher : 9 états (A2) | À confirmer |
| T7 | Structure de `state.json` | v1.0 plat | v2.0 imbriqué | `AKORIS_consolide.md` vs `state_model.md` | Trancher : v2.0 (A2) | À confirmer |
| T8 | Chemins racine du socle | `governance/` | `protocol/` | F3 vs F2 (y compris `documentation/protocol/` de F1) | Trancher le chemin canonique (A4) | À ARBITRER |
| T9 | Liste des rôles | 3 agents + VALIDATOR | 4 rôles | `AKORIS_consolide.md` vs `akoris_documentation_builder.md` | Trancher : 4 rôles (A5) | À confirmer |
| T10 | Catégories de versions | 4 axes (CART) | 5 catégories (A7) | `00_cartographie.md` vs `versioning_policy.md` | Confirmer A7 comme référence (A14) | À confirmer |
| T11 | Éléments à versionner | 8 éléments (F2) | 5 catégories (A7) | `AKORIS_architecture_documentaire.md` §16 vs `versioning_policy.md` | Confirmer A7 comme référence (A14) | À confirmer |
| T12 | Version du profil | Champ dans `state.json` | Aucun champ (en-tête du document) | `state.json` vs `versioning_policy.md` | Confirmer : aucun champ (A10) | À confirmer |
| T13 | Reçu de transition | Pas de mécanisme (F3) | Reçu obligatoire (`getting_started`) | `AKORIS_consolide.md` vs `getting_started.md` | Confirmer : reçu composant central (C8 révisé) | À confirmer |
| T14 | Niveau des permissions | Procédural (F3) | Preuve technique partielle (frontmatter) | `AKORIS_consolide.md` vs `.opencode/agents/` | Clarifier : procédure de vérification (C10 révisé) | À ARBITRER |
| T15 | Emplacement revues de préparation | `docs/governance/readiness/` | Rapport pilote historique | `AKORIS_architecture_documentaire.md` vs pilote | Confirmer : emplacement doctrinal (C13) | À confirmer |

---

## 7. Traitement des 14 confusions terminologiques (CF-1-CF-14)

Ces confusions sont documentées dans `terminology.md` §8 comme des distinctions à ne pas brouiller. Elles ne sont pas des divergences entre documents, mais des points de vigilance à maintenir dans C1.

| # | À ne pas confondre | Avec | Action C1 |
|---|---|---|---|
| CF-1 | Rapport | Preuve | Maintenir la distinction dans tous les documents C1 |
| CF-2 | Recommandation | Décision | Maintenir la distinction (GC-05, GC-21) |
| CF-3 | Autorisation | Consommation | Maintenir la distinction (TP §3) |
| CF-4 | Achèvement | Acceptation | Maintenir la distinction (TP §3) |
| CF-5 | Réserve | Anomalie | Maintenir la distinction (DP §7) |
| CF-6 | Profil | Implémentation | Maintenir la distinction (T §8) |
| CF-7 | Revue de préparation | Audit de sprint | Maintenir la distinction (C19) |
| CF-8 | Changement | Correction | Maintenir la distinction (T §8) |
| CF-9 | Jeton | Preuve cryptographique | Maintenir la distinction (GC-48, C22) |
| CF-10 | Permission déclarée | Permission appliquée | Maintenir la distinction (GC-36) |
| CF-11 | `state.json` | `state.md` | Maintenir la distinction (réserve R4) |
| CF-12 | `NOT_CHECKED` | `PASS` | Maintenir la distinction (GC-25) |
| CF-13 | `declared_only` | Vérifié | Maintenir la distinction (DP §5.1) |
| CF-14 | Document de référence | Document produit | Maintenir la distinction (T §8, réserve R3) |

> **Aucune action corrective n'est requise** pour les confusions CF-1 à CF-14 : elles sont déjà documentées dans `terminology.md` §8. C1 doit simplement veiller à ce que les nouveaux documents C1 respectent ces distinctions.

---

## 8. Synthèse des propositions par priorité

| Priorité | Divergences concernées | Nombre | Justification |
|---|---|---|---|
| **Haute** | D2, D3, D5, D10, D14 (doublons coûteux) ; C1, C2, C3, C4, C5 (contradictions bloquantes) | 10 | Toute évolution y crée immédiatement une divergence ; bloquent la rédaction C1 |
| **Moyenne** | C6-C11 (contradictions majeures) ; T1-T7, T9, T12, T13, T15 (divergences déjà tranchées par A1-A8, C24, C13, C19) | 13 | Dépendent d'arbitrages déjà tranchés (A1-A8) mais nécessitent confirmation formelle |
| **Basse** | C12-C25 (contradictions mineures) ; T8, T10, T11, T14 (divergences à arbitrer) ; CF-1-CF-14 (confusions) | 43 | À traiter après les priorités haute et moyenne |

> **Total** : 20 doublons + 25 contradictions + 15 divergences terminologiques + 14 confusions = 74 items à traiter par propositions documentées.

---

## 9. Règle de non-correction silencieuse (GC-31)

Conformément à **GC-31** : *« Toute divergence entre documents est signalée. Elle n'est jamais corrigée silencieusement. »*

| Principe | Application dans C1.1 |
|---|---|
| Aucun document source n'est modifié | Aucune modification de `_sources/*`, `protocol/*`, `reference/*`, `templates/*`, `prompts/*`, `implementations/*` |
| Chaque divergence fait l'objet d'une proposition | Toutes les divergences ci-dessus ont une proposition de traitement |
| Chaque proposition est soumise au VALIDATOR | Le statut de chaque proposition est `À ARBITRER` |
| Le VALIDATOR tranche ou rejette | Seule une décision VALIDATOR tracée peut trancher une divergence |

---

## 10. Preuves attendues pour C1.1

| Preuve | Référence | Statut |
|---|---|---|
| État Git sur dev_C1 | `git branch`, `git log --oneline` | `directly_verified` |
| Registres C0 (doublons, contradictions, divergences) | `livrables/C0/registres/` | `directly_verified` |
| Propositions de traitement C1.1 | Ce document (`traitement_divergences_C0.md`) | Produit |
| Règle GC-31 respectée | Aucun document source modifié | `directly_verified` (état Git vérifié) |

---

## 11. Suite de C1

Après C1.1, les tâches restantes dans le mandat C1 :

| Tâche | Description | Livrable attendu | Dépend de C1.1 |
|---|---|---|---|
| C1.3 | Distinction MUST/SHOULD/MAY/OUT OF SCOPE | Dans les documents du corpus | Non |
| C1.6 | Préparation audit C1 | `livrables/C1/rapport/` | Oui (règles Git, versionning, permissions, divergences) |
| C1.7 | Rapport C1 + HVG1 | `livrables/C1/rapport/rapport_C1.md` | Oui (toutes) |

---
*Fin de C1.1. 74 divergences C0 converties en propositions documentées (20 doublons, 25 contradictions, 15 divergences terminologiques, 14 confusions). Aucune correction silencieuse appliquée (GC-31 respectée). Toutes les propositions sont en attente d'arbitrage par le VALIDATOR (`À ARBITRER`).*