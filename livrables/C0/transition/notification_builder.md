# Notification de transition vers BUILDER DOCUMENTAIRE — Chantier C0

**Transition** : TR-2026-0001  
**Statut** : `authorized` → passage à `consumé` upon received deposition  
**Mandat** : C0-revise-v1 (MANDAT C0 RÉVISE — Inventaire et état de référence du corpus)  
**Date de notification** : 2026-11-24  
**Émetteur** : ORCHESTRATOR  
**Destinataire** : BUILDER DOCUMENTAIRE  

## 1. Branche de travail

- **Branche** : `dev_C0` (créée depuis `main` vérifié)
- **Commit de référence** : `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea` — `docs(init): import existing AKORIS corpus`
- **État courant** : `dev_C0`, issu du commit initial `main`
- **Fichiers présents** : `state.json`, `livrables/C0/` et sous-répertoires (tous nouveaux, non modifications de sources)

## 2. Réception de transition (MANDATORY BEFORE PRODUCTION)

Conformément à la condition VALIDATOR : **"Le BUILDER dépose son reçu de transition avant toute production."**

Le reçu de transition a été préparé et documenté à l'adresse suivante :
- **Fichier** : `livrables/C0/transition/recu_transition_C0.md`
- **Contenu** : Réception des conditions du mandat C0-revise-v1, incluant :
  - Acceptation des 5 réserves (R1 à R5)
  - Engagement de lecture seule sur le corpus source
  - Engagement de produire les livrables C0 dans l'espace dédié `C:\Methode_AKORIS\livrables\C0\`
  - Connaissance des autorisations Git distinctes (création commits sur `dev_C0`, pas de fusion vers `main` sans décision HVG0 distincte)
  - Périmètre C0 et exclusions notés

**Action requise au BUILDER** : Prendre connaissance du fichier `recu_transition_C0.md` et considérer le reçu comme déposé. C'est l'étape préalable obligatoire avant de commencer la production des livrables C0 (tâches C0-01 à C0-12).

Après cette étape, l'état de `state.json` `transition.status` sera considéré comme `consumé` (il l'est déjà), et le BUILDER peut commencer l'exécution des tâches C0.

## 3. Mandat C0 — 12 tâches à exécuter

Le BUILDER s'exécute sur branche `dev_C0` et produit les 11 livrables C0 suivants (ordre suggéré) :

| Tâche | Description sommaire |
|---|---|
| **C0-01** | Vérifier dépôt, branche, commit initial et état Git |
| **C0-02** | Inventorier fichiers et répertoires |
| **C0-03** | Relever métadonnées de chaque document |
| **C0-04** | Classer documents par nature |
| **C0-05** | Identifier décisions validées et preuves |
| **C0-06** | Identifier doublons, contradictions, divergences |
| **C0-07** | Identifier lacunes, questions et dépendances |
| **C0-08** | Examiner sources historiques et relations |
| **C0-09** | Distinguer statuts documentaires |
| **C0-10** | Construire cartographie et état de référence |
| **C0-11** | Préparer rapport C0 et recommandations |
| **C0-12** | Proposer périmètre C1 au VALIDATOR |

Chaque tâche possède : descriptif détaillé, unités actionnables, critères d'acceptation, preuves attendues, contraintes (notamment : **aucune modification des documents sources**).

## 4. Règles Git et autorisations pendant C0

| Opération | Autorisation | Conditions |
|---|---|---|
| Lecture corpus source | Oui | Interdite aucune restriction |
| Création commits sur `dev_C0` | Oui | Unités C0-01 à C0-12 ; chaque commit lié à son identifiant tâche |
| Push sur `dev_C0` | Oui | Dans cadre C0 |
| Modification documents sources | **Non** | Contrainte lecture seule absolue |
| Création branche supplémentaires | Non | Non requis |
| Fusion vers `main` | **Non** | Décision HVG0 distincte requise |
| Modification `state.json` | **Non** | Sauf par l'orchestrator pour mise à jour transition/réserves (GC-13) |

**Règle GC-14** : BUILDER ne fusionne jamais directement vers `main` et n'étend pas silencieusement le périmètre.

## 5. Conditions d'arrêt pour le BUILDER

Arrêt immédiat en cas de :
- Tentative de modification de document source
- Demande hors périmètre (correction de source, fusion dans main, démarrage C1)
- Préuve critique manquante sur critère obligatoire (→ `HOLD` selon DP)
- Anomalie S0 ou S1 détectée (→ `NO_GO`)
- Divergence état/reçu non résolue

## 6. Premier démarrage : Tâche C0-01

Le BUILDER commence par :
1. Vérifier l'état Git sur `dev_C0` (doit refléter `main` au commit initial)
2. Documenter l'état dans `livrables/C0/inventaire/etat_git.md`
3. Consigner les constats dans le registre C0

**Preuves attendues pour C0-01** :
- `etat_git.md` : état de la working tree, branche confirmée, commit initial noté
- Aucun fichier source modifié par rapport au commit initial

## 7. Rappel des 5 réserves à suivre (R1 à R5)

| Réserve | Consigne C0 |
|---|---|
| R1 | Frontière C0-07 / C0-09 — distinguer lacunes/questions/dépendances vs statuts documentaires sans chevauchement |
| R2 | Classification multi-catégories — catégorie principale + secondaires le cas échéant, avec justification |
| R3 | Attribution autorité sources historiques (C0-08) — ne pas attribuer d'autorité normative par défaut |
| R4 | État de référence vs state.json/state.md — état de référence C0 markdown autonome dans `livrables/C0/reference/` |
| R5 | Fichiers .gitignore et ignorés — politique d'inclusion/exclusion à documenter en début d'inventaire |

## 8. Fin de mandat C0 et HVG0-B

- **Décision HVG0-B** : Après production de tous les livrables C0 et audit, le VALIDATOR prononcera la décision finale (GO/NO_GO/GO_WITH_RESERVES pour la transition C0→C1).
- **Fusion vers main** : Uniquement après décision HVG0-B distincte du VALIDATOR.
- **Règle GC-07** : L'acceptation d'un sprint n'autorise ni fusion, ni déploiement, ni C1.

---

**Notification générée le 24 novembre 2026 suite à la décision VALIDATOR GO_WITH_RESERVES (D-001-HVG0) de la transition TR-2026-0001.**

**Prochaine action BUILDER** : Prendre connaissance de `recu_transition_C0.md`, considérer le reçu comme déposé, puis commencer la tâche C0-01 (vérification Git et état des lieux).