# AKORIS sur OpenCode — implémentation de référence

| Champ | Valeur |
|---|---|
| Version documentaire | 0.1 |
| Date | 2026-11-21 |
| Statut | **Descriptif — non normatif** |
| Portée | Présentation de l’implémentation OpenCode observée dans le pilote `demo_web` |

## 1. Objet et frontière

Ce dossier décrit une implémentation de référence d’AKORIS dans OpenCode. Il documente les configurations observées, leurs prérequis et leurs limites. Il ne définit pas le cadre AKORIS et ne transforme pas une configuration lue en garantie technique.

Les règles de gouvernance restent dans `../../protocol/`. La politique générale des permissions est définie dans [`../../protocol/permission_policy.md`](../../protocol/permission_policy.md). Le constat daté de la configuration du pilote est [`agent_permissions.md`](agent_permissions.md).

## 2. Documents de cette implémentation

- [`frontmatter_reference.md`](frontmatter_reference.md) décrit la structure de permissions observée dans les fichiers d’agents et précise les limites de cette description.
- [`environment_requirements.md`](environment_requirements.md) recense les éléments observés et les vérifications préalables à une reproduction.
- [`limitations.md`](limitations.md) expose les restrictions non éprouvées et les limites constatées dans le pilote.
- [`agent_permissions.md`](agent_permissions.md) contient le relevé détaillé des règles observées, les classifications et le statut des tests.

## 3. Configuration observée

Le relevé du 2026-11-20 porte sur `C:\demo_web - Copie`. Il mentionne `opencode.json`, `agents.md`, `contexte.md` et les fichiers d’agents BUILDER, ORCHESTRATOR et AUDITOR sous `.opencode/agents/`.

Le fichier `opencode.json` observé charge `agents.md` et `contexte.md` comme instructions. Les fichiers d’agents contiennent des règles de permissions. Le détail est dans [`agent_permissions.md`](agent_permissions.md), et non réénoncé ici.

## 4. État de vérification

Le constat disponible est documentaire : les fichiers de configuration ont été lus, mais aucun test contradictoire T1 à T5 n’a été exécuté. En conséquence, le document source classe les permissions `unknown`, ne certifie pas la protection de `main` et déclare T1 à T5 `NON EXÉCUTÉS`.

Cette implémentation ne doit donc pas être présentée comme une installation opérationnelle certifiée. Toute mise à jour de son état exige l’inspection de l’environnement concerné, des preuves et la mise à jour du constat technique selon [`agent_permissions.md`](agent_permissions.md).

## 5. Références AKORIS

- [Carte documentaire](../../reference/document_map.md)
- [Socle de gouvernance](../../protocol/governance_core.md)
- [Politique des permissions](../../protocol/permission_policy.md)
- [Politique d’audit](../../protocol/audit_policy.md)
- [Modèle d’état](../../protocol/state_model.md)
