# Modèle d'état

| Champ | Valeur |
|---|---|
| Version | 0.2 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | États du projet, du sprint et des transitions ; invariants ; structure de `state.json` |
| Autorité | Normatif — modèle d'état |
| Vague | 3 |

**Sources citées :** `F3` = `AKORIS_consolide.md` §6, §7 · `F2` = `AKORIS_architecture_documentaire.md` §4.6 · `GC` = `protocol/governance_core.md` · décisions VALIDATOR **A2**, **A7**, **C22**.

---

## 0. Décision fondatrice (A2)

Trois règles du VALIDATOR structurent tout ce document :

1. **`state.json` est la source de vérité de l'état courant.**
2. **Les reçus sont des preuves d'événements.**
3. **Toute divergence entre l'état et un reçu est une incohérence bloquante jusqu'à réconciliation.**

Ces trois règles ne sont pas des recommandations : elles sont la base du modèle. Toute structure ou procédure qui les contredit est invalide.

---

## 1. Les quatre objets d'état

AKORIS sépare quatre objets qu'il ne faut jamais confondre :

| Objet | Question à laquelle il répond | Porté par |
|---|---|---|
| **État du projet** | Où en est le projet dans son cycle de vie ? | `state.json` → `project.status` |
| **État du sprint** | Où en est l'incrément courant ? | `state.json` → `sprint.current_status` |
| **État de la transition** | Où en est l'autorisation en cours ? | `state.json` → `transition.status` |
| **État de la décision humaine** | Quelle décision fait foi ? | `state.json` → `last_decision` + registre des décisions |

Un projet peut être `in_progress` avec un sprint `awaiting_authorization` et aucune transition active : ce ne sont pas des contradictions, ce sont des objets différents.

Dans `state.json`, cette absence est représentée par `transition: null` ; lorsqu'une transition est présente, son objet contient les 16 champs requis par `reference/state.schema.json`.

---

## 2. États du projet

### 2.1 Liste

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

### 2.2 Transitions autorisées

> **Statut : `RECOMMANDATION`.** Les sources énumèrent les états sans fournir la table de transitions. Cette table est une proposition de rédaction, cohérente avec le cycle nominal de F3 §15 et les checkpoints de F3 §14. Elle doit être validée.

| Depuis | Vers | Condition | Acteur |
|---|---|---|---|
| `initializing` | `framing` | Environnement vérifié | ORCHESTRATOR |
| `framing` | `designing` | **CP1 validé** | VALIDATOR |
| `designing` | `planning` | Conception établie | ORCHESTRATOR |
| `planning` | `preparing` | **CP2 validé** | VALIDATOR |
| `preparing` | `ready` | **CP3 validé** + audit de préparation | VALIDATOR |
| `ready` | `in_progress` | Première transition autorisée | VALIDATOR |
| `in_progress` | `under_review` | Sprint livré, audit engagé | ORCHESTRATOR |
| `under_review` | `in_progress` | Sprint rejeté ou correction demandée | VALIDATOR |
| `under_review` | `ready` | Sprint accepté, sprint suivant à préparer | VALIDATOR |
| tout état actif | `blocked` | Blocage qualifié | ORCHESTRATOR |
| `blocked` | état précédent | Blocage levé | VALIDATOR |
| tout état actif | `suspended` | Suspension décidée | VALIDATOR |
| `suspended` | état précédent | Reprise autorisée | VALIDATOR |
| `ready` / `under_review` | `completed` | Décision finale | VALIDATOR |
| tout état non terminal | `cancelled` | Annulation | VALIDATOR |

`completed` et `cancelled` sont **terminaux**.

### 2.3 Checkpoints — `checkpointStatus`

> **Décision A01 appliquée.** Les valeurs normatives de `checkpointStatus` sont celles déjà portées par `reference/state.schema.json` : `pending`, `in_review`, `validated`, `rejected`. Elles sont définies ici comme vocabulaire d'état des points de contrôle `cp1`, `cp2` et `cp3` de `state.json` (§6.2).

