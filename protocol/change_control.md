# Contrôle des changements

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | Définition, classification, cycle de vie, impact et effets d'un changement |
| Autorité | Normatif — source unique des changements |
| Vague | 4 |

**Sources citées :** `F3` = `AKORIS_consolide.md` §10 · `F2` = `AKORIS_architecture_documentaire.md` §4.8 · `GC` = `protocol/governance_core.md` · `DP` = `protocol/decision_policy.md` · décisions VALIDATOR **A1**, **A3**, **A7**.

---

## 0. Objet

Un changement est un **écart volontaire et tracé** par rapport à ce qui était autorisé. Il n'est pas un défaut : c'est un fait de projet. Ce qui est interdit, ce n'est pas de changer — c'est de changer sans le dire.

Cette politique définit :

- ce qui constitue un changement ;
- comment il est classé ;
- comment il est instruit ;
- ce qu'il produit sur le mandat, l'autorisation et les documents.

---

## 1. Définition

Un changement est toute modification affectant l'un des dix éléments suivants :

| # | Élément |
|---|---|
| 1 | Le périmètre |
| 2 | Une exigence |
| 3 | Une règle métier |
| 4 | Une architecture |
| 5 | Une donnée (structure, nature, traitement) |
| 6 | La sécurité |
| 7 | Un mandat |
| 8 | Un sprint |
| 9 | Une décision validée |
| 10 | Le niveau de gouvernance (profil) |

**Ne sont pas des changements** au sens de cette politique :

- une correction dans le périmètre autorisé ;
- une précision rédactionnelle sans effet sur le sens ;
- une décision déjà prévue par le mandat.

Une correction qui déborde le périmètre **est** un changement.

---

## 2. Classification

> **Statut : `RECOMMANDATION`.** Les sources nomment quatre catégories sans fournir de seuils. Les critères ci-dessous sont une proposition de rédaction, cohérente avec F3 §10.1 et §10.4.

| Classe | Critère | Impact | Réversibilité | Validation |
|---|---|---|---|---|
| **Éditorial** | Aucun effet sur le sens, le périmètre ou les décisions | Nul | R0 | Trace simple |
| **Mineur** | Effet local, sans changement de périmètre ni de décision validée | Faible | R0-R1 | ORCHESTRATOR, trace |
| **Majeur** | Modifie périmètre, exigence, architecture, donnée, mandat ou critère | Significatif | R1-R2 | Analyse d'impact + décision VALIDATOR |
| **Critique / urgent** | Sécurité, intégrité des données, opération irréversible, incident en cours | Élevé | R2-R3 | Confinement immédiat + régularisation |

**Règle d'arbitrage :** en cas de doute entre deux classes, la classe supérieure s'applique. Un changement mal classé est un changement non maîtrisé.

---

## 3. Identifiants

| Type | Format | Usage |
|---|---|---|
| Changement planifié | `CHG-AAAA-NNNN` | Procédure normale |
| Urgence | `URG-AAAA-NNNN` | Confinement immédiat |

Un identifiant est unique et n'est jamais réutilisé. Un changement abandonné conserve le sien.

---

## 4. Cycle de vie

```text
proposed
under_analysis
awaiting_decision
approved
rejected
deferred
implemented
verified
closed
cancelled
```

| Depuis | Vers | Condition | Acteur |
|---|---|---|---|
| `proposed` | `under_analysis` | Fiche créée | ORCHESTRATOR |
| `under_analysis` | `awaiting_decision` | Analyse d'impact complète | ORCHESTRATOR |
| `awaiting_decision` | `approved` | Décision `GO` | VALIDATOR |
| `awaiting_decision` | `rejected` | Décision `NO_GO` | VALIDATOR |
| `awaiting_decision` | `deferred` | Report explicite | VALIDATOR |
| `approved` | `implemented` | Mise en œuvre livrée et auditée | BUILDER, AUDITOR |
| `implemented` | `verified` | Vérification de l'effet réel | AUDITOR |
| `verified` | `closed` | Clôture tracée | ORCHESTRATOR |
| tout état non terminal | `cancelled` | Abandon | VALIDATOR |

**Règle :** `approved` n'autorise pas l'exécution. L'exécution exige un **mandat** et une **transition** (`GC-45`). Un changement approuvé sans mandat reste une intention.

> **Cohérence avec `decision_policy.md` :** les valeurs `GO`, `NO_GO`, `HOLD`, `CANCELLED` s'appliquent aussi aux changements. `HOLD` n'apparaît pas dans ce cycle car il ne modifie pas l'état du changement : il suspend la décision, qui reste `awaiting_decision`.

---

## 5. Analyse d'impact

Tout changement **majeur** ou **critique** exige une analyse portant sur huit dimensions :

| # | Dimension | Question |
|---|---|---|
| 1 | Métier | Quelles règles métier sont affectées ? |
| 2 | Fonctionnel | Quelles exigences et quels parcours changent ? |
| 3 | Technique | Quels composants, interfaces, dépendances ? |
| 4 | Sécurité | Quelles surfaces, quels contrôles, quels secrets ? |
| 5 | Données | Quelles structures, quelles migrations, quelles pertes ? |
| 6 | Planning | Quel effet sur les sprints et la roadmap ? |
| 7 | Tests | Quels tests à créer, modifier, invalider ? |
| 8 | Réversibilité | Peut-on revenir en arrière, et à quel coût ? |

