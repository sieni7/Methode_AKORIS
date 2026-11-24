# AKORIS

## Adaptive Knowledge and Orchestrated Reviews for Iterative Systems

### Cadre de gouvernance et de contrôle du développement assisté par IA

**Version consolidée :** 1.0  
**Rôles :** ORCHESTRATOR, BUILDER, AUDITOR  
**Autorité finale :** VALIDATOR humain  
**Profils :** Lite, Standard, Reinforced

---

## 1. Objet du cadre

AKORIS est un cadre de gouvernance, de contrôle et de traçabilité destiné aux projets développés avec l’assistance d’agents d’intelligence artificielle.

Il organise :

- la compréhension du besoin ;
- la formalisation des décisions ;
- la préparation des tâches ;
- l’exécution par un agent de développement ;
- la vérification indépendante ;
- la gestion des changements ;
- la conservation des preuves ;
- la décision humaine.

AKORIS ne remplace pas l’expertise métier, technique, juridique ou de sécurité. Il aide à structurer les décisions et à réduire les erreurs non détectées.

> **L’IA propose. Les contrôles vérifient. L’humain décide.**

---

## 2. Principes fondamentaux

1. Une proposition de l’IA n’est pas une décision validée.
2. Un rapport positif n’est pas une autorisation de poursuivre.
3. Un identifiant de transition n’est pas une preuve cryptographique.
4. Une hypothèse ne doit pas être présentée comme un fait.
5. Une règle métier ne doit jamais être inventée par l’IA.
6. Toute décision structurante doit être traçable.
7. Toute vérification importante doit être accompagnée d’une preuve.
8. Toute anomalie doit être signalée.
9. Une autorisation ne porte que sur le périmètre explicitement défini.
10. Une modification du mandat doit être signalée.
11. La fusion vers `main` nécessite une validation humaine distincte.
12. Les secrets ne doivent apparaître ni dans les rapports ni dans le dépôt.
13. Les permissions déclarées doivent être distinguées des permissions réellement imposées.
14. Le niveau de gouvernance doit être adapté au risque.
15. Le VALIDATOR conserve toujours la décision finale.

---

## 3. Rôles

### 3.1. ORCHESTRATOR

ORCHESTRATOR :

- conduit le cadrage ;
- distingue faits, hypothèses et recommandations ;
- prépare les décisions ;
- organise les exigences et l’architecture ;
- planifie les sprints ;
- prépare les mandats ;
- gère les transitions ;
- maintient l’état opérationnel ;
- analyse les rapports ;
- formule les recommandations ;
- suit les réserves et les changements.

Pendant l’exécution d’un sprint, ORCHESTRATOR ne modifie pas le code applicatif, sauf autorisation explicite prévue par le profil et le mandat.

ORCHESTRATOR est le seul rédacteur normal de `state.json`.

### 3.2. BUILDER

BUILDER :

- exécute le mandat autorisé ;
- modifie le code dans le périmètre prévu ;
- réalise les tests ;
- crée les commits ;
- signale les blocages ;
- documente les écarts ;
- fournit les preuves ;
- produit le rapport de sprint.

BUILDER ne doit pas :

- modifier les décisions validées sans arbitrage ;
- modifier `state.json` ;
- modifier le rapport d’audit ;
- fusionner directement vers `main` ;
- étendre silencieusement le périmètre.

### 3.3. AUDITOR

AUDITOR :

- examine directement le dépôt ;
- vérifie le mandat ;
- contrôle les tâches ;
- reproduit les tests pertinents ;
- vérifie les critères d’acceptation ;
- recherche les régressions ;
- examine les écarts et les preuves ;
- produit le rapport d’audit.

AUDITOR ne corrige pas le code qu’il audite et ne modifie pas l’état central.

L’indépendance d’AUDITOR est :

- **procédurale** par défaut ;
- **technique** uniquement si l’environnement l’impose réellement.

### 3.4. VALIDATOR humain

VALIDATOR :

