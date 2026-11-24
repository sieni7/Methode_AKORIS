# Politique des permissions

| Champ | Valeur |
|---|---|
| Version | 0.3 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | Nature, matrice, classification, vérification et violations des permissions |
| Autorité | Normatif — règles de permission |
| Vague | 3 |

**Sources citées :** `F3` = `AKORIS_consolide.md` §12, §13, §16 · `F2` = `AKORIS_architecture_documentaire.md` §4.10 · `GC` = `protocol/governance_core.md` · décision VALIDATOR **A8** · décision VALIDATOR d’harmonisation documentaire de T4 (2026-11-20).

---

## 0. Objet et frontière

Cette politique dit **ce qui est permis, à qui, et à quel niveau de garantie**.

Elle ne dit pas **ce que l'environnement applique réellement**. Ce constat appartient à `implementations/opencode/agent_permissions.md`, qui décrit une configuration observée, avec ses preuves et ses failles.

| Question | Document |
|---|---|
| Qui a le droit de faire quoi ? | **ce document** |
| Qu'est-ce qui est effectivement bloqué ? | `implementations/opencode/agent_permissions.md` |
| Comment vérifier ? | ce document §7 |

Confondre les deux produit exactement le défaut que le socle interdit : présenter une règle comme une garantie (`GC-40`).

---

## 1. Trois natures de permission

| Nature | Définition | Preuve attendue |
|---|---|---|
| **Procédurale** | Règle de comportement non imposée techniquement | Déclaration, audit, absence de violation constatée |
| **Technique** | Restriction effectivement imposée par l'environnement : système de fichiers, utilisateur distinct, branche protégée, CI, outil, contrôle d'accès | Configuration **et** test de refus |
| **Contrôlée a posteriori** | Action techniquement possible, vérifiée après exécution | Trace de contrôle, détection effective |

Une permission peut changer de nature au cours d'un projet — dans un sens seulement : une protection ajoutée est un progrès ; une protection retirée doit être déclarée.

---

## 2. Classification

Chaque permission, pour chaque rôle et chaque ressource, est classée :

```text
technical_enforced
procedural_only
post_checked
not_available
unknown
```

| Valeur | Signification | Emploi |
|---|---|---|
| `technical_enforced` | Bloquée par l'environnement, vérifiée | Voir §2.1 |
| `procedural_only` | Règle de conduite, non imposée | Défaut acceptable |
| `post_checked` | Possible, contrôlée après coup | Suppose une détection réelle |
| `not_available` | Capacité absente de l'environnement | À prouver aussi |
| `unknown` | Non vérifiée | **Jamais une garantie** |

### 2.1 Conditions d'emploi de `technical_enforced`

Le terme ne peut être employé que si **les quatre** conditions sont réunies :

| # | Condition | Preuve exigible |
|---|---|---|
| 1 | La règle de configuration existe | Fichier, ligne, extrait |
| 2 | Le harnais la prend effectivement en compte | Test contradictoire : l'action est refusée |
| 3 | La restriction est cohérente pour tous les agents concernés | Comparaison des configurations de chaque rôle |
| 4 | Aucun chemin de contournement équivalent n'est ouvert | Test du contournement (ex. écriture via shell) |

Si une condition manque, la classification est `unknown` ou `post_checked` — jamais `technical_enforced`.

**Une permission déclarée dans un fichier n'est pas une permission appliquée.**

### 2.2 Traçabilité de la classification

Toute classification est datée et adossée à une preuve conservée. Une classification sans preuve est `unknown`, quel que soit le document qui l'affirme.

---

## 3. Matrice des permissions

> **Statut : `RECOMMANDATION`.** Les sources énoncent les principes ; elles ne fournissent pas la matrice complète. Cette matrice est une proposition cohérente avec F3 §3 et §12.

