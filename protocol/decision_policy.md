# Politique de décision

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | Valeurs de décision, gravités, preuves, réserves, conditions d'acceptation |
| Autorité | Normatif — source unique des décisions |
| Vague | 4 |

**Sources citées :** `F3` = `AKORIS_consolide.md` §8, §9 · `F2` = `AKORIS_architecture_documentaire.md` §4.7 · `GC` = `protocol/governance_core.md` · `SM` = `protocol/state_model.md` · décisions VALIDATOR **A1**, **A2**.

---

## 0. Objet

Cette politique définit **comment une décision est prise, sur quelles preuves, et avec quelles conséquences**.

Elle ne définit ni les états (`state_model.md`), ni les transitions (`transition_policy.md`), ni les permissions (`permission_policy.md`). Elle répond à une seule question : *compte tenu de ce qui est prouvé, que faut-il décider ?*

---

## 1. Qui décide

| Acteur | Rôle | Limite |
|---|---|---|
| **VALIDATOR** | Décide | Aucune décision ne lui est substituable |
| **ORCHESTRATOR** | Analyse et **recommande** | Une recommandation n'est pas une décision (`GC-05`) |
| **AUDITOR** | Constate et **recommande** | Ne décide pas, ne corrige pas |
| **BUILDER** | Rapporte | Ne décide pas, ne s'auto-accepte pas |

**Règle :** une décision sans auteur humain identifié et daté n'existe pas (`GC-29`).

---

## 2. Objets de décision

Une décision porte toujours sur un objet identifié. Le même vocabulaire s'applique, les conditions diffèrent.

| Objet | Moment | Document de référence |
|---|---|---|
| Checkpoint (CP1, CP2, CP3) | Fin de phase | Cadrage, conception, readiness |
| Sprint | Après audit | Rapport d'audit |
| Changement | Après analyse d'impact | `protocol/change_control.md` |
| Réserve | À l'acceptation ou plus tard | Fiche de réserve |
| Fusion vers `main` | Après acceptation | Décision **distincte** |
| Déploiement | Après fusion | Décision **distincte** |
| Clôture de projet | Fin de vie | Bilan, risques résiduels |

---

## 3. Les cinq valeurs

```text
GO
GO_WITH_RESERVES
NO_GO
HOLD
CANCELLED
```

> **Décision A1.** Ces cinq valeurs sont normatives, en majuscules, avec underscore. Les formes `GO WITH RESERVES` et `NO GO` du pilote v1 sont **abandonnées**.

| Valeur | Signification | Condition | Conséquence |
|---|---|---|---|
| **`GO`** | Le résultat est accepté sans condition | Toutes les conditions de §6 sont réunies | Le sprint passe à `accepted` |
| **`GO_WITH_RESERVES`** | Le résultat est accepté sous conditions tracées | Aucune anomalie S0/S1, réserves qualifiées et affectées | Le sprint passe à `accepted_with_reserves` |
| **`NO_GO`** | Le résultat est refusé | Au moins une condition de §6 n'est pas remplie | Correction ou abandon |
| **`HOLD`** | La décision **ne peut pas** être prise | Preuve, arbitrage ou cohérence manquants | Gel, pas de décision |
| **`CANCELLED`** | L'objet est abandonné | Décision explicite du VALIDATOR | Sprint ou projet annulé |

**`HOLD` n'est pas un refus.** C'est la reconnaissance honnête qu'une décision serait mal fondée. Un `HOLD` transformé en `GO` par lassitude est une faute de gouvernance.

**`CANCELLED` n'est pas un `NO_GO`.** Un `NO_GO` demande une correction ; un `CANCELLED` met fin à l'objet.

---

## 4. Gravité des anomalies

| Niveau | Définition | Décision habituelle | Réserve possible ? |
|---|---|---|---|
| **S0** | Critique : sécurité, données, secret, risque grave | `NO_GO` | **Non** |
| **S1** | Majeure : exigence essentielle non satisfaite | `NO_GO` | **Non** |
| **S2** | Modérée : défaut maîtrisable avec contournement | Réserve possible | Oui |
| **S3** | Mineure : défaut limité ou amélioration | `GO` possible | Facultative |

La qualification précède la décision (`GC-42`). Une anomalie non qualifiée interdit de conclure : c'est un `HOLD`.

---

## 5. Preuves

### 5.1 Statuts de preuve

```text
directly_verified
reproduced
cross_checked
declared_only
partial
missing
invalid
```

| Statut | Signification | Critère critique | Critère non critique |
|---|---|---|---|
| `directly_verified` | Constaté directement | Accepté | Accepté |
| `reproduced` | Reproduit par un tiers | Accepté | Accepté |
| `cross_checked` | Vérifié par un autre moyen | Accepté avec mention | Accepté |
| `declared_only` | Simple déclaration | **Refusé** | Accepté, signalé |
| `partial` | Couverture incomplète | Refusé pour la partie non couverte | Accepté avec réserve |
| `missing` | Absente | **Refusé** | Refusé |
| `invalid` | Non conforme ou non fiable | **Refusé** | Refusé |

### 5.2 Statuts de contrôle

```text
PASS
FAIL
PARTIAL
N/A
NOT_CHECKED
```

**`NOT_CHECKED` ne vaut jamais `PASS`** (`GC-25`). Un contrôle non réalisé est déclaré non réalisé, jamais omis (`GC-26`).

### 5.3 Règle de suffisance

Une décision est **fondée** si, pour chaque critère obligatoire, il existe une preuve d'un statut acceptable. Un seul critère critique couvert par `declared_only` suffit à rendre la décision infondée — donc à imposer `HOLD`.

---

## 6. Conditions du `GO`

Les neuf conditions suivantes sont **cumulatives** :

