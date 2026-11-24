# AKORIS — Architecture documentaire et organisation recommandées

## 1. Objet du document

Ce document présente l’organisation recommandée des fichiers et des responsabilités du cadre AKORIS.

Il constitue un plan d’architecture documentaire et opérationnelle. Il ne décrit pas le détail des procédures, des schémas JSON, des contrôles d’audit ou des règles de décision.

AKORIS signifie :

> **Adaptive Knowledge and Orchestrated Reviews for Iterative Systems**

Il s’agit d’un cadre de gouvernance et de contrôle du développement assisté par IA.

---

## 2. Principes d’organisation

- Conserver un socle commun stable.
- Séparer les règles du protocole et l’état du projet.
- Séparer les prompts d’amorçage des politiques détaillées.
- Donner à chaque information une source de référence unique.
- Éviter la duplication entre les documents.
- Adapter le niveau de contrôle au risque du projet.
- Ne charger dans le contexte d’un agent que les documents pertinents.
- Maintenir une séparation claire entre ORCHESTRATOR, BUILDER, AUDITOR et VALIDATOR.
- Ne jamais confondre recommandation, décision et autorisation.
- Conserver les preuves et les décisions importantes.
- Rendre explicites les limites techniques de l’environnement.
- Ne pas produire de documents détaillés avant validation des fondations concernées.

---

## 3. Organisation générale recommandée

```text
project/
│
├── protocol/
│   ├── getting_started.md
│   ├── governance_core.md
│   ├── profile_lite.md
│   ├── profile_standard.md
│   ├── profile_reinforced.md
│   ├── state_model.md
│   ├── decision_policy.md
│   ├── change_control.md
│   ├── audit_policy.md
│   ├── permission_policy.md
│   └── recovery_policy.md
│
├── prompts/
│   ├── akoris_orchestrator_bootstrap.md
│   ├── akoris_builder_bootstrap.md
│   └── akoris_auditor_bootstrap.md
│
├── docs/
│   ├── business_rules/
│   ├── use_cases/
│   ├── requirements/
│   ├── acceptance_criteria/
│   ├── architecture/
│   ├── adr/
│   ├── security/
│   ├── risks/
│   └── governance/
│       ├── changes/
│       ├── incidents/
│       └── readiness/
│
├── sprints/
│   ├── roadmap.md
│   └── sprint_01.md
│
├── templates/
│   ├── orchestrator_report_template.md
│   ├── builder_report_template.md
│   ├── auditor_report_template.md
│   ├── decision_template.md
│   ├── change_request_template.md
│   ├── reserve_template.md
│   └── transition_receipt_template.md
│
├── sprint_report/
├── audit_report/
├── debt_report/
│
├── README.md
├── contexte.md
├── agents.md
├── state.json
├── state.md
├── current_sprint.md
├── .gitignore
└── src/
```

La structure est indicative. Les dossiers doivent être créés uniquement lorsqu’ils apportent une valeur réelle au projet.

---

## 4. Fichiers du protocole

### 4.1. `protocol/getting_started.md`

**Rôle :** manuel complet de référence et guide d’initialisation d’AKORIS.

**Blocs principaux :**

- identité et mandat d’AKORIS ;
- principes fondamentaux ;
- rôles des agents ;
- profils de gouvernance ;
- phases du processus ;
- checkpoints ;
- états et transitions ;
- décisions et preuves ;
- gestion des changements ;
- audit ;
- permissions ;
- Git ;
- récupération et incidents ;
- démarrage du protocole.

Ce fichier est la référence complète. Il ne doit pas nécessairement être injecté intégralement dans chaque prompt opérationnel.

### 4.2. `protocol/governance_core.md`

**Rôle :** socle commun obligatoire à tous les profils.

**Blocs principaux :**

- autorité humaine ;
- séparation des rôles ;
- distinction faits, hypothèses et recommandations ;
- règles de preuve ;
- règles de sécurité ;
- traçabilité ;
- gestion des anomalies ;
- règles générales de transition ;
- règles de non-duplication documentaire.

### 4.3. `protocol/profile_lite.md`

**Rôle :** exigences minimales pour les projets à faible risque.

**Blocs principaux :**

