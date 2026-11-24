# Référence de frontmatter — permissions OpenCode observées

| Champ | Valeur |
|---|---|
| Version documentaire | 0.1 |
| Date | 2026-11-21 |
| Statut | **Référence descriptive — portée limitée au constat cité** |
| Source du constat | `agent_permissions.md`, inspection du pilote datée du 2026-11-20 |

## 1. Portée

Cette page résume la forme employée par les fichiers d’agents examinés dans le pilote `C:\demo_web - Copie`. Elle ne constitue ni une spécification exhaustive d’OpenCode, ni une garantie que le moteur applique les règles comme prévu. Pour une configuration ou une version différente, vérifier la documentation correspondante et tester le comportement dans l’environnement concerné.

La source de référence pour le constat du pilote est [`agent_permissions.md`](agent_permissions.md). Les règles AKORIS relatives à la classification et aux preuves restent dans [`../../protocol/permission_policy.md`](../../protocol/permission_policy.md).

## 2. Forme observée

Le constat décrit les permissions de frontmatter comme une liste ordonnée d’objets ayant les champs `action`, `resource` et `effect`. Il rapporte l’utilisation de wildcards et indique que, dans la configuration OpenCode V2 observée, la dernière règle correspondante l’emporte.

Schéma illustratif, non exhaustif et non directement copié d’un fichier réel :

```yaml
permissions:
  - action: edit
    resource: "state.json"
    effect: deny
  - action: edit
    resource: "audit_report/**"
    effect: allow
```

Cet extrait illustre uniquement les noms de champs et la forme rapportés dans le constat. Il ne constitue pas une configuration recommandée pour un projet donné.

## 3. Valeurs relevées dans le pilote

Les règles examinées utilisent notamment les actions `edit`, `shell` et `subagent`, ainsi que les effets `deny` et `allow`. Le relevé indique zéro règle `ask` dans les trois configurations de rôle recensées. Cela ne permet pas de conclure que ces valeurs forment la liste complète ou actuelle des possibilités de l’outil.

Les ressources observées comprennent des chemins de fichiers, des motifs tels que `src/**`, et des commandes shell Git. La portée réelle des motifs et des règles doit être vérifiée dans la version et le contexte d’exécution utilisés.

## 4. Ordre et chevauchement

Selon le constat du pilote, OpenCode V2 applique la dernière règle correspondante gagnante. L’ordre peut donc modifier le résultat lorsque plusieurs règles correspondent à une même action et une même ressource. Le relevé signale notamment que la règle `edit *` d’AUDITOR est suivie d’une règle autorisant `audit_report/**`.

Ne réordonnez ni ne copiez une liste de règles sans vérifier les effets de chevauchement dans le moteur effectivement utilisé. Le comportement observé dans un pilote n’est pas une certification pour un autre environnement.

## 5. Ce que cette page ne certifie pas

La présence d’une règle dans le frontmatter ne prouve pas qu’elle est appliquée. Le constat du pilote rapporte l’absence de tests contradictoires T1 à T5, un contournement possible de règles d’édition par shell et des asymétries entre les agents. Les permissions demeurent `unknown` dans le constat.

Pour classer une permission `technical_enforced`, appliquer toutes les conditions et exigences de preuve de [`../../protocol/permission_policy.md`](../../protocol/permission_policy.md) §2.1. Cette référence de frontmatter ne remplace pas ces tests.
