# Mandat opérationnel BUILDER DOCUMENTAIRE — Chantier C0

**Transition** : TR-2026-0001  
**Statut** : `authorized` → `in_progress`  
**Mandat** : C0-revise-v1 (MANDAT C0 RÉVISE — Inventaire et état de référence du corpus)  
**Décision VALIDATOR** : `GO_WITH_RESERVES` (HVG0), date 2026-11-24  
**Auteur VALIDATOR** : Non précisé ici (acte humain)  

## 1. mandat et périmètre

- **Objet** : Inventaire et état de référence du corpus AKORIS (12 tâches C0-01 à C0-12)
- **Périmètre inclus** :
  - Inventaire complet de `C:\Methode_AKORIS` (racine + _sources, implementations, prompts, protocol, reference, templates)
  - Relevé métadonnées par document (rôle, statut, version, date, relations — avec valeurs `inconnu`/`non indiqué`/`non vérifiable`/`sans objet` le cas échéant)
  - Classification par nature (normatifs, opérationnels, explicatifs, historiques/sources — catégorie principale + secondaires le cas échéant avec justification)
  - Identification décisions validées et preuves
  - Détection doublons, contradictions, divergences terminologiques (signalement uniquement, aucune correction)
  - Identification lacunes, questions ouvertes, dépendances (sans réponse fournie)
  - Examen sources historiques (relations documentées, pas d'autorité normative par défaut)
  - Distinction statuts documentaires (approuvé / proposé / obsolète / retiré / non vérifié)
  - Cartographie globale + état de référence figé (format Markdown, `référence_c0.md`)
  - Rapport C0 constats + incertitudes + recommandations pour C1
  - Proposition périmètre C1 soumise au VALIDATOR
- **Périmètre exclu** :
  - Toute modification des documents sources (contrainte de lecture seule)
  - Commits, pushes ou fusions dans `main` sans décision HVG0 distincte
  - Corrections spontanées de divergences ou lacunes détectées
  - Attribution d'autorité normative aux sources historiques
  - Décision HVG1 (seuil C1) — seule la proposition de périmètre C1 est produite

## 2. Unités exécutables (décomposition C0)

Chaque tâche C0 est décomposée en unités actionnables par le BUILDER. Le BUILDER ne modifie aucun fichier source existant.

### C0-01 : Vérifier dépôt, branche, commit initial et état Git
- **Unités** : 
  - Exécuter `git status` et documenter l'état
  - Vérifier la présence du commit initial `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea`
  - Noter si la branche `main` est vérifiée et propre
  - Consigner l'état Git dans `livrables/C0/inventaire/etat_git.md`
- **Preuves** : `git status`, référence commit, état working tree
- **Contrainte** : Lecture seule — pas de modification

### C0-02 : Inventorier fichiers et répertoires
- **Unités** :
  - Lister tous les fichiers de `C:\Methode_AKORIS` racine et sous-répertoires
  - Documenter l'arborescence des répertoires
  - Identifier fichiers racine (plan_de_consolidation.md, README.md, changelog.md, 00_cartographie.md)
  - Consigner dans `livrables/C0/inventaire/arborescence_fichiers.md`
- **Preuves** : Arborescence fichiers, compte par répertoire, liste fichiers racine
- **Contrainte** : Pas de modification source

### C0-03 : Relever métadonnées de chaque document
- **Unités** :
  - Pour chaque document de l'inventaire,Extraire : rôle, statut, version, date, relations
  - Utiliser valeurs autorisées : `inconnu`, `non indiqué`, `non vérifiable`, `sans objet`
  - Consigner les métadonnées manquantes par valeur `inconnu` ou `non indiqué` (sans invention)
  - Documenter les relations (liens vers autres documents, dépendances, sources historiques)
  - Consigner dans `livrables/C0/metadonnees/tableau_metadonnees.md`
- **Preuves** : Tableau métadonnées par document, rôles attribués, statuts, versions, références croisées
- **Contrainte** : Pas de modification source ; valeurs manquantes signalées non remplies

### C0-04 : Classer documents par nature
- **Unités** :
  - Classer chaque document dans exactement une catégorie principale : normatifs, opérationnels, explicatifs, historiques/sources
  - Le cas échéant, noter catégories secondaires avec justification
  - Consigner la classification dans `livrables/C0/classification/tableau_classification.md`
- **Preuves** : Tableau classification par catégorie, compte par nature, exemples
- **Contrainte** : Pas de catégorie imposée unique ; multi-classification justifiée

### C0-05 : Identifier décisions validées et preuves
- **Unités** :
  - Repérer toutes les décisions dans le corpus
  - Lier chaque décision à sa preuve (commit, document, jeton)
  - Citer ID décision (ex. D-001), date, auteur, référence
  - Consigner dans `livrables/C0/decisions/registre_decision.md`
  - Distinguer : décision formellement validée / proposition / recommandation / décision non confirmée / historique statut inconnu
- **Preuves** : Registre décisions → preuve, IDs D-001+, dates/auteurs
- **Contrainte** : Pas de décision déduite comme validée ; uniquement éléments accessibles

### C0-06 : Identifier doublons, contradictions, divergences
- **Unités** :
  - Repérer les doublons (contenu identique sous noms différents)
  - Repérer les contradictions (instructions opposées dans différents documents)
  - Repérer les divergences terminologiques (même concept nommé différemment)
  - Consigner chaque cas avec documents impliqués et nature du problème
  - **Absence de correction spontanée** : uniquement signalement et documentation
  - Consigner dans `livrables/C0/registres/registre_doublons.md`, `registre_contradictions.md`, `registre_divergences.md`
- **Preuves** : Registres dédiés (doublons, contradictions, divergences terminologiques)
- **Contrainte** : Aucune modification de document source ; signalement uniquement

### C0-07 : Identifier lacunes, questions et dépendances
- **Unités** :
  - Identifier ce qui n'est pas couvert par le corpus (lacunes)
  - Identifier les questions ouvertes sur le sens ou l'application de certaines règles
  - Identifier les dépendances entre documents ou entre documents et externalités
  - **Ne pas répondre aux questions** ni résoudre les dépendances ; les repérer uniquement
  - Consigner dans `livrables/C0/lacunes/liste_lacunes.md`, `questions_questions.md`, `dependances_carte.md`
- **Preuves** : Liste lacunes (sujets non couverts), questions ouvertes avec contexte, carte dépendances
- **Contrainte** : Aucune réponse fournie ni correction apportée

### C0-08 : Examiner sources historiques et relations avec corpus
- **Unités** :
  - Examiner les sources historiques présentes dans le corpus
  - Comprendre leurs relations avec le corpus actuel
  - Documenter l'origine historique de chaque source importante
  - **Ne pas attribuer automatiquement autorité normative**
  - Noter contexte et périodicité des sources
  - Consigner dans `livrables/C0/sources_historique/ sources_historique.md`
- **Preuves** : Liste sources historiques, notes relations avec corpus, déclaration autorité nulle par défaut, contexte/périodicité
- **Contrainte** : Pas d'attribution d'autorité normative par défaut

### C0-09 : Distinguer statuts documentaires
- **Unités** :
  - Pour chaque document, distinguer et consigner le statut documentaire : approuvé, proposé, obsolète, retiré, non vérifié
  - Consigner la répartition des statuts
  - Le cas échéant, justifier un statut si non évident
  - Consigner dans `livrables/C0/stats_doc/tableau_statu.md`
- **Preuves** : Tableau statut par document, count par statut, justification le cas échéant
- **Contrainte** : Pas de document sans statut attribué ; pas de confusion avec statut de version

### C0-10 : Construire cartographie et état de référence
- **Unités** :
  - Produire cartographie globale du corpus AKORIS
  - Générer état de référence récapitulatif (inventaire + métadonnées + classifications + statuts + décisions + divergences + lacunes)
  - Figer l'état de référence à la date d'achèvement de C0
  - L'état de référence est un livrable autonome Markdown : `livrables/C0/reference/référence_c0.md`
  - Ne pas confondre avec `state.json` (source de vérité opérationnelle) ni `state.md` (vue générée)
- **Preuves** : Document cartographie, fichier état de référence, registre divergences/lacunes/Questions, lien Git état de référence
- **Contrainte** : État de référence figé à date de fin C0 ; distinct de state.json/state.md

### C0-11 : Préparer rapport C0 et recommandations
- **Unités** :
  - Rédiger rapport constats (inventaire, classifications, statuts)
  - Rédiger section incertitudes (lacunes, questions, divergences non résolues)
  - Rédiger section recommandations (périmètre C1, priorités, contraintes)
  - **Aucune correction spontanée** des documents sources dans le rapport
  - Lier le périmètre C1 proposé aux constats C0
  - Consigner dans `livrables/C0/rapport/rapport_C0.md`
  - Preuves annexes (registres, cartes, tableaux) en appendice
- **Preuves** : Rapport texte (Markdown), sections constats/incertitudes/recommandations, preuves en appendice
- **Contrainte** : Pas de correction source dans le rapport ; rapport distinct de l'état de référence et des preuves

### C0-12 : Proposer périmètre C1 au VALIDATOR
- **Unités** :
  - Proposer formellement périmètre C1 cohérent avec résultats de l'inventaire C0
  - Respecter contrainte lecture seule de C0 (aucune modification source)
  - Périmètre assez précis pour décision HVG1
  - Documenter lien vers constats C0 qui justifient le périmètre
  - **Pas de décision HVG1 prise ici** — uniquement proposition
  - Consigner dans `livrables/C0/perimetre-C1/proposition_perimetre_C1.md`
- **Preuves** : Document proposition périmètre C1, lien vers constats C0, reception acknowledgment du VALIDATOR
- **Contrainte** : Pas de décision HVG1 à cette étape ; proposition soumise au VALIDATOR

## 3. Règles Git et opérations autorisées

| Opération | Statut | Conditions |
|---|---|---|
| Lecture corpus source | Autorisée | Aucune restriction |
| Création livrables C0 | Autorisée | Dans `C:\Methode_AKORIS\livrables\C0\` uniquement |
| Modification documents sources | **Interdite** | Contrainte lecture seule absolue |
| Création branche `dev_C0` | Autorisée | Depuis `main` vérifié (commit initial f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea) |
| Commits sur `dev_C0` | Autorisée | Unités C0-01 à C0-12 ; chaque commit cohérent et lié à son identifiant tâche |
| Push `dev_C0` | Autorisée | Dans cadre C0 avant décision HVG0 de fusion |
| Fusion vers `main` | **Interdite** | Sans décision HVG0 distincte du VALIDATOR |
| Modification `state.json` | **Interdite** | BUILDER ne modifie ni state.json, ni state.md (GC-13) |

- **Règle plan directeur** : une livraison par chantier. Les livrables C0 sont produits et commités sur `dev_C0`, mais ne sont fusionnés dans `main` qu'après décision HVG0.
- **Règle GC-13** : BUILDER ne modifie ni `state.json`, ni `state.md`, ni le rapport d'audit, ni une décision validée.
- **Règle GC-14** : BUILDER ne fusionne jamais directement vers `main` et n'étend pas silencieusement le périmètre.

## 4. Conditions d'arrêt pour le BUILDER

Le BUILDER arrête l'action en cas de :
- Mandat modifié sans nouvelle transition autorisée
- Tentative de modification de document source
- Demande hors périmètre (correction de source, fusion dans main, etc.)
- Preuve critique manquante sur un critère obligatoire (→ `HOLD`)
- Anomalie S0 ou S1 détectée (→ `NO_GO`)
- Divergence état/reçu non résolue (→ réconciliation par ORCHESTRATOR selon A2)

## 5. Livrables attendus du BUILDER

À la fin du mandat C0, le BUILDER produit :

1. **Inventaire** (`livrables/C0/inventaire/`) : arborescence, état Git, compte fichiers
2. **Métadonnées** (`livrables/C0/metadonnées/`) : tableau par document avec valeurs `inconnu`/`non indiqué`/`non vérifiable`/`sans objet`
3. **Registres** (`livrables/C0/registres/`) : registres de doublons, contradictions, divergences (signalement uniquement)
4. **Cartographie + État de référence** (`livrables/C0/reference/référence_c0.md`) : état de référence Markdown figé
5. **Classement** (`livrables/C0/classification/`) : tableau par catégorie principale + secondaires le cas échéant
6. **Décisions** (`livrables/C0/decisions/`) : registre avec 5 types de décisions distinguées
7. **Lacunes/Questions/Dépendances** (`livrables/C0/lacunes/`) : listes sans réponse fournie
8. **Sources historiques** (`livrables/C0/sources_historique/`) : examen sans attribution autorité
9. **Statuts documentaires** (`livrables/C0/stats_doc/`) : tableau statut par document
10. **Rapport C0** (`livrables/C0/rapport/rapport_C0.md`) : constats + incertitudes + recommandations C1
11. **Proposition périmètre C1** (`livrables/C0/perimetre-C1/proposition_perimetre_C1.md`) : périmètre soumis VALIDATOR
12. **Réception de transition** (`livrables/C0/transition/reception_transition.md`) : reçue de consommation

## 6. Attestation de consommation de transition

Après avoir produit l'ensemble des livrables C0, le BUILDER dépose un reçu de transition conformément au template `templates/transition_receipt_template.md`. Le reçu atteste :
- Avoir produit tous les livrables C0 conformément au mandat C0-revise-v1
- Avoir respecté la contrainte de lecture seule (aucune modification source)
- Avoir consigné les 5 réserves documentées (R1 à R5)
- Être prêt pour la décision HVG0 distincte (transition vers C1 ou clôture C0)

Le reçu de transition est la preuve consommée qui autorise la étape suivante (décision HVG0 distincte du VALIDATOR sur la transition C0→C1).

---
*Fin du mandat opérationnel BUILDER DOCUMENTAIRE C0. Le BUILDER s'exécute sur branche `dev_C0` depuis `main` vérifié. Aucune modification de documents sources n'est effectuée.*