- critères d’utilisation ;
- validations minimales ;
- documentation minimale ;
- audit ciblé ;
- gestion simplifiée des changements ;
- limites du profil.

### 4.4. `protocol/profile_standard.md`

**Rôle :** profil par défaut pour un projet logiciel réel.

**Blocs principaux :**

- checkpoints obligatoires ;
- documents attendus ;
- rôles complets ;
- audit par sprint ;
- gestion des réserves ;
- transitions ;
- validation avant fusion.

### 4.5. `protocol/profile_reinforced.md`

**Rôle :** contrôles renforcés pour les projets sensibles, critiques ou réglementés.

**Blocs principaux :**

- critères de sélection ;
- sécurité ;
- données sensibles ;
- preuves reproductibles ;
- autorisations renforcées ;
- audit approfondi ;
- sauvegarde et rollback ;
- risques résiduels ;
- mesures compensatoires.

### 4.6. `protocol/state_model.md`

**Rôle :** définition des états, transitions et invariants opérationnels.

**Blocs principaux :**

- états du projet ;
- états du sprint ;
- états des transitions ;
- cycle de vie des autorisations ;
- invariants ;
- règles de cohérence ;
- erreurs et reprises ;
- versionnement de l’état.

### 4.7. `protocol/decision_policy.md`

**Rôle :** politique de décision et d’acceptation.

**Blocs principaux :**

- `GO` ;
- `NO_GO` ;
- `GO_WITH_RESERVES` ;
- `HOLD` ;
- niveaux de gravité ;
- types de preuves ;
- critères de décision ;
- traitement des réserves ;
- décision humaine.

### 4.8. `protocol/change_control.md`

**Rôle :** gestion des changements et de leurs impacts.

**Blocs principaux :**

- définition d’un changement ;
- classification ;
- cycle de vie ;
- analyse d’impact ;
- effet sur le mandat ;
- changement urgent ;
- changement de profil ;
- mise à jour des documents.

### 4.9. `protocol/audit_policy.md`

**Rôle :** méthode de vérification indépendante ou contre-vérification.

**Blocs principaux :**

- mandat de l’auditeur ;
- sources de référence ;
- inspection du dépôt ;
- reproduction des tests ;
- classification des preuves ;
- écarts ;
- limites de l’audit ;
- rapport d’audit ;
- désaccords.

### 4.10. `protocol/permission_policy.md`

**Rôle :** distinction entre permissions procédurales, techniques et contrôles a posteriori.

**Blocs principaux :**

- matrice des permissions ;
- moindre privilège ;
- capacités réellement disponibles ;
- protections de `state.json` ;
- protections de `main` ;
- accès aux secrets ;
- violations de permissions ;
- limites de l’environnement partagé.

### 4.11. `protocol/recovery_policy.md`

**Rôle :** gestion des interruptions, incidents, reprises et retours arrière.

**Blocs principaux :**

- blocage ;
- suspension ;
- interruption d’agent ;
- état invalide ;
- perte de rapport ;
- reprise ;
- rollback ;
- incident de sécurité ;
- clôture d’incident.

---

## 5. Prompts d’amorçage des agents

Les prompts d’amorçage sont courts et spécifiques à chaque rôle. Ils orientent l’agent vers les bons documents sans recopier tout le protocole.

### 5.1. `prompts/akoris_orchestrator_bootstrap.md`

**Rôle :** démarrer ORCHESTRATOR dans l’onglet A.

**Blocs principaux :**

- identité et mandat ;
- autorité du VALIDATOR ;
- documents à lire ;
- vérification initiale ;
- interdictions ;
- séquence de démarrage ;
- format de réponse ;
- première question au VALIDATOR.

### 5.2. `prompts/akoris_builder_bootstrap.md`

**Rôle :** démarrer BUILDER dans l’onglet B.

**Blocs principaux :**

- identité et mandat ;
- documents à lire ;
- vérification de la transition ;
- vérification du `GO` ;
- périmètre autorisé ;
- règles d’exécution ;
- tests et commits ;
- rapport attendu ;
- conditions de blocage.

### 5.3. `prompts/akoris_auditor_bootstrap.md`

**Rôle :** démarrer AUDITOR dans l’onglet C.

**Blocs principaux :**

