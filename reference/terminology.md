# Terminologie AKORIS

| Champ | Valeur |
|---|---|
| Version | 0.3 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | Vocabulaire du cadre AKORIS, tous profils, toutes implémentations |
| Autorité | Source unique du vocabulaire |
| Vague | 1 |

**Sources citées :** `F3` = `AKORIS_consolide.md` · `F2` = `AKORIS_architecture_documentaire.md` · `F1` = `akoris_documentation_builder.md` · `GS1` = `getting_started.md` du projet pilote (v1, matériau non doctrinal).

---

## 0. Règle d'usage

Ce fichier est la **source unique** du vocabulaire AKORIS.

- Un terme défini ici ne doit pas être redéfini ailleurs. Les autres documents l'emploient tel quel.
- Si un document emploie un terme dans un sens différent, c'est une **divergence** : elle se signale, elle ne se corrige pas silencieusement.
- Un terme dont la définition dépend d'un arbitrage non tranché porte le statut `À ARBITRER` et ne doit pas être utilisé comme s'il était fixé.
- Les définitions ci-dessous sont **descriptives** : elles disent ce que le terme désigne, pas ce qu'il faut faire. Les obligations sont dans `governance_core.md` et dans les politiques.

---

## 1. Le cadre

| Terme | Définition | Source | Statut |
|---|---|---|---|
| **AKORIS** | *Adaptive Knowledge and Orchestrated Reviews for Iterative Systems.* Cadre de gouvernance, de contrôle et de traçabilité du développement assisté par IA. | F3 §1 | FAIT |
| **Cadre** | Ensemble formé par le protocole, les profils et les implémentations documentées. | F3 §19, A8 | RECOMMANDATION |
| **Protocole** | Ensemble normatif des règles communes : principes, rôles, états, décisions, preuves, changements, audit, permissions, reprises. Le protocole est agnostique de l'outil. | F3, A8 | FAIT |
| **Socle commun** | Partie du protocole applicable à tous les profils sans exception : `governance_core.md`. | F3 §5, F2 §4.2 | FAIT |
| **Profil de gouvernance** | Niveau de contrôle choisi selon le risque : Lite, Standard, Reinforced. Il détermine le niveau de documentation, de preuve, de validation et d'audit, sans modifier les principes fondamentaux. | F3 §4 | FAIT |
| **Implémentation** | Environnement concret dans lequel le protocole est appliqué, et qui peut fournir des contrôles techniques supplémentaires. OpenCode est l'implémentation de référence. | A8 | FAIT |
| **Politique** | Document normatif spécialisé traitant un domaine : état, transitions, décisions, changements, audit, permissions, reprises. | F2 §4 | FAIT |
| **Modèle** | Document réutilisable définissant la forme d'un livrable (rapport, décision, changement, réserve, reçu). Un modèle ne contient aucune décision de projet. | F2 §8.3, F1 §7 | FAIT |
| **Prompt d'amorçage** | Prompt court propre à un rôle, qui oriente vers les documents de référence sans les recopier. | F2 §5 | FAIT |
| **Méga prompt** | Document unique prétendant contenir à lui seul tout le protocole et toute la méthode. Anti-patron explicitement écarté. | F2 §19, F1 §14 | FAIT |

---

## 2. Acteurs