- valide le cadrage ;
- arbitre les décisions structurantes ;
- choisit le profil de gouvernance ;
- autorise les transitions ;
- accepte ou rejette les résultats ;
- accepte les réserves ;
- autorise les fusions ;
- autorise les déploiements ;
- peut suspendre ou annuler le projet.

---

## 4. Profils de gouvernance

Le profil est choisi au début du projet selon le risque. Il est enregistré dans `state.json`.

```json
{
  "governance": {
    "framework": "AKORIS",
    "profile": "standard",
    "profile_locked": true,
    "selected_by": "VALIDATOR"
  }
}
```

Le profil ne modifie pas les principes fondamentaux. Il détermine le niveau de documentation, de preuve, de validation et d’audit.

### 4.1. Lite

Adapté aux :

- prototypes ;
- projets personnels ;
- outils éducatifs ;
- expérimentations ;
- projets faiblement exposés ;
- logiciels facilement réversibles.

Exigences minimales :

- cadrage court ;
- périmètre explicite ;
- exigences principales ;
- décisions techniques importantes ;
- mandat de tâche ;
- tests essentiels ;
- revue humaine avant livraison.

Les checkpoints peuvent être regroupés. L’audit est ciblé, mais l’agent qui produit le code ne doit pas être l’unique juge de son résultat.

### 4.2. Standard

Profil par défaut pour un projet logiciel réel.

Exigences :

- CP1, CP2 et CP3 ;
- ORCHESTRATOR, BUILDER et AUDITOR ;
- exigences fonctionnelles et non fonctionnelles pertinentes ;
- architecture ;
- ADR structurants ;
- roadmap ;
- état central ;
- audit de chaque sprint ;
- gestion des changements majeurs ;
- gestion des réserves ;
- validation humaine avant fusion.

### 4.3. Reinforced

Adapté aux projets :

- manipulant des données sensibles ;
- soumis à des obligations réglementaires ;
- exposés à un risque financier, médical ou administratif ;
- difficiles à restaurer ;
- largement exposés au public ;
- comportant des opérations irréversibles ;
- liés à une infrastructure critique.

Exigences supplémentaires :

- classification des données ;
- analyse de sécurité ;
- stratégie de sauvegarde et restauration ;
- stratégie de rollback ;
- preuves reproductibles ;
- audit complet des exigences critiques ;
- contrôle des dépendances ;
- autorisations versionnées et éventuellement expirantes ;
- analyse des risques résiduels ;
- mesures compensatoires en cas de protection technique absente.

Un projet ne peut pas choisir Lite pour éviter un contrôle rendu nécessaire par son niveau de risque.

---

## 5. Architecture documentaire

La structure recommandée est hybride : un socle commun et des profils séparés.

```text
governance/
├── governance_core.md
├── profile_lite.md
├── profile_standard.md
└── profile_reinforced.md
```

### 5.1. Sources de référence

| Domaine | Source de référence |
|---|---|
| État opérationnel | `state.json` |
| Vue lisible de l’état | `state.md` |
| Mandat courant | `current_sprint.md` |
| Règles métier | `docs/business_rules/` |
| Cas d’utilisation | `docs/use_cases/` |
| Exigences | `docs/requirements/` |
| Critères d’acceptation | `docs/acceptance_criteria/` |
| Architecture | `docs/architecture/` |
| Décisions techniques | `docs/adr/` |
| Roadmap | `sprints/roadmap.md` |
| Rapport BUILDER | `sprint_report/` |
| Rapport AUDITOR | `audit_report/` |
| Réserves et dette | `debt_report/` |
| Changements | `docs/governance/changes/` |
| Risques | `docs/risks/` |

### 5.2. Règle de non-duplication

`contexte.md` doit rester une synthèse. Il ne doit pas reproduire intégralement :

- les exigences ;
- les règles métier ;
- les ADR ;
- les rapports ;
- les mandats.

Il doit contenir des résumés et des références vers les sources spécialisées.