- identité et mandat ;
- documents à lire ;
- vérification de la transition ;
- inspection directe du dépôt ;
- vérification des preuves ;
- tests à reproduire ;
- interdiction de corriger ;
- rapport attendu ;
- gestion des désaccords.

---

## 6. Fichiers de contexte du projet

### 6.1. `README.md`

**Rôle :** point d’entrée humain du projet.

**Contenu général :**

- description ;
- objectif ;
- installation ;
- lancement ;
- tests ;
- organisation ;
- liens vers la documentation.

### 6.2. `contexte.md`

**Rôle :** synthèse centrale du projet.

**Contenu général :**

- vision ;
- objectifs ;
- utilisateurs ;
- périmètre ;
- contraintes ;
- décisions principales ;
- architecture résumée ;
- références vers les documents spécialisés.

Il ne doit pas devenir une copie de toutes les exigences et décisions détaillées.

### 6.3. `agents.md`

**Rôle :** contrats et responsabilités des agents.

**Contenu général :**

- rôles ;
- responsabilités ;
- permissions ;
- interdictions ;
- rapports ;
- transitions ;
- règles de collaboration.

### 6.4. `state.json`

**Rôle :** source de vérité opérationnelle machine.

**Contenu général :**

- version du protocole ;
- profil de gouvernance ;
- état du projet ;
- état du sprint ;
- agent courant ;
- transition active ;
- décisions ;
- blocages ;
- réserves ;
- changements ;
- violations ;
- historique.

### 6.5. `state.md`

**Rôle :** vue lisible générée à partir de `state.json`.

Il ne doit pas être modifié comme une source indépendante.

### 6.6. `current_sprint.md`

**Rôle :** mandat opérationnel du sprint courant.

**Contenu général :**

- objectif ;
- périmètre ;
- tâches ;
- références ;
- dépendances ;
- critères ;
- tests ;
- exclusions ;
- conditions de clôture ;
- rapport attendu.

---

## 7. Documents métier et techniques

### 7.1. `docs/business_rules/`

**Rôle :** règles métier validées.

### 7.2. `docs/use_cases/`

**Rôle :** cas d’utilisation et parcours attendus.

### 7.3. `docs/requirements/`

**Rôle :** exigences fonctionnelles et non fonctionnelles.

### 7.4. `docs/acceptance_criteria/`

**Rôle :** critères vérifiables associés aux exigences et aux tâches.

### 7.5. `docs/architecture/`

**Rôle :** architecture, composants, interactions, flux et frontières.

### 7.6. `docs/adr/`

**Rôle :** décisions techniques structurantes et compromis associés.

### 7.7. `docs/security/`

**Rôle :** exigences, risques et contrôles de sécurité pertinents.

### 7.8. `docs/risks/`

**Rôle :** risques identifiés, impact, probabilité et traitement prévu.

---

## 8. Planification, rapports et registres

### 8.1. `sprints/roadmap.md`

**Rôle :** vision d’ensemble des incréments et de leur ordre.

### 8.2. `sprints/sprint_XX.md`

**Rôle :** description synthétique d’un sprint planifié.

### 8.3. `templates/`

**Rôle :** modèles de rapports, décisions, changements, réserves et reçus.

Les modèles doivent rester génériques et ne pas contenir de décisions de projet.

### 8.4. `sprint_report/`

**Rôle :** rapports produits par BUILDER.

### 8.5. `audit_report/`

**Rôle :** rapports produits par AUDITOR.

### 8.6. `debt_report/`

**Rôle :** réserves acceptées, dette technique et plans de résolution.

### 8.7. `docs/governance/changes/`

**Rôle :** fiches détaillées des changements.

### 8.8. `docs/governance/incidents/`

**Rôle :** incidents de sécurité, de permission, d’état ou d’exécution.

### 8.9. `docs/governance/readiness/`

**Rôle :** audits de préparation et rapports de readiness.

---

## 9. Sources de référence uniques

| Information | Source principale |
|---|---|
| État opérationnel | `state.json` |
| Vue de l’état | `state.md` |
| Mandat courant | `current_sprint.md` |
| Règles métier | `docs/business_rules/` |
| Exigences | `docs/requirements/` |
| Critères de validation | `docs/acceptance_criteria/` |
| Architecture | `docs/architecture/` |
| Décisions techniques | `docs/adr/` |
| Planification | `sprints/` |
| Réserves | `debt_report/` |
| Changements | `docs/governance/changes/` |
| Incidents | `docs/governance/incidents/` |
| Rapport de réalisation | `sprint_report/` |
| Rapport d’audit | `audit_report/` |