| Terme | Définition | Source | Statut |
|---|---|---|---|
| **Agent** | Acteur automatisé assumant un rôle du protocole : ORCHESTRATOR, BUILDER ou AUDITOR. Le VALIDATOR n'est pas un agent. | F3 §3 | FAIT |
| **Rôle** | Fonction assumée par un acteur, définie par un contrat : périmètre, responsabilités, permissions, interdictions, livrables. | F2 §6.3 | FAIT |
| **ORCHESTRATOR** | Agent qui conduit le cadrage, prépare les décisions et les mandats, gère les transitions, maintient l'état opérationnel, analyse les rapports et suit réserves et changements. Seul rédacteur normal de `state.json`. | F3 §3.1 | FAIT |
| **BUILDER** | Agent qui exécute le mandat autorisé, modifie le code dans le périmètre prévu, teste, commite, fournit les preuves et produit le rapport de sprint. | F3 §3.2 | FAIT |
| **AUDITOR** | Agent qui examine directement le dépôt, vérifie le mandat, les tâches, les tests et les critères, et produit le rapport d'audit. Ne corrige pas ce qu'il audite. | F3 §3.3 | FAIT |
| **VALIDATOR** | Autorité humaine finale : valide le cadrage, choisit le profil, arbitre les décisions structurantes, autorise les transitions, accepte ou rejette les résultats, autorise fusions et déploiements. | F3 §3.4 | FAIT |
| **DOCUMENTATION BUILDER** | Rôle documentaire **auxiliaire** : conçoit, rédige, organise et maintient la documentation du cadre. N'agit ni sur le code applicatif ni sur l'état opérationnel. Distinct des trois agents et du VALIDATOR : il ne décide pas, n'audite pas et ne valide pas. | F1 §1 ; décision **A5** | FAIT |
| **Instance d'agent** | Occurrence concrète d'un rôle dans un environnement donné (un onglet, une session). Plusieurs instances ne changent pas le rôle. | GS1 §0.3 | HYPOTHÈSE |

> **Ne pas confondre « rôle » et « instance ».** Un rôle est défini par le protocole ; une instance est un contenant d'exécution. Le protocole ne dépend pas du nombre d'instances.

---

## 3. Objets opérationnels

| Terme | Définition | Source | Statut |
|---|---|---|---|
| **État opérationnel** | Situation courante du projet et du sprint : agent propriétaire du tour, transition active, dernière décision, blocages, réserves, changements. | F3 §7 | FAIT |
| **`state.json`** | Source de vérité machine de l'état opérationnel. Versionné, valide, vérifiable par schéma, cohérent avec les rapports. | F3 §7 | FAIT |
| **`state.md`** | Vue lisible **générée** à partir de `state.json`. Jamais une source concurrente. | F3 §7, F2 §6.5 | FAIT |
| **Sprint** | Incrément de travail borné, doté d'un objectif, d'un périmètre, de tâches, de critères et de conditions de clôture. | F2 §8.2 | FAIT |
| **Mandat** | Mission autorisée, explicite et bornée, confiée à un rôle. Versionnée lorsqu'elle évolue. | F2 §10 | FAIT |
| **Mandat courant** | Mandat du sprint en cours, porté par `current_sprint.md`. | F3 §5.1 | FAIT |
| **Checkpoint** | Point de validation humaine conditionnant la suite : CP1 cadrage, CP2 conception et planification, CP3 préparation opérationnelle. | F3 §14 | FAIT |
| **Transition** | Passage autorisé d'un rôle à un autre pour une action déterminée, identifié et tracé. | F3 §6.3 | FAIT |
| **Identifiant de transition** (`transition_id`) | Identifiant d'une transition utilisé comme autorisation d'agir (`TR-AAAA-NNNN`). N'est **pas** une preuve cryptographique. Le nom `token` est déprécié (C22). | F3 §2.3, §6.4 ; décision **C22** | FAIT |
| **Reçu de transition** | Trace déposée par l'agent destinataire attestant qu'il a reçu et consommé une autorisation, avec agent, sprint, action et date. | `protocol/transition_policy.md` §5 ; décision **A2** | FAIT |
| **Autorisation** | Acte par lequel le VALIDATOR permet une action. | F3 §6.5 | FAIT |
| **Consommation** | Acte par lequel l'agent destinataire accepte et utilise l'autorisation. | F3 §6.5 | FAIT |
| **Exécution** | Période pendant laquelle l'action autorisée est en cours. | F3 §6.5 | FAIT |
| **Achèvement** | Moment où le résultat est produit, avant toute acceptation. | F3 §6.5 | FAIT |
| **Acceptation** | Acte par lequel le VALIDATOR accepte le résultat. Distinct de l'achèvement et de l'autorisation. | F3 §6.5 | FAIT |
| **Blocage** | Situation empêchant la poursuite normale, qui doit être signalée et rattachée à une décision. | F3, F2 §8 | FAIT |
| **Incident** | Événement de sécurité, de permission, d'état ou d'exécution nécessitant un traitement tracé. | F2 §8.8 | FAIT |