| Valeur | Sens documentaire | Limite explicite |
|---|---|---|
| `pending` | Le point de contrôle est en attente. | Aucune échéance ni durée n'est déduite de cette valeur. |
| `in_review` | Le point de contrôle est en cours d'examen. | Aucun acteur ni délai n'est déduit de cette valeur. |
| `validated` | Le point de contrôle est marqué validé. | Ne certifie aucun état réel de projet ni aucune permission. |
| `rejected` | Le point de contrôle est marqué rejeté. | N'énonce aucune procédure de reprise. |

> **Limite.** Le type de revue (`readiness_review`, `sprint_audit`) est distinct du statut du point de contrôle. Aucune matrice de correspondance ni conséquence de processus n'est définie ici. Cette définition n'établit ni séquence obligatoire, ni autorisation, ni règle de transition, ni décision de permission.

---

## 3. États du sprint

### 3.1 Liste

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

### 3.2 Transitions autorisées

> **Statut : `RECOMMANDATION`.** Même réserve que §2.2.

| Depuis | Vers | Condition | Acteur |
|---|---|---|---|
| `planned` | `preparing` | Sprint sélectionné dans la roadmap | ORCHESTRATOR |
| `preparing` | `awaiting_authorization` | Mandat versionné prêt | ORCHESTRATOR |
| `awaiting_authorization` | `authorized` | Autorisation explicite | VALIDATOR |
| `authorized` | `in_progress` | Reçu déposé | BUILDER |
| `in_progress` | `builder_completed` | Rapport de sprint livré | BUILDER |
| `builder_completed` | `auditing` | Transition d'audit autorisée | VALIDATOR |
| `auditing` | `audit_completed` | Rapport d'audit livré | AUDITOR |
| `audit_completed` | `accepted` | Décision `GO` | VALIDATOR |
| `audit_completed` | `accepted_with_reserves` | Décision `GO_WITH_RESERVES` | VALIDATOR |
| `audit_completed` | `rejected` | Décision `NO_GO` | VALIDATOR |
| `rejected` | `correcting` | Mandat correctif autorisé | VALIDATOR |
| `correcting` | `builder_completed` | Correction livrée | BUILDER |
| `accepted` / `accepted_with_reserves` | `merged` | Fusion autorisée **séparément** | VALIDATOR |
| `merged` | `closed` | Sprint clôturé | ORCHESTRATOR |
| tout état non terminal | `cancelled` | Annulation | VALIDATOR |

**Règle :** `accepted` n'implique jamais `merged` (`GC-07`). Ce sont deux décisions distinctes.

---

## 4. États d'une transition

### 4.1 Liste

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

### 4.2 Transitions autorisées

| Depuis | Vers | Condition | Acteur |
|---|---|---|---|
| `draft` | `awaiting_human_go` | Transition soumise | ORCHESTRATOR |
| `awaiting_human_go` | `authorized` | Autorisation explicite | VALIDATOR |
| `awaiting_human_go` | `rejected` | Refus explicite | VALIDATOR |
| `awaiting_human_go` | `expired` | Échéance atteinte | système |
| `authorized` | `consumed` | **Reçu déposé** | agent destinataire |
| `authorized` | `expired` | Échéance atteinte sans consommation | système |
| `consumed` | `in_progress` | Intervention commencée | agent destinataire |
| `in_progress` | `completed` | Résultat produit | agent destinataire |
| tout état non terminal | `cancelled` | Annulation | VALIDATOR |

**États terminaux :** `completed`, `rejected`, `expired`, `cancelled`. Aucun n'est réactivable (`GC-46`).

> **Note (C7).** Le pilote ne connaît que cinq états (`awaiting_human_go`, `authorized`, `in_progress`, `completed`, `cancelled`). Les quatre autres — `draft`, `consumed`, `rejected`, `expired` — sont introduits par F3 et sont nécessaires au mécanisme de reçu : `consumed` matérialise précisément l'événement dont le reçu est la preuve.

---

## 5. Invariants

