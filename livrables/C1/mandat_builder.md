# Mandat opérationnel BUILDER DOCUMENTAIRE — Chantier C1

**Transition** : TR-2026-0002  
**Statut** : `authorized` → `in_progress` (après dépôt reçu)  
**Mandat** : C1-consolide-v1 (Mandat C1 — Consolidation normative et documentaire)  
**Décision VALIDATOR** : GO_WITH_RESERVES (HVG0-B), date 24 nov. 2026  
**Auteur VALIDATOR** : Non précisé (acte humain)  
**Branche** : `dev_C1` (créée depuis `main` vérifié, intègre C0)  

## 1. mandat et périmètre

- **Objet** : Consolidation normative et documentaire du corpus AKORIS suite à l'inventaire C0
- **Périmètre inclus** :
  - Hiérarchie documentaire et statuts (C1A)
  - Modèle d'état `state.json`, `state.md` (C1B)
  - Permissions, rôles, périmètres (C1C)
  - Registres décisions, preuves, rapports (C1D)
  - Versions SemVer, protocole/schéma (C1E)
  - Git/GitHub atomique (C1F)
  - Traitement divergences C0 par propositions (C1.1)
  - Distinction MUST/SHOULD/MAY/OUT OF SCOPE (C1.3, C1.4)
  - Vérification cohérence croisée (C1.5)
  - Audit des changements (C1.6, C1.7)
- **Périmètre exclu** :
  - Modifications en dehors du périmètre C1 défini
  - Fusion dans `main` sans décision HVG1 distincte
  - Corrections spontanées des documents sources
  - Attribution d'autorité normative non justifiée

## 2. Unités exécutables (décomposition C1)

Le BUILDER s'exécute sur branche `dev_C1` et produit les livrables C1 suivants :

| Tâche | Description sommaire |
|---|---|
| **C1-A** | Hiérarchie documentaire : établirarchie des catégories normatives, opérationnelles, explicatives, historiques ; prévalence des sources |
| **C1-B** | Modèle d'état : recréer/adapter `state.json` et `state.md` pour intégrer résultats C0, états de transition, reçus, cycle de vie |
| **C1-C** | Permissions, rôles : harmoniser permissions et rôles entre documents, définir interdictions, exceptions, limites |
| **C1-D** | Registres décisions : consolider les décisions C0 (`D-VAL-*` + D-001-HVG0), registrar nouvelles décisions, lier preuves |
| **C1-E** | Versionning : appliquer SemVer aux documents, distinguer versions protocole/schéma, révisions documentaires |
| **C1-F** | Git/GitHub : tasks atomiques, branches dédiées, commits conventionnels, audit, acceptation, fusion post-HVG1 |
| **C1.1** | Traiter divergences C0 : convertir 20 doublons, 25 contradictions, 15 divergences en propositions documentées |
| **C1.3** | Distinguer `MUST`, `SHOULD`, `MAY` et `OUT OF SCOPE` dans tous les documents du corpus |
| **C1.4** | Modifier les documents uniquement dans périmètre autorisé (lecture seule levée sélective) |
| **C1.5** | Vérifier cohérence croisée : état/mandat/reçu/rapport/état Git |
| **C1.6** | Faire auditer les changements (préparer mandat AUDITOR C1) |
| **C1.7** | Soumettre rapport et réserves au VALIDATOR ; obtenir HVG1 |

## 3. Règles Git et autorisations pendant C1

| Opération | Autorisation | Conditions |
|---|---|---|
| Lecture corpus source | Oui | Interdite aucune restriction |
| Création commits sur `dev_C1` | Oui | Unités C1-A à C1.7 ; chaque commit lié à son identifiant tâche |
| Push sur `dev_C1` | Oui | Dans cadre C1 |
| Modification documents sources | **Autorisée** | Uniquement dans périmètre C1 défini ; pas de hors-périmètre |
| Fusion vers `main` | **Non** | Sans décision HVG1 distincte du VALIDATOR |
| Modification `state.json` | **Autorisée** | Dans cadre C1B (modèle d'état) ; pas de modifications arbitraires |

**Règle GC-14** : BUILDER ne fusionne jamais directement vers `main` et n'étend pas silencieusement le périmètre.

## 4. Conditions d'arrêt pour le BUILDER

Arrêt immédiat en cas de :
- Tentative de modification de document hors périmètre C1
- Demande hors périmètre (fusion main sans HVG1, démarrage C2)
- Preuve critique manquante sur critère obligatoire (→ `HOLD` selon DP)
- Anomalie S0 ou S1 détectée (→ `NO_GO`)
- Divergence état/reçu non résolue

## 5. Première tâche : C1-A — Hiérarchie documentaire

Le BUILDER commence par :
1. Vérifier l'état Git sur `dev_C1` (doit refléter `main` actuel avec C0)
2. Élaborer l'hierarchie documentaire : classifier les fichiers en catégories normatives/opérationnelles/explicatives/historiques avec prévalence des sources
3. Consigner dans `livrables/C1/hierarchie_doc/hiérarchie_doc.md`
4. Distinguer autorités sources sur certains documents (levée partielle réserve R3)

**Preuves attendues pour C1-A** :
- `livrables/C1/hierarchie_doc/hiérarchie_doc.md` : classification et prévalence des sources
- Note sur levée réserve R3 (autorité sources historiques)

## 5. Réserves C1 à suivre (issues des R1-R5 de C0)

| Réserve C0 | Action C1 correspondante | Statut |
|---|---|---|
| **R1** | H1 : Clarifier frontière C0-07 / C0-09 | Ouverte, suivie |
| **R2** | H2 : Formaliser classification multi-catégories | Ouverte, suivie |
| **R3** | H3 : Valider autorité sources historiques (niveau 5 pilote) | Ouverte, nécessite clarification |
| **R4** | H4 : Confirmer distinction état de référence vs state.json/state.md | Ouverte, suivie |
| **R5** | H5 : Documenter politique .gitignore et fichiers ignorés | Ouverte, suivie |

## 6. Actions prioritaires C1 (issues des NC-01 à NC-05)

| Action | Issue | Priorité |
|---|---|---|
| **M1** | Valider schéma `state.schema.json` (4/26 décisions traçabilité moindre) | Élevée |
| **M2** | Porter à 100% documents "Approuvés" (actuellement 3/45 = 6,7%) | Moyenne |
| **M3** | Exécuter tests T1-T5 (non exécutés) et protéger `main` | Élevée |
| **B1** | Documenter politique d'inclusion/exclusion des fichiers (absent .gitignore) | Faible |
| **B2** | Établir règles Git/CI-CD applicables pour C1 | Moyenne |

## 7. Notification

**Notification générée le 24 novembre 2026** suite à la décision VALIDATOR HVG0-B GO_WITH_RESERVES et la mise en place des prérequis C1 (transition TR-2026-0002 dans state.json, current_agent = BUILDER, mandat C1 créé).

Le BUILDER DOCUMENTAIRE peut désormais commencer l'exécution de C1 sur la branche `dev_C1`. La transition est autorisée, le mandat est prêt, et les réserves/actions sont consignées.

**Prochaine action** : Prendre connaissance du mandat, déposer le reçu de transition, et débuter par la tâche **C1-A** (hiérarchie documentaire).

---
*Mandat C1 — Version v1. Prérequis comblés le 24 nov. 2026. ORCHESTRATOR a comblé l'écart signalé par le BUILDER.*