---

## 4. Décisions et preuves

| Terme | Définition | Source | Statut |
|---|---|---|---|
| **Décision** | Acte par lequel une instance habilitée tranche : poursuivre, refuser, poursuivre sous réserve, suspendre ou annuler. | F3 §8.1 | FAIT |
| **Valeurs de décision** | `GO`, `GO_WITH_RESERVES`, `NO_GO`, `HOLD`, `CANCELLED` — cinq valeurs, orthographe à underscore. Le pilote v1 n'en connaît que trois, écrites avec des espaces. | F3 §8.1 ; décision **A1** | FAIT |
| **Recommandation** | Avis motivé d'un agent. Ne vaut jamais décision. | F3 §2 | FAIT |
| **Réserve** | Condition attachée à une acceptation, identifiée, qualifiée, affectée à un responsable, avec tâche, échéance et méthode de vérification. | F3 §8.4 | FAIT |
| **Anomalie** | Défaut constaté, qualifié par une gravité S0 à S3. | F3 §8.2 | FAIT |
| **Gravité** | Niveau d'une anomalie : S0 critique, S1 majeure, S2 modérée, S3 mineure. | F3 §8.2 | FAIT |
| **Écart** | Divergence entre ce qui était autorisé ou spécifié et ce qui est livré, y compris une modification hors périmètre. | F2 §15, F3 §11.2 | FAIT |
| **Preuve** | Élément vérifiable produit à l'appui d'une affirmation : commit, sortie de commande, résultat de test, rapport CI, fichier inspecté, journal, reproduction, scan, décision humaine, comparaison avant/après. | F3 §9 | FAIT |
| **Statut de preuve** | Qualité d'une preuve : `directly_verified`, `reproduced`, `cross_checked`, `declared_only`, `partial`, `missing`, `invalid`. | F3 §9 | FAIT |
| **`declared_only`** | Preuve constituée d'une simple déclaration. Insuffisante pour valider un critère critique. | F3 §9 | FAIT |
| **Statut de contrôle** | Résultat d'une vérification : `PASS`, `FAIL`, `PARTIAL`, `N/A`, `NOT_CHECKED`. | F3 §9 | FAIT |
| **Revue de préparation** (`readiness_review`) | Contrôle effectué **avant exécution** : vérifie que le cadrage, les critères et les conditions de démarrage sont réunis. Elle juge l'aptitude à démarrer, pas un résultat livré. | F3 §14 ; décision **C19** | FAIT |
| **Audit de sprint** (`sprint_audit`) | Contrôle effectué **après exécution** : vérifie le mandat, les tâches, les tests et les critères sur un résultat livré. Il juge un produit, pas une intention. | F3 §8.3 ; décision **C19** | FAIT |
| **Dette technique** | Ensemble des réserves et défauts acceptés, avec plan de résolution. | F2 §8.6 | FAIT |
| **Risque résiduel** | Risque subsistant après traitement, à accepter explicitement. | F3 §4.3 | FAIT |
| **Mesure compensatoire** | Contrôle de substitution lorsqu'une protection technique est absente. | F3 §4.3 | FAIT |

---

## 5. Changements

