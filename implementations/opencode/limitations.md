# Limites — implémentation OpenCode observée

| Champ | Valeur |
|---|---|
| Version documentaire | 0.1 |
| Date | 2026-11-21 |
| Statut | **Descriptif — fondé sur le constat du pilote** |
| Source principale | [`agent_permissions.md`](agent_permissions.md), inspection du 2026-11-20 |

## 1. Portée et prudence d’interprétation

Les points ci-dessous décrivent la configuration examinée dans le pilote `C:\demo_web - Copie`. Ils ne caractérisent pas automatiquement toute installation d’OpenCode ni une configuration ultérieure. La source est un constat documentaire non normatif ; elle ne remplace pas les politiques AKORIS.

## 2. Effectivité non démontrée

Les fichiers de configuration ont été lus, mais aucun test d’exécution n’a été réalisé. En conséquence :

- les permissions rapportées restent classées `unknown` ;
- aucune permission n’est certifiée `technical_enforced` ;
- la protection de `main` reste `unknown` ;
- T1 à T5 restent `NON EXÉCUTÉS`.

Une règle présente dans un fichier n’est pas, à elle seule, la preuve d’un refus effectif. Pour la classification, suivre [`../../protocol/permission_policy.md`](../../protocol/permission_policy.md) §2.1 et §7.

## 3. Limites rapportées dans le pilote

Le constat `agent_permissions.md` relève les éléments suivants dans la configuration examinée :

- aucune permission globale et aucune règle globale de refus par défaut n’y ont été constatées ;
- les règles d’édition ne couvrent pas nécessairement l’écriture via shell ; le contournement de `state.json` est signalé comme probable, mais non testé ;
- les configurations des agents sont asymétriques ; par exemple, `agents.md` n’est pas protégé contre l’édition par ORCHESTRATOR dans les règles relevées ;
- la liste AUDITOR dépend de l’ordre des règles : l’autorisation de `audit_report/**` suit le refus global `edit *` ;
- aucune protection effective de `main` n’a été constatée par les tests, car aucun test n’a été exécuté.

Ces constats ne doivent pas être reformulés comme une preuve qu’une action particulière réussira ou échouera. Leur statut demeure celui indiqué dans le document source.

## 4. Tests et preuves

Les tests définis dans [`../../protocol/permission_policy.md`](../../protocol/permission_policy.md) sont : T1 édition directe de `state.json` par BUILDER ; T2 écriture par shell ; T3 édition de `src/**` par ORCHESTRATOR ; T4 push ou fusion non autorisé vers une branche protégée autre que `main` ; T5 tentative équivalente vers `main`.

Aucun de ces tests n’est déclaré exécuté dans le constat disponible. Le contrôle complémentaire consistant à demander à AUDITOR d’éditer `src/**` n’est pas T4 et ne reçoit pas d’identifiant T1–T5.

## 5. Conséquence documentaire

Les descriptions de configuration doivent rester séparées des garanties effectivement éprouvées. Avant de présenter une permission comme techniquement imposée, il faut disposer de la configuration pertinente, d’un test contradictoire montrant le refus, d’une comparaison des agents concernés et d’une vérification des voies de contournement, conformément à `protocol/permission_policy.md` §2.1.

La mise à jour de ces statuts appartient à un contrôle réalisé dans l’environnement concerné avec conservation des preuves. Cette page n’exécute ni ne remplace ces contrôles.