Un état qui viole un invariant est un **état invalide**. Il ne se corrige pas par interprétation : il se réconcilie.

| ID | Invariant |
|---|---|
| INV-01 | Un `state.json` ne décrit qu'un seul projet. |
| INV-02 | Une seule transition est active à la fois. |
| INV-03 | `current_agent` est le destinataire de la transition active, ou ORCHESTRATOR en l'absence de transition. |
| INV-04 | Une transition possède **au plus un** reçu. La présence de deux reçus pour un même `transition_id` constitue une violation. |
| INV-05 | Une transition terminale n'est jamais réactivée. |
| INV-06 | Aucun sprint n'est `in_progress` sans transition `consumed`. |
| INV-07 | Aucun sprint n'est `accepted` sans `audit_completed`. |
| INV-08 | `state.md` n'est jamais édité manuellement : il est généré. |
| INV-09 | Toute divergence état/reçu est bloquante (A2). |
| INV-10 | Un changement de version de mandat invalide l'autorisation en cours. |
| INV-11 | Le profil est verrouillé après enregistrement ; sa modification suit la procédure de changement. |
| INV-12 | Aucun identifiant consommé n'est réutilisé. |

---

## 6. Structure de `state.json`

### 6.1 Statut de cette structure

> **Décision A2 appliquée.** A2 tranche la primauté de l'état, la nature des reçus, le traitement des divergences et la **forme de sérialisation**. La structure imbriquée `schema_version: "2.0"` décrite dans F3 §7, avec la correction C22 (`transition_id` remplace `token`), est retenue.

> **Statut : Norme AKORIS v2.0.** Le statut provisoire de la structure v2.0 est remplacé par cette qualification normative.
>
> Le pilote utilise encore une structure v1.0.
> La structure v2.0 est la structure normative AKORIS.
> La migration du pilote n'est pas automatiquement réalisée par la documentation.

> **Écart du pilote — documenté séparément.** La structure `v1.0` plate du pilote est une version héritée, non conforme au modèle normatif actuel. Elle est constatée comme fait d'implémentation (niveau 5), sans être promue en règle : elle n'ouvre aucune alternative normative. Le pilote doit être déclaré non conforme à la Norme AKORIS v2.0.

> Le schéma technique correspondant est `reference/state.schema.json`, présenté comme **Schéma AKORIS v2.0** (décision C28). Toute évolution de la structure est versionnée selon A7 et tracée dans `changelog.md`.

### 6.2 Exemple de structure

> **Exemple.** Les valeurs sont des marqueurs, pas des valeurs à réutiliser.
>
> **Représentation.** `transition: null` représente l'absence de transition active. Lorsque la transition est présente, son objet contient les 16 champs requis par `reference/state.schema.json` ; les champs dont l'événement n'a pas encore eu lieu sont représentés par `null`.

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
  "transition": {
    "transition_id": "TR-2026-0001",
    "status": "awaiting_human_go",
    "from_agent": "ORCHESTRATOR",
    "to_agent": "BUILDER",
    "mandate_version": "sprint_01-v1",
    "action": "execute_sprint",
    "sprint_id": null,
    "created_at": null,
    "expires_at": null,
    "authorized_at": null,
    "authorized_by": null,
    "decision_id": null,
    "consumed_at": null,
    "receipt_reference": null,
    "completed_at": null,
    "result_report": null
  },
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

### 6.3 Exigences sur le fichier

Le fichier doit être (`F3` §7) :

- **valide** — structure conforme au schéma ;
- **versionné** — toute modification est historisée ;
- **vérifiable par schéma** — le schéma de validation normatif est `reference/state.schema.json` (décision C28), établi pour la structure v2.0 ;
- **cohérent avec les rapports** — aucune contradiction avec un rapport ou un reçu ;
- **protégé** — modifications non autorisées empêchées ou détectées.

### 6.4 Champs normatifs

