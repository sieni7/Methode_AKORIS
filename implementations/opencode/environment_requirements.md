# Prérequis d’environnement — implémentation OpenCode

| Champ | Valeur |
|---|---|
| Version documentaire | 0.1 |
| Date | 2026-11-21 |
| Statut | **Descriptif — prérequis observés, non certification** |
| Référence de l’inspection | `agent_permissions.md`, 2026-11-20 |

## 1. Portée

Cette page consigne les éléments nécessaires pour comprendre ou reproduire le constat d’implémentation décrit dans [`agent_permissions.md`](agent_permissions.md). Elle ne définit pas une matrice de compatibilité officielle et ne spécifie pas de version minimale d’OpenCode, du système d’exploitation ou de Git : ces informations ne sont pas établies dans le constat disponible.

AKORIS reste agnostique de l’outil. Ces éléments ne s’appliquent qu’à l’implémentation OpenCode examinée.

## 2. Éléments observés dans le pilote

L’inspection documentaire porte sur le projet `C:\demo_web - Copie` et mentionne les fichiers suivants :

- `opencode.json` ;
- `agents.md` et `contexte.md`, chargés comme instructions selon la configuration relevée ;
- `.opencode/agents/builder.md` ;
- `.opencode/agents/orchestrator.md` ;
- `.opencode/agents/auditor.md`.

Le constat rapporte 22 règles de permission pour BUILDER, 18 pour ORCHESTRATOR et 13 pour AUDITOR. Il décrit leur format, leurs effets observés et les limites de chaque configuration dans [`agent_permissions.md`](agent_permissions.md). Ces nombres sont une photographie de l’inspection du 2026-11-20, pas des exigences générales.

## 3. Vérifications préalables à une reproduction

Avant de reproduire ou mettre à jour ce constat :

1. confirmer le chemin et l’identité du dépôt inspecté ;
2. relever la version et la méthode de lancement d’OpenCode réellement utilisées ;
3. vérifier quels fichiers de configuration et d’instructions sont chargés ;
4. vérifier les fichiers d’agents et leurs règles de permissions actuelles ;
5. distinguer les essais effectués sur une copie de test de ceux effectués dans le pilote ;
6. conserver les commandes, sorties et preuves conformément à `protocol/permission_policy.md` §7 ;
7. ne pas utiliser de secrets ou de données de production dans un environnement de test.

Ces étapes sont des consignes de préparation documentaire ; elles ne signifient pas qu’une vérification ou un test a eu lieu.

## 4. Conditions de test des permissions

Les tests T1 à T5 nécessitent que les agents soient lancés sous leur configuration d’exécution propre. T4 et T5 portent sur des tentatives de fusion ou de push non autorisé vers des branches protégées dans un dépôt de test ; un simple changement de branche n’est pas le test. Voir [`../../protocol/permission_policy.md`](../../protocol/permission_policy.md) §7.2 pour les définitions canoniques.

Un environnement partagé, une configuration lue ou une copie locale sans protection distante comparable ne suffisent pas à prouver la restriction technique de l’environnement cible. Documenter séparément les prérequis réellement satisfaits et ceux qui restent inconnus.

## 5. État déclaré dans la source

Au moment de l’inspection consignée dans `agent_permissions.md` : T1 à T5 sont `NON EXÉCUTÉS`, les permissions sont `unknown` et la protection de `main` est `unknown`. Cette page ne met pas ces statuts à jour. Toute évolution doit reposer sur de nouvelles preuves dans l’environnement effectivement concerné.
