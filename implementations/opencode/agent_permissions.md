# Permissions observées — implémentation OpenCode

| Champ | Valeur |
|---|---|
| Version | 0.4 |
| Date | 2026-11-20 |
| Statut | **CONSTAT — non normatif** |
| Portée | Configuration de permissions du projet pilote `demo_web` |
| Autorité | Constat technique, opposable par sa preuve |
| Vague | 3 |

**Sources citées :** `PP` = `protocol/permission_policy.md` · `GC` = `protocol/governance_core.md` · documentation OpenCode V2 (agents, permissions) · fichiers du projet pilote · décision VALIDATOR d’harmonisation documentaire de T4 (2026-11-20).

---

## 0. Objet

Ce document enregistre **ce qui est réellement configuré**, et **ce qui n'a pas pu être vérifié**.

Il ne définit aucune règle de gouvernance. Les règles sont dans `permission_policy.md`.

> **Principe directeur (`GC-36`, `GC-40`).** Une permission déclarée n'est pas une permission appliquée. Ce document ne certifie rien qu'il n'ait constaté.

---

## 1. Périmètre de l'inspection

| Élément | État |
|---|---|
| Environnement inspecté | `C:\demo_web - Copie` |
| Date de l'inspection | 2026-11-20 |
| Fichiers examinés | `opencode.json`, `.opencode/agents/builder.md`, `.opencode/agents/orchestrator.md`, `.opencode/agents/auditor.md` |
| Fichiers non examinés | Aucun des quatre agents |
| Tests d'exécution réalisés | **Aucun** — T1 à T5 restent `NON EXÉCUTÉ` (§6) |
| Conclusion générale | Configuration présente, **effectivité non démontrée** |

**Limite majeure :** l'inspection est documentaire. Les quatre configurations d'agents ont été lues, mais aucun test contradictoire n'a été exécuté : une règle lue n'est pas une règle appliquée. Les classifications qui suivent en tiennent compte.

---

## 2. Configuration globale

```json
{
  "$schema": "https://opencode.ai/config.json",
  "instructions": ["agents.md", "contexte.md"]
}
```

| Constat | Conséquence |
|---|---|
| Aucune permission globale définie | Aucun filet de sécurité commun |
| Aucune règle de base `deny` | Tout ce qui n'est pas listé est **autorisé** |
| `instructions` charge deux documents | `agents.md` et `contexte.md` entrent dans le contexte de chaque agent |

**Le modèle est une liste noire, pas une liste blanche.** Une ressource oubliée est ouverte par défaut.

---

## 3. Configuration de BUILDER

Fichier : `.opencode/agents/builder.md`, frontmatter `permissions`.

| Constat | Valeur |
|---|---|
| Format | Liste ordonnée de `{action, resource, effect}` |
| Conformité au schéma OpenCode V2 | **Oui** — dernière règle gagnante, wildcards supportés |
| Nombre de règles | 22 |
| Règles `allow` | 0 |
| Règles `ask` | 0 |
| Règles `deny` | 22 |

### 3.1 Règles constatées

| # | Action | Ressource | Effet |
|---|---|---|---|
| 1 | `edit` | `state.json` | deny |
| 2 | `edit` | `state.md` | deny |
| 3 | `edit` | `current_sprint.md` | deny |
| 4 | `edit` | `audit_report/**` | deny |
| 5 | `edit` | `debt_report/**` | deny |
| 6 | `edit` | `docs/**` | deny |
| 7 | `edit` | `sprints/**` | deny |
| 8 | `edit` | `templates/**` | deny |
| 9 | `edit` | `data/**` | deny |
| 10 | `edit` | `agents.md` | deny |
| 11 | `edit` | `contexte.md` | deny |
| 12 | `edit` | `getting_started.md` | deny |
| 13 | `edit` | `README.md` | deny |
| 14 | `edit` | `opencode.json` | deny |
| 15 | `edit` | `.opencode/**` | deny |
| 16 | `subagent` | `*` | deny |
| 17 | `shell` | `git merge *` | deny |
| 18 | `shell` | `git push --force*` | deny |
| 19 | `shell` | `git push -f *` | deny |
| 20 | `shell` | `git checkout main*` | deny |
| 21 | `shell` | `git switch main*` | deny |
| 22 | `shell` | `git reset --hard*` | deny |

**Lecture :** la configuration protège correctement les fichiers de gouvernance contre les outils d'édition, et bloque six commandes Git destructrices ou contraires au protocole. C'est un dispositif sérieux, pas décoratif.

---

## 3bis. Configuration d'ORCHESTRATOR

Fichier : `.opencode/agents/orchestrator.md`, frontmatter `permissions`.