| Champ | Rôle | Remarque |
|---|---|---|
| `schema_version` | Version du schéma de sérialisation | Distinct de `protocol.version` (A7) |
| `protocol.version` | Version du protocole appliqué | A7 |
| `governance.profile` | Profil actif | `standard` par défaut |
| `governance.profile_locked` | Verrouillage du profil | `INV-11` |
| `project.status` | État du projet | §2 |
| `sprint.current_status` | État du sprint | §3 |
| `transition.transition_id` | Identifiant de la transition | **Remplace `token` (C22)** |
| `transition.status` | État de la transition | §4 |
| `transition.receipt_reference` | Référence du reçu | Preuve de consommation |
| `last_decision` | Dernière décision humaine | `GC-29` |
| `permission_violations` | Violations constatées | `GC-43` |

> **Dépréciation (C22).** Le champ `authorization.token` du pilote est **déprécié**. Le nom normatif est `transition_id`. La raison n'est pas cosmétique : le mot « token » suggère une garantie cryptographique que F3 §2.3 exclut explicitement.

---

## 7. Divergence état / reçu (A2)

### 7.1 Détection

Une divergence existe lorsque, pour un même `transition_id` :

- l'état indique `authorized` et un reçu de consommation existe ;
- l'état indique `consumed` et aucun reçu n'existe ;
- l'état et le reçu diffèrent sur l'agent, le sprint, l'action ou l'horodatage ;
- deux reçus existent pour un même identifiant.

### 7.2 Traitement

| Étape | Action | Acteur |
|---|---|---|
| 1 | **Gel** : aucune nouvelle action opérationnelle | ORCHESTRATOR |
| 2 | Projet passé en `blocked` | ORCHESTRATOR |
| 3 | Constat écrit : identifiant, écart, sources comparées | ORCHESTRATOR |
| 4 | Réconciliation : l'état est corrigé **ou** le reçu est invalidé, jamais les deux | ORCHESTRATOR |
| 5 | Décision de reprise | VALIDATOR |
| 6 | Trace conservée dans `docs/governance/incidents/` | ORCHESTRATOR |

**Règle :** on ne « choisit » pas la source la plus favorable. La réconciliation est un acte explicite, motivé et validé, jamais une correction silencieuse (`GC-31`).

---

## 8. Versions distinctes (A7)

Cinq versions coexistent et ne se confondent jamais :

| Version | Objet | Portée par |
|---|---|---|
| Version du **protocole** | Règles du cadre | `protocol.version` |
| Version du **profil** | Niveau d'exigence | Document de profil |
| Version du **schéma** | Structure de `state.json` | `schema_version` |
| Version du **mandat** | Périmètre autorisé | `current_sprint.md`, `mandate_version` |
| Version du **document** | Révision d'un fichier | En-tête de chaque document |

Une évolution du protocole n'est pas une évolution du projet (`F2` §16). Une évolution du schéma n'est pas une évolution du protocole.

---

## 9. Erreurs et reprises

Ce document définit les états ; il ne définit pas les procédures de reprise. Les cas de blocage, suspension, interruption d'agent, perte de rapport, rollback et incident de sécurité sont traités dans `protocol/recovery_policy.md`.

---

## 10. Limites

- La table de transitions (§2.2, §3.2) est une **proposition**, pas une décision validée.
- Le schéma technique `reference/state.schema.json` existe et est enregistré comme **Schéma AKORIS v2.0** (décision C28) ; à la suite de l'arbitrage A01, ses énumérations de projet et de sprint sont alignées sur ce modèle. L'exigence « vérifiable par schéma » demeure une exigence documentaire : aucun état réel de projet n'a été validé ici, et la validation JSON Schema n'a pas été reproduite avec un validateur nommé (`NON VÉRIFIÉE`).
- La protection technique de `state.json` est **partielle** : voir `implementations/opencode/agent_permissions.md`.
- Le comportement en cas d'écriture concurrente n'est pas défini (`INCONNU`).

---

## 11. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 3) — intégration A2, A7, C22 |
| 0.2 | 2026-11-20 | A2 tranchée : v2.0 normative, pilote v1.0 écart historique ; C28 : schéma technique créé |