| Objet | ORCHESTRATOR | BUILDER | AUDITOR | VALIDATOR |
|---|---|---|---|---|
| Code applicatif `src/` | **Interdit** pendant un sprint, sauf autorisation explicite | Écrit, **dans le périmètre du mandat** | Lecture seule | Lecture |
| `state.json` | **Écrit** (seul rédacteur normal) | Interdit | Interdit | Lecture |
| `state.md` | Génère | Interdit | Interdit | Lecture |
| `current_sprint.md` | Écrit | Lecture | Lecture | Valide |
| `docs/` | Écrit | Lecture | Lecture | Valide |
| `sprint_report/` | Lecture | **Écrit** | Lecture | Lecture |
| `audit_report/` | Lecture | **Interdit** | **Écrit** | Lecture |
| `debt_report/` | Écrit | Interdit | Lecture | Valide |
| `templates/` | Lecture | Interdit | Lecture | Valide |
| `agents.md` | Écrit | Lecture | Lecture | Valide |
| Branche `main` | Interdit de fusion | Interdit | Interdit | **Autorise** |
| Secrets | Pas d'accès général | Pas d'accès | Pas d'accès | Pas nécessairement |
| Transitions | Crée | Consomme + reçu | Consomme + reçu | Autorise |
| Décisions | Recommande | — | Recommande | **Décide** |

**Lecture étendue :** un rôle peut lire tout ce qui est nécessaire à son mandat. La lecture n'est pas restreinte par défaut ; elle peut l'être par l'environnement.

---

## 4. Moindre privilège

| Rôle | Principe |
|---|---|
| ORCHESTRATOR | Écrit la gouvernance, pas le code applicatif pendant les sprints |
| BUILDER | Écrit le code autorisé, ni l'état central ni les rapports d'audit |
| AUDITOR | Écrit son rapport, ni le code audité ni l'état central |
| VALIDATOR | Décide, sans nécessairement disposer d'un accès général aux secrets |

Trois conséquences opérationnelles :

1. **Aucun rôle n'écrit la preuve de son propre contrôle.** Le rapport d'audit appartient à AUDITOR ; l'état appartient à ORCHESTRATOR.
2. **Aucun rôle ne cumule production et acceptation** (`GC-17`).
3. **Le VALIDATOR ne contourne pas les contrôles** : son autorité porte sur les décisions, pas sur l'exécution technique.

---

## 5. Protections spécifiques

### 5.1 `state.json`

| Exigence | Niveau |
|---|---|
| Écriture réservée à ORCHESTRATOR | Procédural au minimum (`GC-12`) |
| Modification non autorisée empêchée ou détectée | Technique ou a posteriori |
| Intégrité vérifiable | Versionnement Git |
| Divergence avec un reçu | Bloquante (A2) |

### 5.2 Branche `main`

- La protection de `main` doit être **vérifiée, jamais supposée** (`F3` §16).
- Une branche dite « protégée » sans test est une permission `unknown`.
- La fusion exige une décision humaine distincte (`GC-14`).

### 5.3 Secrets

| Exigence | Portée |
|---|---|
| Absence dans les rapports et le dépôt | Tous rôles (`GC-33`) |
| Recherche avant commit et avant fusion | BUILDER, ORCHESTRATOR (`GC-34`) |
| Accès limité au strict nécessaire | Tous rôles |
| Révocation possible | ORCHESTRATOR, VALIDATOR |

Une exposition de secret est une violation **P0**, sans exception de profil.

### 5.4 Transitions

Le droit de créer une transition appartient à ORCHESTRATOR ; le droit de l'autoriser au VALIDATOR ; le droit de la consommer au seul destinataire. Aucun rôle ne peut consommer une transition qui ne lui est pas adressée (`INV-03`).

---

## 6. Violations

### 6.1 Niveaux

| Niveau | Exemple | Conséquence habituelle |
|---|---|---|
| **P0** | Secret exposé, état falsifié, preuve détruite | Blocage immédiat, `NO_GO` |
| **P1** | Fusion non autorisée, décision modifiée, rejeu de transition | Invalidation possible du résultat |
| **P2** | Fichier hors périmètre modifié | Réserve ou correction |
| **P3** | Erreur documentaire mineure | Correction |

### 6.2 Traitement

Toute violation suit sept étapes (`GC-43`) :

1. **Arrêter** l'action.
2. **Conserver** les traces — aucune suppression.
3. **Identifier** l'acteur, l'objet, le moment, le moyen.
4. **Évaluer** la gravité et l'impact.
5. **Auditer** : la violation entre dans le périmètre d'audit.
6. **Rattacher** à une décision.
7. **Corriger** ou **accepter explicitement** — jamais ignorer.

