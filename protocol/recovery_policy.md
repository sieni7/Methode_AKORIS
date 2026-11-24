# Politique de reprise et d'incident

| Champ | Valeur |
|---|---|
| Version | 0.2 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | Blocage, suspension, interruption, état invalide, perte de preuve, reprise, rollback, incident |
| Autorité | Normatif — source unique des reprises |
| Vague | 4 |

**Sources citées :** `F3` = `AKORIS_consolide.md` §10.6, §13 · `F2` = `AKORIS_architecture_documentaire.md` §4.11 · `GC` = `protocol/governance_core.md` · `SM` = `protocol/state_model.md` · `TP` = `protocol/transition_policy.md` · `DP` = `protocol/decision_policy.md`.

---

## 0. Objet et principe

Cette politique traite ce qui se passe **quand le déroulement nominal s'interrompt** : blocage, suspension, agent qui s'arrête, état incohérent, preuve perdue, incident de sécurité.

Trois principes la gouvernent :

1. **Ne jamais improviser.** Une reprise suit une procédure, même courte.
2. **Ne jamais corriger silencieusement.** Toute correction est un acte tracé (`GC-31`).
3. **Ne jamais détruire de trace.** Une trace gênante est conservée, pas effacée (`GC-41`).

---

## 1. Vocabulaire

| Terme | Définition | Distinct de |
|---|---|---|
| **Blocage** | Situation qui empêche d'avancer, sans décision humaine en cours | Suspension (qui est une décision) |
| **Suspension** | Arrêt décidé par le VALIDATOR | Blocage (qui est subi) |
| **Interruption** | Arrêt involontaire d'un agent pendant son action | Achèvement (qui est normal) |
| **Incident** | Événement de sécurité, de permission, d'état ou d'exécution nécessitant un traitement tracé | Anomalie (qui est un défaut constaté) |
| **Reprise** | Reprise d'une activité interrompue, sous conditions vérifiées | Redémarrage (qui ignore l'état) |
| **Rollback** | Retour à un état antérieur connu | Correction (qui avance) |

---

## 2. Typologie des situations

| Situation | Détection | État résultant | Décideur | Urgence |
|---|---|---|---|---|
| Blocage technique ou métier | Agent ou ORCHESTRATOR | Projet `blocked` | VALIDATOR (levée) | Normale |
| Suspension volontaire | VALIDATOR | Projet `suspended` | VALIDATOR | Normale |
| Interruption d'agent | Absence de progression, session perdue | Sprint inchangé, transition en cours | ORCHESTRATOR | Normale |
| État invalide | Violation d'invariant | Projet `blocked` | VALIDATOR | Haute |
| Divergence état/reçu | Comparaison état ↔ reçu | Projet `blocked` | VALIDATOR | Haute |
| Perte de rapport ou de preuve | Contrôle de complétude | Selon gravité | VALIDATOR | Haute |
| Incident de sécurité | Détection, alerte, audit | Projet `blocked` | VALIDATOR | **Immédiate** |
| Opération irréversible engagée | Avant exécution | — | VALIDATOR | **Immédiate** |

---

## 3. Blocage

### 3.1 Déclenchement

Un blocage est déclaré dès qu'une condition nécessaire à la poursuite manque : dépendance indisponible, décision métier absente, preuve manquante, environnement défaillant.

### 3.2 Procédure

| # | Action | Acteur |
|---|---|---|
| 1 | Arrêter toute action non engagée | agent concerné |
| 2 | Consigner : nature, cause connue, impact, action tentée | agent concerné |
| 3 | Passer le projet en `blocked` | ORCHESTRATOR |
| 4 | Qualifier : technique, métier, gouvernance | ORCHESTRATOR |
| 5 | Décider : `HOLD`, correction, changement, ou abandon | VALIDATOR |
| 6 | Lever le blocage et tracer la levée | ORCHESTRATOR |