| Constat | Valeur |
|---|---|
| Format | Liste ordonnée de `{action, resource, effect}` |
| Nombre de règles | 18 |
| Règles `allow` | 0 |
| Règles `ask` | 0 |
| Règles `deny` | 18 |

### 3bis.1 Règles constatées

| # | Action | Ressource | Effet |
|---|---|---|---|
| 1 | `edit` | `src/**` | deny |
| 2 | `edit` | `tests/**` | deny |
| 3 | `edit` | `data/**` | deny |
| 4 | `edit` | `sprint_report/**` | deny |
| 5 | `edit` | `audit_report/**` | deny |
| 6 | `edit` | `package.json` | deny |
| 7 | `edit` | `package-lock.json` | deny |
| 8 | `edit` | `tsconfig.json` | deny |
| 9 | `edit` | `next.config.*` | deny |
| 10 | `edit` | `vitest.config.*` | deny |
| 11 | `edit` | `playwright.config.*` | deny |
| 12 | `edit` | `opencode.json` | deny |
| 13 | `edit` | `.opencode/**` | deny |
| 14 | `subagent` | `*` | deny |
| 15 | `shell` | `git merge *` | deny |
| 16 | `shell` | `git push --force*` | deny |
| 17 | `shell` | `git push -f *` | deny |
| 18 | `shell` | `git reset --hard*` | deny |

**Constat notable :** `state.json` n'est **pas** refusé à ORCHESTRATOR — cohérent avec son rôle de seul rédacteur (`agents.md`). En revanche, **`agents.md` n'est pas protégé** : l'agent peut éditer le document qui fait foi sur son propre contrat. Aucune règle `edit` ne couvre `docs/**`, `sprints/**`, `templates/**`, `current_sprint.md` ni `state.md`.

---

## 3ter. Configuration d'AUDITOR

Fichier : `.opencode/agents/auditor.md`, frontmatter `permissions`.

| Constat | Valeur |
|---|---|
| Format | Liste ordonnée de `{action, resource, effect}` |
| Nombre de règles | 13 |
| Règles `allow` | 1 |
| Règles `ask` | 0 |
| Règles `deny` | 12 |

### 3ter.1 Règles constatées

| # | Action | Ressource | Effet |
|---|---|---|---|
| 1 | `edit` | `*` | deny |
| 2 | `edit` | `audit_report/**` | **allow** |
| 3 | `edit` | `opencode.json` | deny |
| 4 | `edit` | `.opencode/**` | deny |
| 5 | `subagent` | `*` | deny |
| 6 | `shell` | `git commit *` | deny |
| 7 | `shell` | `git push *` | deny |
| 8 | `shell` | `git merge *` | deny |
| 9 | `shell` | `git checkout *` | deny |
| 10 | `shell` | `git switch *` | deny |
| 11 | `shell` | `git reset *` | deny |
| 12 | `shell` | `git clean *` | deny |
| 13 | `shell` | `git rm *` | deny |

**Lecture de l'ordre :** `edit *` est refusé en règle 1, puis `audit_report/**` est autorisé en règle 2. OpenCode V2 applique la **dernière règle correspondante gagnante** : AUDITOR peut donc écrire son rapport, et rien d'autre par l'outil d'édition. C'est la seule liste blanche partielle du pilote. Elle est **fragile** : toute règle ajoutée après la ligne 2 sur un chemin chevauchant `audit_report/**` annulerait l'autorisation.

**Constat notable :** le refus global ne porte que sur `edit` et `subagent`. Aucune règle `shell` n'interdit l'écriture par redirection (`Set-Content`, `>`), ni `git add`, ni `npm`. L'indépendance d'AUDITOR reste donc **procédurale**, pas technique.

---

## 4. Classification

### 4.1 Application stricte de `PP` §2.1

| Condition | État |
|---|---|
| 1. La règle existe | **Remplie** |
| 2. Le harnais la prend en compte | **Non testée** |
| 3. Cohérence entre tous les agents | **Non vérifiée** |
| 4. Absence de chemin de contournement | **Non remplie** — voir §5.1 |

**Conclusion : aucune permission ne peut être classée `technical_enforced` à ce jour.** Toutes restent `unknown` au sens de `PP` §2.

### 4.2 Tableau

