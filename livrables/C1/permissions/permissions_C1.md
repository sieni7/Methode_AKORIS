# C1-C — Permissions, rôles et périmètres

**Chantier** : C1 — Consolidation normative et documentaire  
**Tâche** : C1-C — Permissions, rôles, périmètres, interdictions, exceptions, limites  
**Transition** : TR-2026-0002 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C1-consolide-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C1` (alignée sur `main`, intègre les 10 commits C0)  
**Contrainte** : Modifications autorisées uniquement dans le périmètre C1 défini ; pas de fusion vers `main` sans HVG1

---

## 1. Vérification état Git (prérequis C1-C)

| Vérification | Résultat | Preuve |
|---|---|---|
| Branche courante | `dev_C1` | `git branch` |
| Alignement avec `main` | `dev_C1` = `main` (commit `cc6ebc5`) | `git log --oneline` |
| Intégration C0 dans `main` | 10 commits C0 présents sur `main` | `git log --oneline main` |
| C1-A terminé | `livrables/C1/hierarchie_doc/hiérarchie_doc.md` | Commit `7da7ebc` |
| C1-B terminé | `livrables/C1/etat_model/etat_model_C1.md` | Commit `cc6ebc5` |
| Reçu de transition C1 déposé | `livrables/C1/transition/recu_transition_C1.md` | Commit `7da7ebc` |

---

## 2. Objectif de C1-C

Définir et documenter :

1. La **matrice des permissions** (rôles × ressources × niveaux de classification)
2. La classification de chaque permission selon les 5 classifications du protocole (`technical_enforced`, `procedural_only`, `post_checked`, `not_available`, `unknown`)
3. Les écarts et failles constatés (liés aux contradictions C10 et C14 de C0)
4. Les niveaux de violation P0-P3 et leur traitement
5. La mise en relation avec le modèle d'état (C1-B) et l'hierarchie documentaire (C1-A)

---

## 3. Cadre de référence

### 3.1 Trois natures de permission (permission_policy.md §1)

| Nature | Définition | Preuve attendue |
|---|---|---|
| **Procédurale** | Règle de comportement non imposée techniquement | Déclaration, audit, absence de violation constatée |
| **Technique** | Restriction effectivement imposée par l'environnement | Configuration **et** test de refus |
| **Contrôlée a posteriori** | Action techniquement possible, vérifiée après exécution | Trace de contrôle, détection effective |

### 3.2 Cinq classifications (permission_policy §2, terminology §6)

| Classification | Signification | Emploi |
|---|---|---|
| `technical_enforced` | Bloquée par l'environnement, vérifiée | 4 conditions requises (§2.1) |
| `procedural_only` | Règle de conduite, non imposée | Défaut acceptable |
| `post_checked` | Possible, contrôlée après coup | Suppose une détection réelle |
| `not_available` | Capacité absente de l'environnement | À prouver aussi |
| `unknown` | Non vérifiée | **Jamais une garantie** |

### 3.3 Quatre conditions pour `technical_enforced` (permission_policy §2.1)

| # | Condition | Preuve exigible |
|---|---|---|
| 1 | La règle de configuration existe | Fichier, ligne, extrait |
| 2 | Le harnais la prend effectivement en compte | Test contradictoire : l'action est refusée |
| 3 | La restriction est cohérente pour tous les agents concernés | Comparaison des configurations de chaque rôle |
| 4 | Aucun chemin de contournement équivalent n'est ouvert | Test du contournement (ex. écriture via shell) |

---

## 4. Matrice des permissions consolidée

La matrice ci-dessous synthétise la matrice proposée de `permission_policy.md` §3 (statut RECOMMANDATION) et les constatations de `agent_permissions.md` §4.2.

### 4.1 Matrice théorique (règles du protocole)

| Objet | ORCHESTRATOR | BUILDER | AUDITOR | VALIDATOR | Nature de la permission |
|---|---|---|---|---|---|
| Code applicatif `src/` | Interdit (sauf autorisation explicite) | Écrit, dans périmètre du mandat | Lecture seule | Lecture | Procédurale / Technique |
| `state.json` | **Écrit** (seul rédacteur normal) | Interdit | Interdit | Lecture | Procédurale (GC-12) |
| `state.md` | Génère | Interdit | Interdit | Lecture | Procédurale (généré) |
| `current_sprint.md` | Écrit | Lecture | Lecture | Valide | Procédurale |
| `docs/` | Écrit | Lecture | Lecture | Valide | Procédurale |
| `sprint_report/` | Lecture | **Écrit** | Lecture | Lecture | Procédurale |
| `audit_report/` | Lecture | **Interdit** | **Écrit** | Lecture | Procédurale |
| `debt_report/` | Écrit | Interdit | Lecture | Valide | Procédurale |
| `templates/` | Lecture | Interdit | Lecture | Valide | Procédurale |
| `agents.md` | Écrit | Lecture | Lecture | Valide | Procédurale |
| Branche `main` | Interdit de fusion | Interdit | Interdit | **Autorise** | Technique (à vérifier) |
| Secrets | Pas d'accès général | Pas d'accès | Pas d'accès | Pas nécessairement | Procédurale / Technique |
| Transitions | Crée | Consomme + reçu | Consomme + reçu | Autorise | Procédurale |
| Décisions | Recommande | — | Recommande | **Décide** | Procédurale |

### 4.2 Matrice constatée (configuration OpenCode observée)

| Objet | Rôle | Mécanisme constaté | Classification | Preuve |
|---|---|---|---|---|
| `state.json` | BUILDER | `edit` refusé (frontmatter) | `unknown` — contournement possible par shell | `agent_permissions.md` §3.1, règle 1 |
| `state.md` | BUILDER | `edit` refusé | `unknown` | `agent_permissions.md` §3.1, règle 2 |
| `current_sprint.md` | BUILDER | `edit` refusé | `unknown` | `agent_permissions.md` §3.1, règle 3 |
| `audit_report/**` | BUILDER | `edit` refusé | `unknown` | `agent_permissions.md` §3.1, règle 4 |
| `debt_report/**` | BUILDER | `edit` refusé | `unknown` | `agent_permissions.md` §3.1, règle 5 |
| `docs/**` | BUILDER | `edit` refusé | `unknown` | `agent_permissions.md` §3.1, règle 6 |
| `sprints/**`, `templates/**`, `data/**` | BUILDER | `edit` refusé | `unknown` | `agent_permissions.md` §3.1, règles 7-9 |
| `agents.md`, `contexte.md`, `README.md` | BUILDER | `edit` refusé | `unknown` | `agent_permissions.md` §3.1, règles 10-12 |
| `opencode.json`, `.opencode/**` | BUILDER | `edit` refusé | `unknown` | `agent_permissions.md` §3.1, règles 14-15 |
| `git merge` | BUILDER | `shell` refusé | `unknown` | `agent_permissions.md` §3.1, règle 17 |
| `git push --force` | BUILDER | `shell` refusé | `unknown` | `agent_permissions.md` §3.1, règle 18 |
| `git reset --hard` | BUILDER | `shell` refusé | `unknown` | `agent_permissions.md` §3.1, règle 22 |
| `src/**` | BUILDER | Autorisé (non listé) | Conforme au mandat | `agent_permissions.md` §3.1 |
| `state.json` | ORCHESTRATOR | Autorisé (non listé) — rédacteur normal | `unknown` sur l'effectivité | `agent_permissions.md` §3bis |
| `state.json` | AUDITOR | `edit *` refusé, contournable par shell | `unknown` | `agent_permissions.md` §3ter |
| `src/**` | ORCHESTRATOR | `edit src/**` refusé, contournable par shell | `unknown` | `agent_permissions.md` §3bis |
| `src/**` | AUDITOR | `edit *` refusé, contournable par shell | `unknown` | `agent_permissions.md` §3ter |
| `agents.md` | ORCHESTRATOR | **Non protégé** — aucune règle | **Faille, effectivité unknown** | `agent_permissions.md` §3bis |
| `audit_report/**` | AUDITOR | `edit` autorisé après refus global | `unknown` — dépend de l'ordre des règles | `agent_permissions.md` §3ter |
| Secrets | Tous | Aucune règle constatée | `unknown` | `agent_permissions.md` §4.2 |
| `main` | Tous | Aucune protection constatée | `unknown` | `agent_permissions.md` §4.2 (C29) |

### 4.3 Répartition des classifications

| Classification | Nombre de permissions | Pourcentage |
|---|---|---|
| `technical_enforced` | 0 | 0 % |
| `procedural_only` | À déterminer | — |
| `post_checked` | À déterminer | — |
| `not_available` | 0 | 0 % |
| `unknown` | 25+ | 100 % des permissions constatées |

> **Constat critique** : Aucune permission n'est classée `technical_enforced` à ce jour. Toutes restent `unknown` car aucun test contradictoire T1-T5 n'a été exécuté (agent_permissions.md §6).

---

## 5. Écarts et failles constatés

Ces écarts sont issus de `00_cartographie.md` §5 (contradictions C10, C14) et d'`agent_permissions.md` §5 (failles).

### 5.1 Failles techniques

| ID | Faille | Description | Gravité | Source |
|---|---|---|---|---|
| F1 | Contournement par `shell` | Les règles `edit` ne couvrent pas l'écriture par shell (`Set-Content`, `>`, `tee`). La protection de `state.json` est contournable par un moyen trivial. | P1 | `agent_permissions.md` §5.1 |
| F2 | Absence de liste blanche | Sans règle de base `{action: "*", resource: "*", effect: "deny"}`, toute ressource non listée est ouverte par défaut. | P1 | `agent_permissions.md` §5.2 |
| F3 | `agents.md` non protégé pour ORCHESTRATOR | ORCHESTRATOR peut éditer le document qui fait foi sur son propre contrat. Aucune règle `edit` ne couvre `agents.md` pour ORCHESTRATOR. | P2 | `agent_permissions.md` §3bis |
| F4 | Dépendance à l'ordre des règles (AUDITOR) | L'autorisation `audit_report/**` suit le refus global `edit *`. Toute règle ajoutée après sur un chemin chevauchant annulerait l'autorisation. | P2 | `agent_permissions.md` §3ter |
| F5 | Absence de preuve de refus | Aucun rapport du pilote ne contient de trace montrant qu'une édition a été refusée. La configuration est présumée active. | P2 | `agent_permissions.md` §5.4 |

### 5.2 Asymétries inter-rôles

| Interdiction | BUILDER | ORCHESTRATOR | AUDITOR | Commentaire |
|---|---|---|---|---|
| Écrire `state.json` (`edit`) | Refusé | Autorisé (rôle prévu) | Refusé (`*`) | Conforme au rôle |
| Écrire `agents.md` | Refusé | **Non protégé** | Refusé (`*`) | Faille F3 |
| Écrire `src/**` | Non protégé (rôle prévu) | Refusé | Refusé (`*`) | Conforme au rôle |
| `git checkout main*` | Refusé | **Non protégé** | Refusé (`*`) | Faille potentielle |
| `git commit` | **Non protégé** | **Non protégé** | Refusé | Asymétrie |

---

## 6. Niveaux de violation P0-P3 (decision_policy §10, permission_policy §6)

| Niveau | Exemple | Conséquence habituelle |
|---|---|---|
| **P0** | Secret exposé, état falsifié, preuve détruite | Blocage immédiat, `NO_GO` |
| **P1** | Fusion non autorisée, décision modifiée, rejeu de transition | Invalidation possible du résultat |
| **P2** | Fichier hors périmètre modifié | Réserve ou correction |
| **P3** | Erreur documentaire mineure | Correction |

**Règle** : Une violation peut invalider un résultat même si le code fonctionne (`GC-44`). Une violation P0 ou P1 ne peut pas être couverte par une réserve.

---

## 7. Mise en relation avec C1-A et C1-B

### 7.1 Relation avec C1-A (hiérarchie documentaire)

Les permissions s'appliquent aux documents classés dans C1-A selon leur catégorie et niveau de prévalence :

| Catégorie C1-A | Exemple de document | Permission principale |
|---|---|---|
| Normatifs (niveau 2-3) | `governance_core.md`, `permission_policy.md` | ORCHESTRATOR écrit, BUILDER/AUDITOR lisent, VALIDATOR valide |
| Opérationnels (niveau 8) | Prompts, modèles | Selon matrice C1-C |
| Explicatifs (niveau 4-8) | `README.md`, `document_map.md` | Lecture pour tous, écriture selon rôle |
| Historiques/sources (niveau 9-12) | `_sources/*` | Lecture seulement, pas d'autorité normative (réserve R3) |

### 7.2 Relation avec C1-B (modèle d'état)

| Champ `state.json` | Rôle responsable | Permission | Classification |
|---|---|---|---|
| `state.json` | ORCHESTRATOR (seul rédacteur normal) | Écrit | `unknown` (effectivité non prouvée) |
| `state.json` | BUILDER | Interdit | `unknown` (contournable par shell) |
| `state.json` | AUDITOR | Interdit | `unknown` |
| `state.json` | VALIDATOR | Lecture | Procédurale |
| `transition` | ORCHESTRATOR (crée), BUILDER/AUDITOR (consomme) | Selon rôle | Procédurale |
| `last_decision` | VALIDATOR (décide) | Écrit | Procédurale |
| `reserves` | ORCHESTRATOR (suit), VALIDATOR (accepte) | Écrit/Lecture | Procédurale |

> **Réserve R4** (C0) : La distinction entre état de référence C0 (markdown, figé dans `livrables/C0/reference/`) et `state.json`/`state.md` (états opérationnels) est maintenue. Les permissions sur `state.json` ne s'appliquent pas aux livrables C0.

---

## 8. Points d'attention et actions prioritaires

### 8.1 Action M3 (priorité élevée) — Tests T1-T5 et protection de `main`

| Test | Description | Statut actuel | Lien C1-C |
|---|---|---|---|
| T1 | BUILDER édite `state.json` | `NON EXÉCUTÉ` | Vérifie la classification `unknown` de BUILDER sur `state.json` |
| T2 | BUILDER écrit `state.json` par shell | `NON EXÉCUTÉ` | Vérifie la faille F1 (contournement par shell) |
| T3 | ORCHESTRATOR édite `src/**` | `NON EXÉCUTÉ` | Vérifie l'asymétrie ORCHESTRATOR sur `src/**` |
| T4 | Fusion/push non autorisé vers branche protégée (≠ main) | `NON EXÉCUTÉ` | Vérifie la protection des branches |
| T5 | Fusion/push non autorisé vers `main` | `NON EXÉCUTÉ` — préparé | Vérifie la protection de `main` (C29) |

### 8.2 Action B2 (priorité moyenne) — Règles Git/CI-CD applicables pour C1

| Élément | État | Action C1-C |
|---|---|---|
| Règle GC-14 (pas de fusion directe main) | Documentée | À maintenir |
| Protection de `main` | `unknown` | À vérifier (T5) |
| Commits conventionnels | En cours (C0, C1) | À formaliser |
| CI/CD | Non présente dans le dépôt | À évaluer |

---

## 9. Preuves attendues pour C1-C

| Preuve | Référence | Statut |
|---|---|---|
| État Git sur dev_C1 | `git branch`, `git log --oneline` | `directly_verified` |
| Matrice des permissions (théorique) | `permission_policy.md` §3 | `directly_verified` (lecture du document source) |
| Matrice constatée (OpenCode) | `agent_permissions.md` §3, §4.2 | `directly_verified` (lecture du document source) |
| Classification `unknown` (aucune `technical_enforced`) | `agent_permissions.md` §4.1 | `directly_verified` |
| Failles F1-F5 | `agent_permissions.md` §5 | `directly_verified` |
| Asymétries inter-rôles | `agent_permissions.md` §5.3 | `directly_verified` |
| Niveaux P0-P3 | `decision_policy.md` §10, `permission_policy.md` §6 | `directly_verified` |

---

## 10. Suite de C1

Après C1-C, les tâches suivantes sont prévues dans le mandat C1 :

| Tâche | Description | Livrable attendu | Dépend de C1-C |
|---|---|---|---|
| C1-D | Registres décisions | `livrables/C1/registres/` | Non |
| C1-E | Versionning SemVer | `livrables/C1/versioning/` | Non |
| C1-F | Git/GitHub atomique | `livrables/C1/git/` | Oui (permissions Git, protection main) |
| C1.1 | Traitement divergences C0 | `livrables/C1/registres/` | Non |
| C1.3 | MUST/SHOULD/MAY/OUT OF SCOPE | Dans les documents | Non |
| C1.6 | Préparation audit C1 | `livrables/C1/rapport/` | Oui (matrice permissions) |
| C1.7 | Rapport C1 + HVG1 | `livrables/C1/rapport/rapport_C1.md` | Oui (toutes) |

---
*Fin de C1-C. Matrice des permissions et rôles établie. Aucune permission classée `technical_enforced` (toutes `unknown`). Failles F1-F5 documentées. Action M3 (tests T1-T5, protection main) identifiée comme priorité élevée.*