**Un blocage sans trace n'existe pas** : il réapparaîtra, et personne ne saura pourquoi.

### 3.3 Ce qui n'est pas un blocage

- un refus d'audit : c'est un `NO_GO` ;
- une réserve : c'est une condition acceptée ;
- une question ouverte : c'est un `HOLD`, pas un blocage ;
- un désaccord entre agents : c'est un constat à arbitrer.

---

## 4. Suspension

La suspension est une **décision**, pas un incident. Elle peut viser un sprint, un projet ou l'ensemble d'une activité.

| Élément | Règle |
|---|---|
| Décideur | VALIDATOR uniquement |
| Effet | Aucune nouvelle action opérationnelle |
| Autorisations en cours | Suspendues ; elles ne sont ni consommables ni prolongées |
| Reprise | Décision explicite, avec vérification préalable de l'état |
| Traçabilité | Motif, date, portée, condition de reprise |

Une autorisation suspendue puis reprise **conserve son identifiant** si aucun élément du mandat n'a changé. Si le mandat a changé, la procédure de changement s'applique : nouvelle version, nouvelle transition, nouveau `GO`.

---

## 5. Interruption d'agent

### 5.1 Le problème

Un agent a consommé une autorisation, déposé son reçu, puis s'est arrêté : session fermée, contexte perdu, erreur d'exécution. L'état indique `consumed` ou `in_progress`, mais aucun résultat n'existe.

Ce cas n'est pas théorique : c'est le scénario le plus fréquent en pratique.

### 5.2 Reprise dans le même rôle

> **Statut : `RECOMMANDATION`.** Les sources ne décrivent pas ce cas. La règle ci-dessous est une proposition cohérente avec `GC-46` et `TP` §4.

| Condition | Décision |
|---|---|
| Mandat inchangé, aucun autre agent n'a agi, reçu unique | **Continuation** : le même rôle reprend, sous le même `transition_id` |
| Mandat modifié | **Invalidation** : nouvelle version, nouvelle transition, nouveau `GO` |
| Un autre agent a agi sur le même périmètre | **Blocage** : réconciliation préalable |
| Reçu absent ou ambigu | **Blocage** : divergence état/reçu (`SM` §7) |

Une continuation **n'est pas une réactivation** : on progresse de `consumed` vers `in_progress`, on ne rejoue pas la consommation.

### 5.3 Traçabilité de l'interruption

| Élément | Contenu |
|---|---|
| Événement | Interruption constatée, datée |
| Transition concernée | `transition_id`, statut au moment de l'arrêt |
| Travail effectué | Commits, fichiers, tests exécutés |
| Travail non effectué | Ce qui reste |
| Décision | Continuation ou invalidation |

Un travail interrompu sans inventaire est un travail à refaire — ou pire, à croire fait.

---

## 6. État invalide

Un état est invalide lorsqu'il viole un invariant de `state_model.md` §5.

| Étape | Action |
|---|---|
| 1 | Geler : aucune action opérationnelle |
| 2 | Passer le projet en `blocked` |
| 3 | Identifier l'invariant violé (`INV-01` à `INV-12`) |
| 4 | Constater l'écart, sans interpréter |
| 5 | Réconcilier : corriger l'état **ou** la preuve, jamais les deux |
| 6 | Faire valider la réconciliation |
| 7 | Consigner dans `docs/governance/incidents/` |

**Règle :** on ne « répare » pas un état en le réécrivant pour qu'il redevienne cohérent. On démontre pourquoi il était faux.

---

## 7. Divergence état / reçu

Le traitement détaillé est dans `state_model.md` §7. Rappel du caractère **bloquant** (A2) : aucune poursuite tant que la divergence n'est pas réconciliée.

Cas particulier : lorsque le reçu existe et que le rapport de sprint est absent, la consommation est prouvée mais l'exécution ne l'est pas. La classification est alors `partial`, et le critère concerné ne peut pas recevoir un `PASS` (`DP` §5.1).

