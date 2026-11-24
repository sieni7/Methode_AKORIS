# PLAN DE CONSOLIDATION AKORIS

**Version :** 0.1.0-draft  
**Date :** 2026-11-24  
**Cible :** AKORIS 1.0.0  
**Dépôt :** `sieni7/Methode_AKORIS`  
**Répertoire :** `C:\\Methode_AKORIS`  
**Branche de référence :** `main`  
**Commit initial :** `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea` — `docs(init): import existing AKORIS corpus`

## 1. Objet et principes

Ce plan organise la consolidation du corpus AKORIS existant. Il ne s'agit pas de repartir de zéro.

**Principe directeur :** L’IA propose. Les contrôles vérifient. L’humain décide.

- [ ] Travailler dans le dépôt existant, sans le remplacer.
- [ ] Préserver l'historique Git et le commit initial.
- [ ] Ne modifier aucune source pendant C0.
- [ ] Distinguer règles documentées, configuration technique et comportement testé.
- [ ] Ne jamais présenter une vérification non exécutée comme réussie.
- [ ] Utiliser `PASS`, `FAIL`, `NOT_CHECKED` ; `NOT_CHECKED` n'est jamais un succès.
- [ ] Conserver rapports, preuves, décisions et références de commits.
- [ ] Ne passer au chantier suivant qu'après décision explicite du VALIDATOR.

## 2. Gouvernance

| Rôle | Responsabilité |
|---|---|
| VALIDATOR humain | Décide, valide les livrables et autorise les transitions |
| ORCHESTRATOR | Cadre, planifie, coordonne et tient l'état |
| BUILDER DOCUMENTAIRE | Modifie le corpus selon un mandat autorisé |
| AUDITOR DOCUMENTAIRE | Vérifie indépendamment les livrables |

- [ ] L'ORCHESTRATOR ne se substitue jamais au VALIDATOR.
- [ ] Le BUILDER agit uniquement dans le périmètre autorisé.
- [ ] L'AUDITOR n'audite pas ses propres modifications.
- [ ] `state.json` est la source de vérité ; `state.md` est une vue générée.
- [ ] L'ORCHESTRATOR est le seul rédacteur normal de `state.json`.
- [ ] Les transitions opérationnelles utilisent les autorisations et jetons à usage unique prévus par le protocole.
- [ ] Les points HVG de ce plan ne sont pas les transitions opérationnelles entre agents.

Décisions possibles à chaque HVG : `GO`, `GO_WITH_RESERVES`, `NO_GO`, `HOLD`, `CANCELLED`. Toute décision précise son périmètre. Un rapport favorable ne vaut pas autorisation.

## 3. Règles Git de livraison

- [ ] Le VALIDATOR autorise le périmètre et décompose le chantier en tâches atomiques identifiées.
- [ ] Chaque tâche précise résultat attendu, périmètre, dépendances, critères d'acceptation et preuves/tests.
- [ ] Le BUILDER crée une branche de chantier depuis `main` (ex. `dev_C0`) et ne travaille pas directement sur `main`.
- [ ] Chaque tâche terminée donne lieu à un commit cohérent Conventional Commits, lié à son identifiant.
- [ ] L'AUDITOR examine changements, historique, tests, preuves, secrets et respect du périmètre.
- [ ] Acceptation du chantier et autorisation de fusion sont deux décisions distinctes.
- [ ] Après fusion autorisée, vérifier le commit sur `main`.
- [ ] Le chantier suivant part de `main` mis à jour et vérifié.
- [ ] Pousser les branches/livrables autorisés et conserver les preuves Git. Ne jamais déclarer un push effectué sans preuve.

## 4. Feuille de route

### C0 — Inventaire et état de référence du corpus
**HVG0 : approbation du périmètre et de l'état de référence**