En cas de divergence, la source spécialisée prévaut et la divergence doit être signalée.

---

## 6. États et transitions

AKORIS sépare :

1. l’état du projet ;
2. l’état du sprint ;
3. l’état de la transition ;
4. l’état de la décision humaine.

### 6.1. États du projet

```text
initializing
framing
designing
planning
preparing
ready
in_progress
under_review
blocked
suspended
completed
cancelled
```

### 6.2. États du sprint

```text
planned
preparing
awaiting_authorization
authorized
in_progress
builder_completed
auditing
audit_completed
accepted
accepted_with_reserves
rejected
correcting
merged
closed
cancelled
```

### 6.3. États d’une transition

```text
draft
awaiting_human_go
authorized
consumed
in_progress
completed
rejected
expired
cancelled
```

Une transition terminée, consommée, expirée ou annulée ne peut pas être réactivée. Une nouvelle action exige un nouvel identifiant.

### 6.4. Structure minimale d’une transition

```json
{
  "id": "TR-2026-0001",
  "from_agent": "ORCHESTRATOR",
  "to_agent": "BUILDER",
  "project_id": "PROJECT-001",
  "sprint_id": "sprint_01",
  "action": "execute_sprint",
  "mandate_version": "sprint_01-v1",
  "status": "awaiting_human_go",
  "created_at": null,
  "expires_at": null,
  "authorized_at": null,
  "consumed_at": null,
  "started_at": null,
  "completed_at": null,
  "receipt_reference": null,
  "result_report": null,
  "authorization": {
    "required": true,
    "authorized_by": null,
    "decision_id": null
  }
}
```

### 6.5. Distinction essentielle

Les notions suivantes ne doivent pas être confondues :

- **autorisation** : le VALIDATOR autorise l’action ;
- **consommation** : l’agent accepte et utilise l’autorisation ;
- **exécution** : l’action est en cours ;
- **achèvement** : le résultat est produit ;
- **acceptation** : le VALIDATOR accepte le résultat.

---

## 7. État central

`state.json` est la source de vérité de l’état opérationnel.

`state.md` est une vue générée. Il ne doit jamais devenir une source concurrente.

Exemple de structure :

```json
{
  "schema_version": "2.0",
  "protocol": {
    "name": "AKORIS",
    "version": "1.0"
  },
  "governance": {
    "profile": "standard",
    "profile_locked": true,
    "selected_by": "VALIDATOR",
    "selected_at": null
  },
  "project": {
    "id": "PROJECT-001",
    "name": "PROJECT_NAME",
    "status": "initializing",
    "created_at": null,
    "updated_at": null
  },
  "checkpoints": {
    "cp1": "pending",
    "cp2": "pending",
    "cp3": "pending"
  },
  "sprint": {
    "current_id": null,
    "current_status": null,
    "next_id": "sprint_01"
  },
  "agent": {
    "current_agent": "ORCHESTRATOR",
    "state_owner": "ORCHESTRATOR"
  },
  "transition": null,
  "last_decision": null,
  "blockers": [],
  "reserves": [],
  "change_control": {
    "active_changes": [],
    "change_history": []
  },
  "permission_violations": [],
  "transition_history": []
}
```

Le fichier doit être :

- valide ;
- versionné ;
- vérifiable par schéma ;
- cohérent avec les rapports ;
- protégé contre les modifications non autorisées.

---

## 8. Critères de décision

### 8.1. Décisions possibles

```text
GO
GO_WITH_RESERVES
NO_GO
HOLD
CANCELLED
```

`HOLD` est utilisé lorsque la décision ne peut pas être prise faute de preuve, d’arbitrage ou de cohérence.

### 8.2. Gravité des anomalies

| Niveau | Description | Décision habituelle |
|---|---|---|
| S0 | Critique : sécurité, données, secret, risque grave | `NO_GO` |
| S1 | Majeure : exigence essentielle non satisfaite | `NO_GO` |
| S2 | Modérée : défaut maîtrisable avec contournement | Réserve possible |
| S3 | Mineure : défaut limité ou amélioration | `GO` possible |