| Terme | Définition | Source | Statut |
|---|---|---|---|
| **Changement** | Toute modification affectant périmètre, exigence, règle métier, architecture, donnée, sécurité, mandat, sprint, décision validée ou niveau de gouvernance. | F3 §10 | FAIT |
| **Identifiant de changement** | `CHG-AAAA-NNNN` pour un changement planifié, `URG-AAAA-NNNN` pour une urgence. | F3 §10.2 | FAIT |
| **Urgence** | Situation justifiant un confinement immédiat, sans jamais supprimer la traçabilité ni l'audit a posteriori. | F3 §10.6 | FAIT |
| **Réversibilité** | Capacité à revenir en arrière : R0 facile, R1 correction simple, R2 migration importante, R3 difficile ou irréversible. | F3 §10.4 | FAIT |

---

## 6. Permissions

| Terme | Définition | Source | Statut |
|---|---|---|---|
| **Permission procédurale** | Règle de comportement non imposée techniquement. | F3 §12 | FAIT |
| **Permission technique** | Restriction effectivement imposée par l'environnement : système de fichiers, utilisateur distinct, branche protégée, CI, outil, contrôle d'accès. | F3 §12 | FAIT |
| **Permission contrôlée a posteriori** | Action techniquement possible, vérifiée après exécution. | F3 §12 | FAIT |
| **Classification de permission** | `technical_enforced`, `procedural_only`, `post_checked`, `not_available`, `unknown`. | F3 §12 | FAIT |
| **`technical_enforced`** | N'est employable qu'après vérification effective du harnais. Une configuration présente n'est pas une restriction active. | F3 §12, cartographie §11 | FAIT |
| **`unknown`** | Permission non vérifiée. Ne doit jamais être présentée comme une garantie. | F3 §12 | FAIT |
| **Violation de permission** | Dépassement du périmètre autorisé, qualifié P0 à P3. | F3 §13 | FAIT |
| **Moindre privilège** | Chaque rôle ne dispose que des capacités nécessaires à son mandat. | F3 §12 | FAIT |
| **Indépendance procédurale** | Indépendance d'audit obtenue par les règles et la séparation des tours, sans garantie technique. | F3 §3.3 | FAIT |
| **Indépendance technique** | Indépendance obtenue par une contrainte réellement imposée par l'environnement. À ne déclarer que si elle est prouvée. | F3 §3.3 | FAIT |

---

## 7. Statuts épistémiques

Ces cinq statuts qualifient tout énoncé important. Ils ne sont pas décoratifs : ils déterminent ce qui peut être affirmé.

| Statut | Signification | Usage |
|---|---|---|
| `FAIT` | Établi et vérifiable dans une source citée. | Peut être affirmé sans réserve. |
| `HYPOTHÈSE` | Admis provisoirement, non vérifié. | Doit être identifié comme tel. |
| `RECOMMANDATION` | Proposition du rédacteur ou d'un agent. | Ne vaut pas décision. |
| `À ARBITRER` | Dépend d'une décision humaine non prise. | Ne doit pas être présenté comme fixé. |
| `INCONNU` | Information absente. | Ne doit jamais devenir une règle. |

> Une information `INCONNU` transformée en règle officielle est une faute documentaire, pas une simplification.

---

## 8. Confusions à éviter

| Ne pas confondre | Avec | Pourquoi |
|---|---|---|
| Rapport | Preuve | Un rapport raconte ; une preuve démontre. Le rapport de BUILDER est une source d'information, pas la source première de vérité. |
| Recommandation | Décision | Seul le VALIDATOR décide. |
| Autorisation | Consommation | Autoriser n'est pas agir ; consommer n'est pas exécuter. |
| Achèvement | Acceptation | Un résultat produit n'est pas un résultat accepté. |
| Réserve | Anomalie | Une anomalie est un défaut ; une réserve est une condition acceptée, tracée et planifiée. |
| Profil | Implémentation | Le profil règle le niveau de contrôle ; l'implémentation fournit des moyens techniques. |
| Revue de préparation | Audit de sprint | Le premier vérifie l'aptitude à démarrer, **avant** exécution ; le second vérifie un résultat livré, **après** exécution. Deux contrôles distincts, aux preuves et aux décideurs différents (C19). |
| Changement | Correction | Une correction reste dans le périmètre autorisé ; un changement le modifie. |
| Jeton | Preuve cryptographique | Un identifiant de transition est traçable, pas infalsifiable. |
| Permission déclarée | Permission appliquée | Déclarer n'est pas imposer. |
| `state.json` | `state.md` | L'un est la source, l'autre une vue générée. |
| `NOT_CHECKED` | `PASS` | L'absence de contrôle n'est pas un succès. |
| `declared_only` | Vérifié | Une déclaration n'est pas une vérification. |
| Document de référence | Document produit | Une source alimente la documentation ; elle n'en fait pas partie. |
| Mandat | Sprint | Le mandat borne l'action ; le sprint borne la durée et le contenu. |