| # | Condition | Preuve attendue |
|---|---|---|
| 1 | Périmètre clairement défini | Mandat versionné |
| 2 | Exigences obligatoires satisfaites | Matrice de couverture |
| 3 | Critères vérifiés | Statuts de contrôle |
| 4 | Tests pertinents passés | Résultats reproductibles |
| 5 | Aucune anomalie S0 ou S1 | Rapport d'audit |
| 6 | Preuves disponibles | Références de preuve |
| 7 | Mandat respecté | Comparaison mandat / livré |
| 8 | Transition valide et consommée | Reçu de transition |
| 9 | Risques acceptables pour le profil | Analyse de risque |

Une condition non établie n'est pas « probablement remplie » : elle est **non établie**, et la décision est `HOLD`.

---

## 7. Conditions du `GO_WITH_RESERVES`

### 7.1 Réserves autorisées

Une réserve ne peut couvrir qu'une anomalie **S2**, ou une S3 non bloquante. Elle ne peut jamais couvrir :

- une anomalie S0 ou S1 ;
- un changement de périmètre ;
- une preuve manquante sur un critère critique ;
- une violation de permission P0 ou P1.

Une réserve qui masque une anomalie critique n'est pas une réserve : c'est un contournement.

### 7.2 Les dix attributs obligatoires

| # | Attribut | Contenu |
|---|---|---|
| 1 | Identifiant | Unique, stable |
| 2 | Description | Ce qui n'est pas conforme |
| 3 | Gravité | S2 ou S3 |
| 4 | Impact | Conséquence si non traitée |
| 5 | Responsable | Acteur affecté |
| 6 | Tâche de résolution | Action attendue |
| 7 | Sprint de résolution | Échéance planifiée |
| 8 | Échéance | Date cible |
| 9 | Méthode de vérification | Comment la clôture sera prouvée |
| 10 | Décision humaine | Acte d'acceptation de la réserve |

Une réserve sans responsable ni échéance n'est pas une réserve : c'est une intention.

---

## 8. Conditions du `NO_GO` et du `HOLD`

### 8.1 `NO_GO`

Prononcé dès qu'une condition du `GO` échoue et qu'aucune réserve n'est admissible. Il ouvre la voie à une **correction**, pas à une négociation.

### 8.2 `HOLD` — six motifs

| # | Motif |
|---|---|
| 1 | Une preuve critique manque |
| 2 | Une décision métier manque |
| 3 | Des documents se contredisent |
| 4 | Le résultat n'est pas reproductible |
| 5 | L'état central est incohérent (divergence état/reçu incluse — A2) |
| 6 | Une dépendance doit être clarifiée |

Le `HOLD` suspend la décision sans suspendre la traçabilité : le motif est consigné, la levée est datée.

---

## 9. Décisions dérivées

| Décision | Condition | Ne peut pas être déduite de |
|---|---|---|
| Fusion vers `main` | `GO` ou `GO_WITH_RESERVES` **et** décision distincte | L'acceptation du sprint (`GC-07`) |
| Déploiement | Fusion effectuée **et** décision distincte | La fusion |
| Sprint suivant | Décision distincte | L'acceptation du sprint |
| Accès à de nouvelles données | Décision distincte | Une autorisation précédente |
| Modification d'architecture | Procédure de changement | Une acceptation de sprint |
| Clôture de projet | Bilan complet | Le dernier `GO` |

**Aucune décision n'en implique une autre par défaut.** C'est le principe le plus souvent contourné, et le plus coûteux quand il l'est.

---

## 10. Décision et violation de permission

Une violation qualifiée **P0** ou **P1** peut invalider un résultat **même si le code fonctionne** (`GC-44`).

| Niveau | Effet sur la décision |
|---|---|
| P0 | `NO_GO` immédiat ; incident de sécurité |
| P1 | `HOLD` ou `NO_GO` ; invalidation possible |
| P2 | Réserve admissible si le périmètre est rétabli |
| P3 | Correction documentaire |

Une violation ne se « compense » pas par un résultat satisfaisant : elle se traite (`GC-43`).

---

## 11. Traçabilité de la décision

Chaque décision consigne au minimum :

| Champ | Contenu |
|---|---|
| Identifiant | Décision ou objet concerné |
| Type | Checkpoint, sprint, changement, réserve, fusion, déploiement |
| Valeur | `GO`, `GO_WITH_RESERVES`, `NO_GO`, `HOLD`, `CANCELLED` |
| Auteur | VALIDATOR |
| Date | Horodatage |
| Motif | Justification, en une phrase |
| Preuves | Références |
| Réserves | Liste, le cas échéant |
| Effet | État résultant |

Ces éléments alimentent `state.json` (`last_decision`) et, à terme, `reference/decision_log.md` — **fichier planifié, non créé**.

---

## 12. Limites et points ouverts

| Limite | Statut |
|---|---|
| Aucun seuil quantitatif de gravité | `INCONNU` — la qualification reste humaine |
| Aucune règle de quorum ou de délégation | `INCONNU` |
| `reference/decision_log.md` inexistant | Le registre des décisions reste partiel |
| Décision en cas d'absence prolongée du VALIDATOR | `INCONNU` — le cadre suppose sa disponibilité |

---

## 13. Renvois

| Sujet | Document |
|---|---|
| États résultants | `protocol/state_model.md` |
| Transitions et reçus | `protocol/transition_policy.md` |
| Changements | `protocol/change_control.md` |
| Audit | `protocol/audit_policy.md` |
| Réponses aux incidents | `protocol/recovery_policy.md` |
| Forme des décisions et réserves | `templates/decision_template.md`, `templates/reserve_template.md` |

---

## 14. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 4) — intégration A1 |