### 8.3. Conditions d’un `GO`

- périmètre clairement défini ;
- exigences obligatoires satisfaites ;
- critères vérifiés ;
- tests pertinents passés ;
- aucune anomalie S0 ou S1 ;
- preuves disponibles ;
- mandat respecté ;
- transition valide ;
- risques acceptables pour le profil.

### 8.4. Conditions d’un `GO_WITH_RESERVES`

Chaque réserve doit posséder :

- un identifiant ;
- une description ;
- une gravité ;
- un impact ;
- un responsable ;
- une tâche de résolution ;
- un sprint de résolution ;
- une échéance ;
- une méthode de vérification ;
- une décision humaine.

Une réserve ne doit pas servir à masquer une anomalie critique ou un changement de périmètre.

### 8.5. Conditions d’un `HOLD`

`HOLD` est utilisé lorsque :

- une preuve critique manque ;
- une décision métier manque ;
- des documents se contredisent ;
- le résultat n’est pas reproductible ;
- l’état central est incohérent ;
- une dépendance doit être clarifiée.

---

## 9. Gestion des preuves

Une affirmation d’agent n’est pas automatiquement une preuve.

### Types de preuves

- commit Git ;
- sortie de commande ;
- résultat de test ;
- rapport CI ;
- fichier inspecté ;
- journal d’exécution ;
- reproduction manuelle ;
- scan de sécurité ;
- décision humaine ;
- comparaison avant/après.

### Statuts de preuve

```text
directly_verified
reproduced
cross_checked
declared_only
partial
missing
invalid
```

Une preuve `declared_only` ne suffit pas pour valider un critère critique.

Les contrôles utilisent les statuts :

```text
PASS
FAIL
PARTIAL
N/A
NOT_CHECKED
```

`NOT_CHECKED` ne vaut jamais `PASS`.

---

## 10. Gestion des changements

Un changement est toute modification affectant :

- le périmètre ;
- une exigence ;
- une règle métier ;
- une architecture ;
- une donnée ;
- la sécurité ;
- un mandat ;
- un sprint ;
- une décision validée ;
- le niveau de gouvernance.

### 10.1. Classification

- changement éditorial ;
- changement mineur ;
- changement majeur ;
- changement critique ou urgent.

### 10.2. Identifiants

```text
CHG-YYYY-NNNN
URG-YYYY-NNNN
```

### 10.3. Cycle de vie

```text
proposed
under_analysis
awaiting_decision
approved
rejected
deferred
implemented
verified
closed
cancelled
```

### 10.4. Analyse d’impact

Une analyse de changement doit examiner :

- impact métier ;
- impact fonctionnel ;
- impact technique ;
- impact sécurité ;
- impact données ;
- impact planning ;
- impact tests ;
- impact réversibilité.

La réversibilité est classée :

```text
R0 — facilement réversible
R1 — correction simple
R2 — migration ou intervention importante
R3 — difficilement réversible ou irréversible
```

### 10.5. Effet sur le mandat

Si un changement modifie :

- le périmètre ;
- le sprint ;
- l’action ;
- l’architecture ;
- les critères ;
- le profil de risque ;
- la version du mandat ;

alors :

1. l’ancienne autorisation est suspendue ou invalidée ;
2. le mandat reçoit une nouvelle version ;
3. les documents sont mis à jour ;
4. une nouvelle transition est créée ;
5. un nouveau `GO` est nécessaire.

### 10.6. Urgence

Une urgence peut justifier un confinement immédiat :

- désactivation d’une fonctionnalité ;
- révocation d’un secret ;
- blocage d’un accès ;
- arrêt d’un déploiement ;
- isolation d’une intégration.

Elle ne supprime jamais la traçabilité ni l’audit a posteriori.

---

## 11. Audit indépendant

L’auditeur doit travailler selon la chaîne :