---

## 9. Identifiants

| Préfixe | Objet | Format | Source |
|---|---|---|---|
| `TR-` | Transition | `TR-AAAA-NNNN` | F3 §6.4 |
| `CHG-` | Changement | `CHG-AAAA-NNNN` | F3 §10.2 |
| `URG-` | Urgence | `URG-AAAA-NNNN` | F3 §10.2 |
| `CP1` `CP2` `CP3` | Checkpoints | fixe | F3 §14 |
| `S0` → `S3` | Gravité d'anomalie | fixe | F3 §8.2 |
| `P0` → `P3` | Gravité de violation de permission | fixe | F3 §13 |
| `R0` → `R3` | Réversibilité | fixe | F3 §10.4 |

> Un identifiant n'est jamais réutilisé. Un identifiant consommé, expiré ou annulé reste dans l'historique.

---

## 10. Vocabulaire à éviter

| À éviter | Préférer | Raison |
|---|---|---|
| « sécurisé », « protégé » | « permission technique vérifiée » + preuve | Aucune garantie sans preuve |
| « validé » pour une proposition | « proposé », « à valider » | Confondre proposition et décision |
| « vérifié » sans trace | « contrôlé — preuve : … » | Affirmation sans preuve |
| « conforme » sans référentiel | « conforme à `<document>` § … » | Conformité sans référence est vide |
| « tout est prêt » | état par checkpoint, avec preuves | Fausse impression de sécurité |
| « l'IA a validé » | « l'IA a recommandé » | Seul l'humain valide |
| « automatique » pour un contrôle procédural | « procédural » ou « technique » selon preuve | Nature du contrôle |

---

## 11. Arbitrages et effet sur le vocabulaire

| Terme | État | Effet |
|---|---|---|
| Valeurs de décision | **Tranché (A1)** | 5 valeurs, orthographe à underscore |
| Forme de sérialisation de `state.json` | **Tranché (A2)** | v2.0 structure normative ; pilote v1.0 écart historique |
| Reçu pour ORCHESTRATOR | **Tranché (C26)** | `docs/governance/receipts/` — `protocol/transition_policy.md` §5.7 |
| Statut du DOCUMENTATION BUILDER | **Tranché (A5)** | Rôle documentaire auxiliaire, distinct des trois agents et du VALIDATOR |
| Revue de préparation / audit de sprint | **Tranché (C19)** | Deux contrôles distincts : avant exécution, après exécution |
| Nom du README de documentation | **Tranché (A4)** | `documentation/README.md` |
| Versionnement | **Tranché (A7)** | 5 versions distinctes : protocole, profil, schéma, mandat, document |

---

## 12. Maintenance

- Un terme nouveau n'entre ici qu'avec une source ou un statut explicite.
- Un terme retiré reste tracé dans l'historique de version.
- Toute divergence terminologique constatée dans un autre document est signalée au VALIDATOR, jamais corrigée unilatéralement.

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 1) |
| 0.2 | 2026-11-20 | Intégration A5 (rôle documentaire auxiliaire) et C19 (`readiness_review` / `sprint_audit`) |
| 0.3 | 2026-11-20 | A2 (v2.0 normative) et C26 (reçu ORCHESTRATOR) intégrés |