En cas de divergence, la source spécialisée prévaut sur une synthèse. La divergence doit être signalée et corrigée selon la procédure appropriée.

---

## 10. Mandats recommandés

AKORIS distingue plusieurs mandats. Chaque mandat doit être explicite, limité et versionné lorsque nécessaire.

### 10.1. Mandat d’initialisation

**Destinataire :** ORCHESTRATOR  
**Objectif :** comprendre le projet et préparer ses fondations.

**Blocs :**

- environnement ;
- cadrage ;
- informations manquantes ;
- profil de gouvernance ;
- décisions à arbitrer ;
- documents à préparer ;
- conditions de sortie.

### 10.2. Mandat de conception

**Destinataire :** ORCHESTRATOR  
**Objectif :** transformer le cadrage en exigences, architecture et roadmap.

**Blocs :**

- exigences ;
- règles métier ;
- architecture ;
- ADR ;
- risques ;
- dépendances ;
- sprints proposés ;
- checkpoint attendu.

### 10.3. Mandat de préparation opérationnelle

**Destinataire :** ORCHESTRATOR  
**Objectif :** préparer le premier sprint et vérifier la readiness.

**Blocs :**

- documentation ;
- Git ;
- état opérationnel ;
- permissions ;
- tâches atomiques ;
- critères ;
- tests ;
- transition proposée.

### 10.4. Mandat d’exécution de sprint

**Destinataire :** BUILDER  
**Objectif :** réaliser uniquement le périmètre autorisé d’un sprint.

**Blocs :**

- sprint ;
- transition ;
- version du mandat ;
- branche ;
- objectif ;
- tâches ;
- références ;
- exclusions ;
- tests ;
- livrables ;
- rapport attendu.

### 10.5. Mandat d’audit

**Destinataire :** AUDITOR  
**Objectif :** vérifier directement le résultat du sprint.

**Blocs :**

- sprint ;
- transition ;
- mandat audité ;
- périmètre ;
- critères ;
- fichiers et commits ;
- tests à reproduire ;
- preuves attendues ;
- rapport d’audit.

### 10.6. Mandat correctif

**Destinataire :** BUILDER  
**Objectif :** corriger les anomalies identifiées sans étendre le périmètre.

**Blocs :**

- anomalie ou réserve ;
- cause connue ;
- correction autorisée ;
- critères de sortie ;
- tests de non-régression ;
- nouvelle transition ;
- rapport attendu.

### 10.7. Mandat de changement

**Destinataire :** ORCHESTRATOR, puis BUILDER si approuvé  
**Objectif :** analyser et, le cas échéant, mettre en œuvre un changement accepté.

**Blocs :**

- identifiant du changement ;
- origine ;
- description ;
- impact ;
- options ;
- décision ;
- documents affectés ;
- nouveau mandat ;
- vérification attendue.

### 10.8. Mandat de clôture

**Destinataire :** ORCHESTRATOR  
**Objectif :** préparer la clôture du projet.

**Blocs :**

- objectifs ;
- fonctionnalités ;
- audits ;
- état de `main` ;
- tests ;
- réserves ;
- risques résiduels ;
- documentation ;
- décision finale du VALIDATOR.

---

## 11. Ordre d’implémentation recommandé

L’implémentation d’AKORIS doit suivre un ordre progressif.

### Étape 1 — Définir le socle

Mettre en place :

- nom et finalité ;
- principes fondamentaux ;
- rôles ;
- autorité humaine ;
- vocabulaire commun.

### Étape 2 — Définir les profils

Mettre en place :

- Lite ;
- Standard ;
- Reinforced ;
- critères de sélection ;
- profil par défaut ;
- règles de changement de profil.

### Étape 3 — Définir les sources documentaires

Mettre en place :

- architecture des fichiers ;
- sources de référence ;
- règles de non-duplication ;
- liens entre documents.

### Étape 4 — Formaliser l’état

Mettre en place :

- `state.json` ;
- `state.md` ;
- états du projet ;
- états du sprint ;
- transitions ;
- décisions ;
- historique.