| Objet | Rôle | Mécanisme constaté | Classification |
|---|---|---|---|
| `state.json` | BUILDER | `edit` refusé | `unknown` — contournement possible |
| `state.md` | BUILDER | `edit` refusé | `unknown` |
| `current_sprint.md` | BUILDER | `edit` refusé | `unknown` |
| `audit_report/**` | BUILDER | `edit` refusé | `unknown` |
| `debt_report/**` | BUILDER | `edit` refusé | `unknown` |
| `docs/**` | BUILDER | `edit` refusé | `unknown` |
| `sprints/**`, `templates/**`, `data/**` | BUILDER | `edit` refusé | `unknown` |
| `agents.md`, `contexte.md`, `README.md` | BUILDER | `edit` refusé | `unknown` |
| `opencode.json`, `.opencode/**` | BUILDER | `edit` refusé | `unknown` |
| `git merge` | BUILDER | `shell` refusé | `unknown` |
| `git push --force` | BUILDER | `shell` refusé | `unknown` |
| `git reset --hard` | BUILDER | `shell` refusé | `unknown` |
| `src/**` | BUILDER | Autorisé (non listé) | Conforme au mandat |
| `state.json` | ORCHESTRATOR | Autorisé (non listé) — rédacteur normal | `unknown` sur l'effectivité |
| `state.json` | AUDITOR | `edit *` refusé, contournable par `shell` | `unknown` |
| `src/**` | AUDITOR | `edit *` refusé, contournable par `shell` | `unknown` |
| `src/**` | ORCHESTRATOR | `edit src/**` refusé, contournable par `shell` | `unknown` |
| `agents.md` | ORCHESTRATOR | **Non protégé** — aucune règle | **Constat de faille, effectivité `unknown`** |
| `audit_report/**` | AUDITOR | `edit` autorisé après refus global | `unknown` — dépend de l'ordre des règles |
| Secrets | Tous | **Aucune règle constatée** | `unknown` |
| `main` | Tous | **Aucune protection constatée** | `unknown` |

> **Nuance importante.** `unknown` ne signifie pas « non protégé ». Cela signifie « non prouvé ». La distinction est exactement celle que le socle impose.

---

## 5. Failles constatées

### 5.1 Contournement par `shell`

`edit` couvre les outils d'édition. Il ne couvre **pas** l'écriture par shell :

```text
Set-Content state.json "{}"
"..." > state.md
Get-Content x | Set-Content state.json
```

Aucune règle `shell` ne porte sur ces écritures. La protection de `state.json` est donc **contournable par un moyen trivial**, sans même une intention malveillante — une redirection suffit.

**Gravité : P1** (état falsifié) si exploité.

### 5.2 Absence de liste blanche

Sans règle de base `{action: "*", resource: "*", effect: "deny"}`, toute ressource non listée est ouverte. Une nouvelle arborescence ajoutée au projet n'est protégée par défaut.

### 5.3 Asymétrie entre agents

Les quatre configurations ont été comparées à la matrice de `agents.md` §6. Les écarts constatés :

| Interdiction | BUILDER | ORCHESTRATOR | AUDITOR |
|---|---|---|---|
| Écrire `state.json` (`edit`) | refusé | **autorisé** (rôle prévu) | refusé (`*`) |
| Écrire `agents.md` | refusé | **non protégé** | refusé (`*`) |
| Écrire `src/**` | **non protégé** (rôle prévu) | refusé | refusé (`*`) |
| `git checkout main*` | refusé | **non protégé** | refusé (`*`) |
| `git commit` | **non protégé** | **non protégé** | refusé |

**Conclusion :** l'asymétrie est réelle et documentée. Une même ressource peut être refusée à un agent et ouverte à un autre, ce qui est parfois conforme au rôle (`state.json` pour ORCHESTRATOR) et parfois non (`agents.md` pour ORCHESTRATOR, `src/**` pour BUILDER par construction). Aucun de ces écarts n'est corrigé ici : ce document constate.

### 5.4 Absence de preuve de refus

Aucun rapport du pilote ne contient de trace montrant qu'une édition a été refusée. La configuration est **présumée** active.

---

## 6. Tests à exécuter

| # | Test | Attendu | État |
|---|---|---|---|
| T1 | BUILDER édite `state.json` | Refus | **NON EXÉCUTÉ** |
| T2 | BUILDER écrit `state.json` par shell | Refus | **NON EXÉCUTÉ** |
| T3 | ORCHESTRATOR édite `src/**` | Refus | **NON EXÉCUTÉ** |
| T4 | Tentative de fusion ou de push non autorisé vers une branche protégée autre que `main`, dans un dépôt de test | Refus | **NON EXÉCUTÉ** |
| T5 | Tentative équivalente de fusion ou de push non autorisé vers `main`, dans un dépôt de test (décision **C29**) | Refus | **NON EXÉCUTÉ** — test préparé |