- [ ] C0.1 Confirmer dépôt, branche, commit de référence et état Git.
- [ ] C0.2 Inventorier tous les fichiers et répertoires.
- [ ] C0.3 Relever pour chaque document : rôle, statut, version, date disponible et relations.
- [ ] C0.4 Classer les documents : normatifs, opérationnels, explicatifs, historiques/sources.
- [ ] C0.5 Identifier les décisions validées et leurs preuves.
- [ ] C0.6 Relever doublons, contradictions, divergences terminologiques, lacunes et dépendances.
- [ ] C0.7 Distinguer approuvé, proposé, obsolète, retiré et non vérifié.
- [ ] C0.8 Examiner les sources historiques sans leur attribuer automatiquement une autorité normative.
- [ ] C0.9 Produire cartographie du corpus et état de référence.
- [ ] C0.10 Présenter constats, incertitudes et recommandations.
- [ ] C0.11 Soumettre le rapport C0 au VALIDATOR.
- [ ] C0.12 Obtenir la décision HVG0.

**Contrainte : C0 est en lecture seule. Aucune correction des documents sources.**  
**Livrables :** inventaire, cartographie, registre des divergences/questions, rapport C0, proposition de périmètre C1.

### C1 — Consolidation normative et documentaire
**HVG1 : approbation du corpus consolidé**

- [ ] C1A Hiérarchie documentaire, statuts, autorité et prévalence des sources.
- [ ] C1B Modèle d'état, `state.json`, `state.md`, mandats, reçus et cycle de vie des transitions.
- [ ] C1C Permissions, rôles, périmètres, interdictions, exceptions et limites.
- [ ] C1D Décisions, preuves, rapports, registres, contestations, questions et historique.
- [ ] C1E Versions et évolution : consolider les règles SemVer déjà approuvées ; distinguer versions protocole/schéma et révisions documentaires.
- [ ] C1F Git/GitHub : tâches atomiques, branches, commits conventionnels, audit, acceptation, autorisation de fusion et vérification post-fusion.
- [ ] C1.1 Traiter les divergences de C0 par propositions documentées.
- [ ] C1.2 Relier les règles à leurs sources, justifications et mécanismes de vérification.
- [ ] C1.3 Distinguer `MUST`, `SHOULD`, `MAY` et `OUT OF SCOPE`.
- [ ] C1.4 Modifier les documents uniquement dans le périmètre autorisé.
- [ ] C1.5 Vérifier la cohérence croisée.
- [ ] C1.6 Faire auditer les changements.
- [ ] C1.7 Soumettre rapport et réserves au VALIDATOR ; obtenir HVG1.

**Livrables :** corpus consolidé, hiérarchie documentaire, règles harmonisées, registres et rapport d'audit.

### C2 — Vérification technique
**HVG2 : approbation du niveau de vérification**

- [ ] C2.1 Définir environnement, limites et conditions de sécurité.
- [ ] C2.2 Vérifier `state.json` et son schéma.
- [ ] C2.3 Vérifier transitions, destinataire, mandat, rapport source, jeton unique et autorisation humaine.
- [ ] C2.4 Vérifier cohérence état/mandat/reçu/rapport.
- [ ] C2.5 Vérifier permissions et frontières de rôle.
- [ ] C2.6 Vérifier règles Git/GitHub et CI/CD applicables.
- [ ] C2.7 Distinguer ce qui relève d'OpenCode, du système de fichiers, de Git local, du serveur distant ou de l'humain.
- [ ] C2.8 Définir T1 à T5 : préconditions, acteur, action, autorisation, attendu et preuve.
- [ ] C2.9 Tester dans un environnement jetable/réversible, avec données fictives et sans secrets.
- [ ] C2.10 Prévoir sauvegarde de l'état initial et procédure d'arrêt.
- [ ] C2.11 Documenter refus attendus et preuves de non-exécution.
- [ ] C2.12 Classer chaque résultat `PASS`, `FAIL` ou `NOT_CHECKED`.
- [ ] C2.13 Faire auditer et soumettre le rapport au VALIDATOR ; obtenir HVG2.

**Livrables :** protocole, résultats T1–T5, preuves, limites et rapport C2.

### C3 — Expérimentation dans `/app`
**HVG3 : approbation des résultats expérimentaux**

- [ ] C3.1 Définir périmètre et conditions de sécurité.
- [ ] C3.2 Décrire chaque scénario : précondition, acteur, action, autorisation, attendu, observé, preuve, écart et impact.
- [ ] C3.3 Préparer des scénarios de démonstration.
- [ ] C3.4 Préparer des scénarios de validation nominale.
- [ ] C3.5 Préparer des scénarios de résistance : refus, autorisation expirée/remplacée, réserves et limites.
- [ ] C3.6 Préparer des scénarios de récupération/reprise.
- [ ] C3.7 Préparer si nécessaire des scénarios de migration.
- [ ] C3.8 Exécuter uniquement les scénarios autorisés.
- [ ] C3.9 Consigner les écarts attendus/observés.
- [ ] C3.10 Distinguer défaut de méthode, configuration, implémentation et environnement.
- [ ] C3.11 Faire auditer, soumettre au VALIDATOR et obtenir HVG3.