### 6.3 Effet sur le résultat

Une violation peut invalider un résultat **même si le code fonctionne** (`GC-44`). C'est particulièrement vrai en profil Reinforced : un résultat obtenu hors cadre n'est pas un résultat conforme.

---

## 7. Vérification effective

### 7.1 Principe

La classification `technical_enforced` ne s'obtient que par **test contradictoire**. Un test qui réussit ne prouve rien ; c'est un test qui **échoue** qui prouve une restriction.

### 7.2 Protocole

| # | Test | Attendu | Si le résultat diffère |
|---|---|---|---|
| T1 | Édition directe d'un fichier interdit | Refus | `procedural_only` |
| T2 | Écriture du même fichier par shell (redirection, `Set-Content`, `tee`) | Refus | **Faille de contournement** |
| T3 | Édition d'un fichier autorisé à un autre rôle | Refus | Asymétrie de configuration |
| T4 | Tentative de fusion ou de push non autorisé vers une branche protégée autre que `main`, dans un dépôt de test | Refus | Protection de la branche non démontrée → `unknown` |
| T5 | Tentative équivalente de fusion ou de push non autorisé vers `main`, dans un dépôt de test (décision **C29**) | Refus | Protection de `main` maintenue `unknown` |

Un simple changement de branche (`checkout` ou `switch`) ne constitue pas, à lui seul, la vérification du blocage d’une fusion ou d’un push : T4 et T5 portent sur la tentative de fusion ou de push non autorisé.

Le contrôle consistant à demander à AUDITOR d’éditer `src/**` reste une vérification complémentaire des permissions inter-rôles. Il n’est ni T4 ni un nouveau test T1–T5, et ne reçoit aucun identifiant de test supplémentaire.

### 7.3 Qui vérifie, quand

| Élément | Règle |
|---|---|
| Exécutant | AUDITOR, ou ORCHESTRATOR en préparation (CP3) |
| Fréquence | Avant CP3, puis à chaque changement d'environnement |
| Trace | Date, test, commande, résultat, capture ou journal |
| Emplacement | `implementations/opencode/agent_permissions.md` |
| Verdict | Classification mise à jour, avec preuve |

### 7.4 Absence de vérification

Sans test exécuté, la classification reste `unknown`. Un projet peut démarrer avec des `unknown` **déclarés** ; il ne peut pas les présenter comme des garanties.

---

## 8. Limites de l'environnement partagé

Dans un environnement partagé — même machine, même utilisateur système, même dépôt — les permissions sont **principalement procédurales**, sauf preuve technique contraire (`F3` §12).

Conséquences à déclarer :

- un agent peut, techniquement, écrire là où un autre devrait être seul ;
- la séparation des rôles repose d'abord sur la discipline et l'audit ;
- les garanties augmentent avec l'isolation (utilisateur distinct, conteneur, branche protégée, CI) ;
- l'absence d'isolation n'est pas un échec : c'est une **limite à documenter**.

---

## 9. Renvois

| Sujet | Document |
|---|---|
| Règles communes | `protocol/governance_core.md` §3, §7 |
| États et invariants | `protocol/state_model.md` |
| Reçu et consommation | `protocol/transition_policy.md` |
| Audit des permissions | `protocol/audit_policy.md` |
| Configuration observée | `implementations/opencode/agent_permissions.md` |
| Limites de l'environnement | `implementations/opencode/limitations.md` |

---

## 10. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 3) — intégration A8, C10, GC-36 |
| 0.2 | 2026-11-20 | T5 préparé pour la protection de `main` (C29) ; aucune permission requalifiée |
| 0.3 | 2026-11-20 | Harmonisation documentaire de T4 approuvée par le VALIDATOR : tentative de fusion ou de push non autorisé vers une branche protégée autre que `main`, dans un dépôt de test ; simple changement de branche exclu ; T5 maintenu pour `main` ; contrôle AUDITOR/`src/**` conservé comme complément ; aucun test exécuté, aucune permission requalifiée |