Un simple changement de branche (`checkout` ou `switch`) ne suffit pas, à lui seul, à tester le blocage d’une fusion ou d’un push.

**Contrôle complémentaire — hors T1 à T5 :** demander à AUDITOR d’éditer `src/**` vérifie les permissions inter-rôles. Ce contrôle n’est pas T4 et ne reçoit aucun nouvel identifiant de test ; son état reste non vérifié.

Chaque test doit produire : date, commande exacte, sortie, verdict, emplacement de la trace.

**Statut au 2026-11-20 : les cinq tests sont `NON EXÉCUTÉ`.**

Justification : T1 à T5 supposent de lancer chaque agent dans le projet pilote `C:\demo_web - Copie`, sous sa propre configuration, et de tenter l'action interdite. T4 porte sur une branche protégée autre que `main`, T5 sur la protection de `main`, maintenue `unknown` par la décision C29. Le rôle documentaire ne peut pas exécuter ces tests : il n'a ni le mandat ni l'environnement d'exécution des agents. Aucun résultat n'est donc disponible, et aucun ne sera simulé.

Conséquence : la configuration est **lue**, jamais **éprouvée**. La classification `unknown` de §4.2 s'applique sans exception.

Tant que T2 n'est pas exécuté, la faille §5.1 reste **probable** et non **constatée** — ce qui suffit à interdire `technical_enforced`.

---

## 7. Conséquences par profil

| Profil | Conséquence |
|---|---|
| Lite | Acceptable si les `unknown` sont déclarés |
| Standard | Acceptable avec mesures compensatoires documentées |
| Reinforced | **Non conforme** : une protection technique absente exige une mesure compensatoire explicite (`profile_reinforced.md` §5) |

> **Décision C29 — mesures compensatoires.** La protection technique de `main` n'est **pas certifiée** : son statut reste `unknown`. Le test dédié **T5 — Vérification de la protection effective de main** est préparé, avec un statut initial `NON EXÉCUTÉ`. Aucune permission n'est classée `technical_enforced` sur la seule base des fichiers de configuration.

Mesures compensatoires à appliquer tant que T5 n'a pas produit de résultat concluant :

| # | Mesure | Effet |
|---|---|---|
| 1 | Audit systématique de `state.json` avant chaque transition | Détecte une divergence d'état avant consommation |
| 2 | Comparaison état / reçu à chaque consommation | Rend visible une divergence bloquante (`A2`) |
| 3 | Revue humaine des diffs avant fusion | Substitue un contrôle procédural au contrôle technique absent |
| 4 | Utilisation d'un utilisateur système distinct | Réduit le risque de contournement par shell |
| 5 | Décision humaine de fusion distincte de l'acceptation du sprint | Empêche la fusion déduite (`DP` §9) |

Ces mesures sont **procédurales** : elles ne transforment pas un `unknown` en `technical_enforced`.

---

## 8. Mise à jour de ce document

| Événement | Action |
|---|---|
| Test exécuté | Renseigner §6, mettre à jour §4.2 |
| Configuration modifiée | Réviser §3 et dater |
| Nouvel agent inspecté | Compléter §4.2 |
| Faille corrigée | Conserver la ligne, passer la classification à `technical_enforced` avec preuve |

**Interdit :** supprimer une ligne de faille parce qu'elle a été corrigée. On la met à jour, on ne l'efface pas (`GC-41`).

---

## 9. Renvois

| Sujet | Document |
|---|---|
| Règles de permission | `protocol/permission_policy.md` |
| Règles communes | `protocol/governance_core.md` §7 |
| Référence du schéma OpenCode | `implementations/opencode/frontmatter_reference.md` *(à créer)* |
| Hypothèses d'environnement | `implementations/opencode/environment_requirements.md` *(à créer)* |
| Limites générales | `implementations/opencode/limitations.md` *(à créer)* |

---

## 10. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Constat initial — 22 règles, 0 test exécuté |
| 0.2 | 2026-11-20 | Inspection ORCHESTRATOR (18 règles) et AUDITOR (13 règles) ; asymétrie comparée ; T1–T4 déclarés `NON EXÉCUTÉ` avec justification |
| 0.3 | 2026-11-20 | C29 : protection de `main` maintenue `unknown` ; T5 préparé, non exécuté |
| 0.4 | 2026-11-20 | Harmonisation documentaire de T4 approuvée par le VALIDATOR : tentative de fusion ou de push non autorisé vers une branche protégée autre que `main`, dans un dépôt de test ; simple changement de branche exclu ; T5 maintenu pour `main` ; contrôle AUDITOR/`src/**` conservé comme complément hors T1–T5 ; aucun test exécuté, aucune permission requalifiée |