**Livrables :** scénarios, preuves, écarts, limites et rapport C3.

### C4 — Documentation finale et cas pratiques
**HVG4 : approbation de la documentation finale**

- [ ] C4.1 Stabiliser les documents normatifs.
- [ ] C4.2 Finaliser les guides opérationnels par rôle.
- [ ] C4.3 Finaliser modèles de rapports, mandats, décisions, réserves et reçus.
- [ ] C4.4 Documenter transitions, autorisations, refus, incidents et reprises.
- [ ] C4.5 Produire des cas pratiques nominaux et limites.
- [ ] C4.6 Harmoniser terminologie et conventions éditoriales.
- [ ] C4.7 Vérifier liens, références, exemples, commandes et chemins.
- [ ] C4.8 Ne pas présenter comme garanties des capacités non testées.
- [ ] C4.9 Faire réaliser une revue indépendante.
- [ ] C4.10 Traiter les réserves, soumettre au VALIDATOR et obtenir HVG4.

**Livrables :** documentation finale, guides, modèles, cas pratiques et rapport C4.

### C5 — Préparation et publication AKORIS 1.0.0
**HVG5 : autorisation finale de publication**

- [ ] C5.1 Définir le périmètre exact de 1.0.0.
- [ ] C5.2 Vérifier versions protocole, schémas et documents.
- [ ] C5.3 Vérifier changelog et notes de version.
- [ ] C5.4 Vérifier dépôt, branches, commits, tags et éléments publiés.
- [ ] C5.5 Vérifier tests/preuves et signaler les `NOT_CHECKED`.
- [ ] C5.6 Faire réaliser l'audit final.
- [ ] C5.7 Documenter réserves, limites, exclusions et compatibilités.
- [ ] C5.8 Soumettre le dossier au VALIDATOR.
- [ ] C5.9 Obtenir une autorisation explicite HVG5.
- [ ] C5.10 Publier/taguer uniquement après autorisation.
- [ ] C5.11 Vérifier la publication et archiver les preuves.

**Précaution :** la stabilité de la méthode/spécification dans le périmètre déclaré ne prouve pas que toutes les implémentations sont stables, que toutes les permissions sont garanties, que toutes les migrations sont réalisées ou que l'efficacité à long terme est démontrée.

**Livrables :** dossier de publication, audit final, notes de version, tag/release et preuves.

## 5. Registre de suivi

| Chantier | Point | Statut initial | Décision | Commit / preuve |
|---|---|---|---|---|
| C0 — Inventaire | HVG0 | À préparer | En attente | — |
| C1 — Consolidation | HVG1 | Bloqué par C0 | En attente | — |
| C2 — Vérification | HVG2 | Bloqué par C1 | En attente | — |
| C3 — Expérimentation | HVG3 | Bloqué par C2 | En attente | — |
| C4 — Documentation finale | HVG4 | Bloqué par C3 | En attente | — |
| C5 — Publication 1.0.0 | HVG5 | Bloqué par C4 | En attente | — |

## 6. Journal des décisions

| ID | Date | Objet | Décision | Auteur | Référence |
|---|---|---|---|---|---|
| D-001 | 2026-11-24 | Plan global | Cadre de travail proposé ; adoption et GO C0 restent à confirmer explicitement par le VALIDATOR | VALIDATOR | Présent document |

## 7. Clôture

- [ ] Rapports distincts pour C0 à C5.
- [ ] Décision explicite du VALIDATOR à chaque HVG.
- [ ] Réserves ouvertes recensées et arbitrées.
- [ ] Commits, fusions et publication vérifiés par preuves.
- [ ] Limites et vérifications non réalisées exposées.
- [ ] Dossier de publication 1.0.0 complet et autorisé.

**Rappel :** l'approbation du plan ne vaut ni GO automatique pour C0, ni autorisation de modifier les sources, de fusionner ou de publier.