Une dimension non renseignée est déclarée `N/A` avec justification, jamais laissée vide.

### 5.1 Réversibilité

| Classe | Signification | Conséquence |
|---|---|---|
| **R0** | Facilement réversible | Aucune précaution particulière |
| **R1** | Correction simple | Plan de retour minimal |
| **R2** | Migration ou intervention importante | Plan de retour obligatoire, testé si possible |
| **R3** | Difficilement réversible ou irréversible | Autorisation renforcée, sauvegarde préalable |

Un changement **R3** ne s'instruit pas comme un changement R1 : le coût d'une erreur n'est pas le même.

---

## 6. Effet sur le mandat

Si un changement modifie le périmètre, le sprint, l'action, l'architecture, les critères, le profil de risque ou la version du mandat, la procédure est **automatique** :

1. L'ancienne autorisation est **suspendue ou invalidée**.
2. Le mandat reçoit une **nouvelle version**.
3. Les documents affectés sont mis à jour.
4. Une **nouvelle transition** est créée, avec un nouvel identifiant.
5. Un **nouveau `GO`** est nécessaire.

**Aucune exception.** Poursuivre avec une autorisation périmée est une violation **P1**.

---

## 7. Changement urgent

Une urgence autorise un **confinement immédiat** :

| Action de confinement | Effet |
|---|---|
| Désactivation d'une fonctionnalité | Réduit la surface d'exposition |
| Révocation d'un secret | Coupe l'accès compromis |
| Blocage d'un accès | Empêche l'exploitation |
| Arrêt d'un déploiement | Évite la propagation |
| Isolation d'une intégration | Contient la dépendance |

L'urgence **ne supprime jamais** :

- la traçabilité ;
- l'audit a posteriori ;
- la régularisation sous forme de `URG-AAAA-NNNN` ;
- la décision du VALIDATOR sur le maintien ou le retour.

Un confinement non régularisé devient une dette invisible.

---

## 8. Changement de profil

Le profil est verrouillé après enregistrement (`GC-09`). Son changement est un **changement majeur** :

| Étape | Contenu |
|---|---|
| 1 | Motif documenté : risque nouveau, risque sous-estimé, contrainte externe |
| 2 | Analyse d'impact sur les documents, preuves et audits |
| 3 | Décision VALIDATOR |
| 4 | Nouvelle version du profil appliqué |
| 5 | Réévaluation des contrôles déjà réalisés |

**Interdit :** déclasser un profil pour tenir un délai. Un déclassement sans motif de risque est une violation de gouvernance.

---

## 9. Documents à mettre à jour

Un changement approuvé impose la mise à jour de tout document dont le contenu devient faux :

| Document | Quand |
|---|---|
| `contexte.md` | Périmètre, objectifs, contraintes |
| `docs/requirements/` | Exigences affectées |
| `docs/architecture/` | Structure ou composants |
| `docs/adr/` | Décision technique nouvelle ou remplacée |
| `docs/acceptance_criteria/` | Critères invalidés ou ajoutés |
| `docs/risks/` | Risque nouveau ou modifié |
| `sprints/roadmap.md` | Planning |
| `current_sprint.md` | Mandat |
| `state.json` | Changement actif, décisions |
| `debt_report/` | Réserve créée ou levée |

**Règle :** un document devenu faux et non corrigé est une anomalie **S1** — il induit en erreur les agents qui s'y réfèrent.

---

## 10. Traçabilité

Chaque changement conserve au minimum :

| Champ | Contenu |
|---|---|
| Identifiant | `CHG-AAAA-NNNN` ou `URG-AAAA-NNNN` |
| Origine | Qui l'a demandé, et pourquoi |
| Description | Ce qui change |
| Classe | Éditorial, mineur, majeur, critique |
| Analyse d'impact | Huit dimensions |
| Réversibilité | R0 à R3 |
| Options | Alternatives examinées |
| Décision | Valeur et auteur |
| Documents affectés | Liste |
| Nouveau mandat | Version |
| Vérification | Preuve de l'effet réel |

Emplacement : `docs/governance/changes/`. Le modèle est `templates/change_request_template.md` (vague 6).

---

## 11. Ce que cette politique n'autorise pas

- Modifier une décision validée sans changement.
- Étendre le périmètre « pendant qu'on y est ».
- Poursuivre avec un mandat dont la version a changé.
- Traiter une urgence sans régularisation.
- Classer un changement majeur en mineur pour éviter une validation.
- Corriger silencieusement un document devenu faux.

---

## 12. Limites

| Limite | Statut |
|---|---|
| Aucun seuil quantitatif de classement | `INCONNU` — appréciation humaine |
| Aucune durée maximale d'instruction | `INCONNU` |
| Aucun mécanisme technique empêchant un changement non déclaré | `unknown` (voir `permission_policy.md`) |
| `docs/governance/changes/` non créé dans le pilote | Le registre n'existe pas encore |

---

## 13. Renvois

| Sujet | Document |
|---|---|
| Valeurs de décision | `protocol/decision_policy.md` |
| Transitions et invalidation | `protocol/transition_policy.md` |
| États du sprint | `protocol/state_model.md` |
| Incidents et reprises | `protocol/recovery_policy.md` |
| Fiche de changement | `templates/change_request_template.md` |

---

## 14. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 4) |