### Étape 5 — Formaliser les décisions

Mettre en place :

- niveaux de gravité ;
- preuves ;
- `GO` ;
- `NO_GO` ;
- `GO_WITH_RESERVES` ;
- `HOLD` ;
- réserves.

### Étape 6 — Formaliser les changements

Mettre en place :

- identifiants ;
- cycle de vie ;
- analyses d’impact ;
- changement de mandat ;
- changements urgents.

### Étape 7 — Formaliser l’audit

Mettre en place :

- méthode ;
- sources ;
- tests ;
- preuves ;
- rapport ;
- désaccords ;
- limites d’indépendance.

### Étape 8 — Formaliser les permissions

Mettre en place :

- matrice des rôles ;
- protections disponibles ;
- contrôles a posteriori ;
- violations ;
- gestion des secrets ;
- protection de `main`.

### Étape 9 — Créer les prompts d’amorçage

Créer :

- prompt ORCHESTRATOR ;
- prompt BUILDER ;
- prompt AUDITOR.

### Étape 10 — Tester sur un projet pilote

Vérifier :

- compréhension des rôles ;
- cohérence des documents ;
- transitions ;
- rapports ;
- décisions ;
- reprise après interruption ;
- limites de l’environnement.

### Étape 11 — Stabiliser et versionner

Après le projet pilote :

- corriger les ambiguïtés ;
- supprimer les duplications ;
- documenter les exceptions ;
- versionner le protocole ;
- publier les profils et les prompts stabilisés.

---

## 12. Bonnes pratiques de rédaction

- Écrire les règles impératives avec des formulations non ambiguës.
- Distinguer les obligations des recommandations.
- Identifier les hypothèses et les inconnues.
- Utiliser des identifiants stables.
- Préférer les références aux duplications.
- Ne pas mettre une décision de projet dans un modèle générique.
- Ne pas confondre exemple et valeur à utiliser telle quelle.
- Versionner les modèles importants.
- Indiquer les conditions de sortie de chaque bloc.
- Déclarer les limites des outils et de l’environnement.
- Ne pas prétendre qu’une permission est technique sans preuve.
- Ne pas déclarer un contrôle réussi sans preuve.
- Conserver les désaccords importants.
- Ne pas supprimer une anomalie pour rendre un rapport plus favorable.
- Prévoir les cas d’interruption et de reprise.

---

## 13. Bonnes pratiques de contexte pour les agents

### ORCHESTRATOR

Charger en priorité :

1. prompt ORCHESTRATOR ;
2. `governance_core.md` ;
3. profil actif ;
4. `state.json` ;
5. `state.md` ;
6. `agents.md` ;
7. documents métier et techniques pertinents.

### BUILDER

Charger en priorité :

1. prompt BUILDER ;
2. `state.json` ;
3. `current_sprint.md` ;
4. exigences concernées ;
5. critères d’acceptation ;
6. ADR applicables ;
7. contraintes techniques ;
8. rapport ou reçu de transition.

### AUDITOR

Charger en priorité :

1. prompt AUDITOR ;
2. transition reçue ;
3. `current_sprint.md` ;
4. exigences et critères ;
5. règles métier ;
6. ADR applicables ;
7. dépôt et commits ;
8. rapport de BUILDER.

Le contexte doit être chargé progressivement. Aucun agent ne doit recevoir automatiquement tous les documents si cela n’est pas nécessaire.

---

## 14. Workflow recommandé

```text
1. Choisir le profil de gouvernance
          ↓
2. Démarrer ORCHESTRATOR avec son bootstrap prompt
          ↓
3. Lire le protocole et inspecter l’environnement
          ↓
4. Conduire le cadrage
          ↓
5. Valider CP1
          ↓
6. Produire les exigences et la conception
          ↓
7. Valider CP2
          ↓
8. Préparer la gouvernance, Git et l’état
          ↓
9. Préparer le premier sprint
          ↓
10. Réaliser l’audit de préparation
          ↓
11. Valider CP3
          ↓
12. Créer une transition vers BUILDER
          ↓
13. VALIDATOR autorise BUILDER
          ↓
14. BUILDER exécute le sprint
          ↓
15. BUILDER produit son rapport
          ↓
16. Créer une transition vers AUDITOR
          ↓
17. VALIDATOR autorise AUDITOR
          ↓
18. AUDITOR vérifie directement le résultat
          ↓
19. ORCHESTRATOR analyse les résultats
          ↓
20. VALIDATOR décide : GO, NO GO, GO_WITH_RESERVES ou HOLD
          ↓
21. Corriger, accepter, fusionner ou suspendre
          ↓
22. Traiter les changements et réserves
          ↓
23. Préparer le sprint suivant
          ↓
24. Clôturer le projet après validation finale
```