```text
Mandat
→ Code livré
→ Commits
→ Tests
→ Preuves
→ Critères d’acceptation
→ Résultat
```

Le rapport de BUILDER est une source d’information, pas la source première de vérité.

### 11.1. Séquence d’audit

1. Vérifier la transition.
2. Lire le mandat.
3. Lire les exigences et critères.
4. Inspecter le dépôt.
5. Examiner les commits.
6. Reproduire les tests pertinents.
7. Tester les cas limites et négatifs.
8. Vérifier les modifications hors périmètre.
9. Classer les preuves.
10. Produire le rapport.

### 11.2. Rapport d’audit

Le rapport doit contenir :

- identification ;
- périmètre ;
- limites ;
- sources examinées ;
- méthode ;
- tâches vérifiées ;
- tests reproduits ;
- écarts ;
- preuves ;
- éléments non vérifiés ;
- comparaison avec le rapport BUILDER ;
- recommandation.

AUDITOR doit pouvoir conclure :

- qu’une affirmation de BUILDER est confirmée ;
- qu’elle est partiellement confirmée ;
- qu’elle n’est pas confirmée ;
- qu’elle est contredite.

---

## 12. Permissions réelles

AKORIS distingue trois types de permissions.

### Permission procédurale

Règle de comportement non imposée techniquement.

### Permission technique

Restriction effectivement imposée par :

- système de fichiers ;
- utilisateur distinct ;
- branche protégée ;
- CI ;
- outil ;
- contrôle d’accès ;
- répertoire isolé.

### Permission contrôlée a posteriori

Action techniquement possible mais vérifiée après exécution.

Chaque permission doit être classée :

```text
technical_enforced
procedural_only
post_checked
not_available
unknown
```

`unknown` ne doit jamais être présenté comme une garantie.

### Principe du moindre privilège

- ORCHESTRATOR écrit la gouvernance, pas le code applicatif pendant les sprints.
- BUILDER écrit le code autorisé, pas l’état central ni les rapports d’audit.
- AUDITOR écrit son rapport, pas le code audité ni l’état central.
- VALIDATOR décide, mais ne doit pas nécessairement posséder un accès général aux secrets.

Dans un environnement partagé, les permissions sont principalement procédurales sauf preuve technique contraire.

---

## 13. Violations de permissions

Une violation doit être :

1. arrêtée ;
2. conservée dans les traces ;
3. identifiée ;
4. évaluée ;
5. auditée ;
6. rattachée à une décision ;
7. corrigée ou acceptée explicitement.

Niveaux :

| Niveau | Exemple |
|---|---|
| P0 | Secret exposé, état falsifié ou preuve détruite |
| P1 | Fusion non autorisée, décision modifiée |
| P2 | Fichier hors périmètre modifié |
| P3 | Erreur documentaire mineure |

Une violation peut invalider le résultat même si le code fonctionne, notamment dans le profil Reinforced.

---

## 14. Checkpoints

### CP1 — Cadrage

Validation de :

- vision ;
- problème ;
- utilisateurs ;
- objectifs ;
- périmètre ;
- exclusions ;
- contraintes ;
- principales règles métier.

### CP2 — Conception et planification

Validation de :

- exigences ;
- architecture ;
- stack ;
- ADR ;
- roadmap ;
- sprints ;
- dépendances ;
- risques.

### CP3 — Préparation opérationnelle

Validation de :

- documentation ;
- contrats d’agents ;
- permissions ;
- Git ;
- état central ;
- premier sprint ;
- audit de préparation.

Aucune transition opérationnelle ne doit être déclenchée avant validation du checkpoint concerné.

---

## 15. Cycle nominal d’un sprint