---

## 8. Perte de rapport ou de preuve

| Situation | Effet | Traitement |
|---|---|---|
| Rapport perdu, reçu présent | Consommation prouvée, exécution non prouvée | Reconstruction ou `HOLD` |
| Preuve perdue, rapport présent | Affirmation non vérifiable | `declared_only` au mieux |
| Commit perdu ou réécrit | Traçabilité rompue | Blocage, reconstitution |
| Journal CI perdu | Contrôle non reproductible | Re-exécution ou `NOT_CHECKED` |

Une preuve perdue ne se remplace pas par une déclaration. Au mieux, elle se reconstitue ; sinon, elle est déclarée manquante, et la décision en tient compte.

---

## 9. Reprise

### 9.1 Checklist préalable

Avant toute reprise, les six vérifications suivantes sont obligatoires :

| # | Vérification | Échec ⇒ |
|---|---|---|
| 1 | L'état est cohérent avec les reçus | Blocage |
| 2 | Aucun invariant n'est violé | Blocage |
| 3 | Le mandat est à jour et versionné | Nouveau mandat |
| 4 | L'autorisation est valide, non expirée, non consommée ailleurs | Nouvelle transition |
| 5 | L'environnement est opérationnel | Report |
| 6 | Le périmètre est connu et borné | Clarification |

### 9.2 Trace de reprise

| Élément | Contenu |
|---|---|
| Date | Horodatage |
| Cause | Blocage, suspension, interruption, incident |
| État avant | Statut, transition, sprint |
| Actions | Ce qui a été fait pour rétablir |
| État après | Statut, transition, sprint |
| Décision | Qui a autorisé la reprise |

---

## 10. Rollback

### 10.1 Objets

| Objet | Moyen | Autorité |
|---|---|---|
| Code applicatif | Revert de commits, retour de branche | BUILDER dans sa branche ; VALIDATOR pour `main` |
| Données | Restauration depuis sauvegarde | VALIDATOR |
| Configuration | Retour à une version antérieure | ORCHESTRATOR, trace obligatoire |
| État opérationnel | **Interdit** en tant que rollback | Voir §6 : on réconcilie |

**`state.json` ne se « restaure » pas** pour effacer un incident : ce serait détruire une preuve (P0).

### 10.2 Conditions

> **Décision C34.** L'exigence de rollback est déterminée par le **risque réel**, pas par le seul profil. Le profil fixe un **plancher** ; il ne dispense jamais d'évaluer le risque concret du changement.

| Risque réel | Critère d'appréciation | Exigence minimale |
|---|---|---|
| **Faible** | R0, aucune donnée, aucun secret, retour par simple revert | Revert possible, pas de plan formel |
| **Modéré** | R1-R2, donnée reconstructible, intégration interne | Plan de retour écrit avant exécution |
| **Élevé** | R2 avec donnée non reconstructible, secret exposé, intégration externe | Sauvegarde préalable **et** procédure de restauration documentée |
| **Critique** | R3, opération irréversible, donnée réglementée ou sensible | Sauvegarde vérifiée, restauration **testée**, décision VALIDATOR explicite |

**Règles d'application :**

1. Le risque réel est apprécié **avant** l'exécution, et consigné.
2. Un changement classé R0 dans un profil Reinforced n'exige pas de restauration testée : il exige ce que son risque impose.
3. Un changement à risque élevé dans un profil Lite exige les mesures du niveau élevé : le profil bas ne réduit pas le risque.
4. En cas de doute entre deux niveaux, le niveau supérieur s'applique.
5. Le profil Reinforced conserve une exigence plancher : tout changement non trivial y est au minimum au niveau « modéré ».

| Situation | Exigence supplémentaire |
|---|---|
| Incident de sécurité | Confinement d'abord, rollback ensuite |
| Opération irréversible engagée | Aucun rollback possible : décision VALIDATOR avant exécution |