---

## 15. Règles de transfert entre les agents

### ORCHESTRATOR vers BUILDER

Le transfert doit comprendre :

- identifiant de transition ;
- sprint ;
- version du mandat ;
- objectif ;
- périmètre ;
- tâches ;
- critères ;
- exclusions ;
- branche ;
- rapport attendu.

### BUILDER vers ORCHESTRATOR

Le rapport doit comprendre :

- tâches réalisées ;
- tâches non réalisées ;
- fichiers modifiés ;
- commits ;
- tests ;
- résultats ;
- anomalies ;
- écarts ;
- réserves ;
- preuves ;
- blocages éventuels.

### ORCHESTRATOR vers AUDITOR

Le transfert doit comprendre :

- identifiant de transition ;
- sprint ;
- mandat ;
- rapport de BUILDER ;
- périmètre à contrôler ;
- critères ;
- tests attendus ;
- limites connues.

### AUDITOR vers ORCHESTRATOR

Le rapport doit comprendre :

- périmètre audité ;
- méthode ;
- fichiers et commits examinés ;
- tests reproduits ;
- preuves ;
- tâches conformes ;
- anomalies ;
- gravité ;
- éléments non vérifiés ;
- recommandation.

---

## 16. Règles de versionnement

Les éléments suivants doivent être versionnés lorsque cela est pertinent :

- protocole AKORIS ;
- profils ;
- prompts ;
- modèles de rapports ;
- schéma de `state.json` ;
- décisions techniques ;
- mandats ;
- documents métier validés.

Une modification du protocole ne doit pas être confondue avec une modification du projet.

Les versions doivent être distinguées :

- version du protocole ;
- version du profil ;
- version du mandat ;
- version de l’état ;
- version du projet.

---

## 17. Règles de maintenance du cadre

Toute évolution d’AKORIS doit :

1. être identifiée ;
2. être analysée ;
3. indiquer les documents affectés ;
4. préserver la compatibilité avec les projets existants lorsque possible ;
5. mettre à jour les prompts concernés ;
6. mettre à jour les modèles concernés ;
7. être testée sur un projet pilote ;
8. recevoir une nouvelle version ;
9. être documentée dans un journal de changements du protocole.

Les changements du cadre lui-même doivent suivre les mêmes principes de traçabilité que les changements d’un projet.

---

## 18. Résumé opérationnel

```text
getting_started.md
= manuel complet et référence du protocole

governance_core.md
= règles communes obligatoires

profile_*.md
= niveau de contrôle choisi selon le risque

*_policy.md
= politiques spécialisées

*_bootstrap.md
= prompt opérationnel propre à chaque agent

state.json
= état opérationnel machine

state.md
= vue lisible générée

current_sprint.md
= mandat actif

reports/
= résultats et preuves des interventions
```

La séparation recommandée est donc :

> **Le protocole explique le cadre.**  
> **Le bootstrap donne le point de départ.**  
> **L’état décrit la situation courante.**  
> **Le mandat limite l’action autorisée.**  
> **Les rapports et les audits apportent les preuves.**

---

## 19. Conclusion

AKORIS doit être organisé comme un système documentaire modulaire, et non comme un unique méga prompt.

La combinaison recommandée est :

- un manuel complet `getting_started.md` ;
- un socle `governance_core.md` ;
- trois profils de gouvernance ;
- des politiques spécialisées ;
- un prompt d’amorçage par agent ;
- un état opérationnel central ;
- des mandats versionnés ;
- des rapports et registres séparés ;
- un workflow contrôlé par le VALIDATOR humain.

Cette organisation permet de conserver la richesse du protocole tout en limitant la charge de contexte, les duplications et les confusions de rôle.