```text
ORCHESTRATOR prépare le mandat
        ↓
VALIDATOR valide le checkpoint ou la transition
        ↓
BUILDER reçoit un GO identifié
        ↓
BUILDER exécute le sprint
        ↓
BUILDER produit son rapport
        ↓
ORCHESTRATOR prépare la transition vers AUDITOR
        ↓
AUDITOR reçoit un GO identifié
        ↓
AUDITOR vérifie directement le résultat
        ↓
AUDITOR produit son rapport
        ↓
ORCHESTRATOR formule une recommandation
        ↓
VALIDATOR prend la décision
        ↓
Correction, acceptation ou fusion séparée
```

L’acceptation d’un sprint n’autorise pas automatiquement :

- le sprint suivant ;
- la fusion dans `main` ;
- le déploiement ;
- l’accès à de nouvelles données ;
- une modification d’architecture.

---

## 16. Règles de Git

- Le travail de sprint se fait sur une branche dédiée.
- BUILDER ne travaille pas directement sur `main`.
- Chaque tâche terminée produit un commit cohérent lorsque cela est pertinent.
- Les commits doivent être traçables.
- Les modifications hors mandat sont signalées.
- La fusion vers `main` nécessite une décision humaine distincte.
- La protection technique de `main` doit être vérifiée et non supposée.
- Les secrets doivent être recherchés avant commit et avant fusion.

---

## 17. Architecture indicative du projet

La structure exacte doit être adaptée à la complexité du projet. Ne créer que les dossiers nécessaires.

```text
project/
├── .gitignore
├── README.md
├── contexte.md
├── agents.md
├── state.json
├── state.md
├── current_sprint.md
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
│       └── changes/
├── sprints/
│   └── roadmap.md
├── sprint_report/
├── audit_report/
├── debt_report/
└── src/
```

---

## 18. Charge estimative consolidée

Les priorités 1 à 7 représentent, individuellement, une charge documentaire importante. Certaines tâches se recouvrent :

- les profils utilisent les critères de décision ;
- les transitions utilisent les permissions ;
- l’audit utilise la classification des preuves ;
- la réduction documentaire affecte tous les autres sujets ;
- le schéma de `state.json` centralise plusieurs priorités.

### Version documentaire initiale

> **35 à 55 heures**

Elle comprend :

- profils ;
- règles de décision ;
- changements ;
- audit ;
- permissions ;
- architecture documentaire ;
- schéma conceptuel de l’état.

### Version professionnelle cohérente

> **65 à 110 heures**

Elle ajoute :

- JSON Schema ;
- tables de transition ;
- modèles de rapports ;
- scénarios d’erreur ;
- procédure de reprise ;
- règles de preuve ;
- tests de cohérence documentaire ;
- vérification des permissions effectives.

### Version renforcée avec automatisation

> **100 à 160 heures**

Elle ajoute notamment :

- validation automatique de `state.json` ;
- génération de `state.md` ;
- contrôles de cohérence ;
- hooks Git ou CI ;
- détection des fichiers hors périmètre ;
- contrôle des transitions ;
- scénarios automatisés de reprise ;
- tests du protocole ;
- vérification de la protection de `main`.

Ces estimations concernent la consolidation d’AKORIS, pas le développement de l’application gouvernée.

---

## 19. Conclusion

AKORIS est :

> **Un cadre de gouvernance et de contrôle du développement assisté par IA, reposant sur un socle commun et trois profils proportionnés au risque : Lite, Standard et Reinforced.**

Les décisions structurantes retenues sont :

1. Un socle commun, complété par trois profils séparés.
2. Un état opérationnel central versionné et vérifiable.
3. Une séparation entre projet, sprint, transition et décision.
4. Des critères de décision fondés sur la gravité et les preuves.
5. Une procédure formelle de changement.
6. Un audit reposant sur la contre-vérification directe.
7. Une distinction entre permissions procédurales et techniques.
8. Une architecture documentaire sans duplication inutile.
9. Une validation humaine distincte de la recommandation de l’IA.
10. Une fusion, un déploiement ou une modification sensible toujours soumis à une autorisation explicite.

> **AKORIS organise les connaissances, limite le périmètre d’action des agents, exige des preuves, orchestre les revues et conserve à l’humain la décision finale.**