### 10.3 Rollback et changement

Un rollback qui défait une décision validée **est un changement** : il s'instruit comme tel, avec identifiant `CHG-` ou `URG-`.

---

## 11. Incident de sécurité

### 11.1 Déclenchement

Tout événement touchant un secret, une donnée sensible, une permission ou l'intégrité du dépôt est un incident. Il relève au minimum de **S0** (`GC-35`).

### 11.2 Procédure

| # | Action | Délai | Acteur |
|---|---|---|---|
| 1 | **Confiner** : couper l'accès, révoquer le secret, désactiver la fonction | Immédiat | agent constatant |
| 2 | **Préserver** : ne rien supprimer, copier les traces | Immédiat | agent constatant |
| 3 | **Alerter** le VALIDATOR | Immédiat | ORCHESTRATOR |
| 4 | **Bloquer** le projet | Immédiat | ORCHESTRATOR |
| 5 | **Qualifier** : P0, S0, portée, données touchées | 24 h (recommandé) | ORCHESTRATOR |
| 6 | **Auditer** : cause, chronologie, mesures existantes | Avant reprise | AUDITOR |
| 7 | **Corriger** ou accepter explicitement | Avant reprise | VALIDATOR |
| 8 | **Régulariser** en `URG-AAAA-NNNN` | Avant clôture | ORCHESTRATOR |

### 11.3 Interdits

- Supprimer un journal pour « nettoyer ».
- Réécrire l'historique Git pour masquer un commit.
- Reprendre sans audit.
- Annoncer une reprise sans preuve de correction.
- Considérer l'incident clos parce qu'il ne se reproduit plus.

---

## 12. Clôture d'incident

Un incident est clos lorsque quatre éléments existent :

1. **Cause** identifiée, ou explicitement déclarée inconnue.
2. **Mesures** prises, avec preuve.
3. **Décision** du VALIDATOR sur la reprise.
4. **Trace** conservée dans `docs/governance/incidents/`.

Une clôture sans cause ni mesure n'est pas une clôture : c'est un oubli organisé.

---

## 13. Ce que la reprise n'autorise jamais

- Réutiliser un identifiant consommé (`GC-46`).
- Poursuivre avec un mandat périmé (`GC-30`).
- Corriger un état sans preuve de l'écart.
- Passer un contrôle `NOT_CHECKED` en `PASS` (`GC-25`).
- Reprendre sans vérifier la cohérence état/reçu (A2).
- Déclarer une permission technique sans test (`GC-36`).

---

## 14. Limites

| Limite | Statut |
|---|---|
| Exigence de rollback fondée sur le risque réel (C34) | Aucun seuil quantitatif de risque défini : l'appréciation reste humaine (`INCONNU`) |
| Risque faible en profil Lite ou Standard | Aucune restauration testée exigée : conséquence assumée de la proportionnalité |
| Aucun RTO / RPO défini | `INCONNU` |
| Aucune durée de conservation des incidents | `INCONNU` |
| Aucun isolement technique vérifié | `unknown` (voir `implementations/opencode/agent_permissions.md`) |
| Reprise après interruption non décrite par les sources | `RECOMMANDATION` (§5.2) |
| `docs/governance/incidents/` non créé dans le pilote | Registre inexistant |

---

## 15. Renvois

| Sujet | Document |
|---|---|
| États et invariants | `protocol/state_model.md` |
| Transitions et reçus | `protocol/transition_policy.md` |
| Décisions et gravités | `protocol/decision_policy.md` |
| Changements et urgences | `protocol/change_control.md` |
| Permissions et violations | `protocol/permission_policy.md` |

---

## 16. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 4) |
| 0.2 | 2026-11-20 | C34 intégré : exigence de rollback fondée sur le risque réel, le profil ne fixant qu'un plancher |
