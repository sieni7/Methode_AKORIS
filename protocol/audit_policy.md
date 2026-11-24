# Audit Policy

| Champ | Valeur |
|---|---|
| Version | 0.3 |
| Date | 2026-11-21 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | Méthode de vérification indépendante : `readiness_review` et `sprint_audit` |
| Autorité | Normatif — source unique de l'audit |
| Vague | 5 |

**Sources citées :** `F3` = `AKORIS_consolide.md` §11, §14, §15 · `F2` = `AKORIS_architecture_documentaire.md` §4.9, §8.5, §8.9, §10.5 · `GC` = `protocol/governance_core.md` · `DP` = `protocol/decision_policy.md` · `SM` = `protocol/state_model.md` · `TP` = `protocol/transition_policy.md` · `PP` = `protocol/permission_policy.md` · `CC` = `protocol/change_control.md` · `RP` = `protocol/recovery_policy.md` · `T` = `reference/terminology.md` · décisions **A2**, **A5**, **C13**, **C19**, **C22**, **C26**, **C27**, **C28**, **C29**, **C30**, **C31**.

---

## 1. Objet

Cette politique définit **comment un contrôle indépendant est préparé, exécuté et rapporté** dans le cadre AKORIS.

Elle répond à quatre questions :

1. Que vérifie-t-on, et à quel moment ?
2. Comment le vérifie-t-on, et sur quelles preuves ?
3. Comment un désaccord est-il conservé ?
4. Que se passe-t-il après le rapport ?

Elle ne définit **ni** les états (`SM`), **ni** les valeurs de décision (`DP` §3), **ni** les règles de permission (`PP`), **ni** la procédure de changement (`CC`).

**Chaîne d'audit normative (`F3` §11) :**

```text
Mandat → Code livré → Commits → Tests → Preuves → Critères d'acceptation → Résultat
```

> **Principe fondateur.** Le rapport de BUILDER est une **source d'information**, pas la source première de vérité. L'auditeur vérifie directement (`F3` §11).

---

## 2. Distinction entre `readiness_review` et `sprint_audit`

> **Décision C19.** Ces deux contrôles sont **distincts**, non substituables, et portent des noms normatifs différents (`T` §4).

| Dimension | `readiness_review` | `sprint_audit` |
|---|---|---|
| Objet | Aptitude à démarrer | Résultat produit par BUILDER |
| Moment | **Avant** exécution | **Après** exécution |
| Question | « Les conditions sont-elles réunies ? » | « Ce qui a été livré est-il conforme ? » |
| Déclencheur | Checkpoint de préparation, dont CP3 (`F3` §14) | Sprint achevé et rapport BUILDER déposé |
| Entrée | Cadrage, contrats, permissions, Git, état central, premier sprint | Mandat audité, commits, tests, critères, reçu |
| Livrable | Rapport de revue de préparation | Rapport d'audit de sprint |
| Emplacement | `docs/governance/readiness/` (décision **C13**) | `audit_report/` |
| Décision associée | Validation du checkpoint par le VALIDATOR (`GC`, `F3` §14) | Décision sur le sprint (`DP` §3) |
| Remplace l'autre ? | **Non** | **Non** |

**Règles :**

1. Une `readiness_review` réussie **ne prouve pas** la conformité d'un résultat futur.
2. Un `sprint_audit` réussi **ne répare pas** une préparation défaillante.
3. Aucun checkpoint opérationnel ne doit être déclenché avant validation du checkpoint concerné (`F3` §14).
4. Les deux contrôles portent des références, des preuves et des décisions distinctes ; ils ne partagent pas de rapport.
5. Le terme générique « audit » employé seul est **ambigu** : dans un document normatif, il doit être remplacé par l'un des deux termes ci-dessus.
6. **Décision C13 appliquée.** La politique distingue trois éléments distincts :
   1. **Emplacement doctrinal futur** : `docs/governance/readiness/` est l'emplacement normatif de la `readiness_review`.
   2. **Fichier historique du pilote** : `docs/governance/initialization_readiness_report.md` est conservé comme preuve historique ; il n'est ni réécrit ni promu en source concurrente.
   3. **Éventuelle procédure de migration ultérieure** : elle n'est pas définie à ce jour. Un transfert ou une conversion du rapport historique ferait l'objet d'une décision distincte ; aucune migration n'est réalisée par la présente politique.

---

## 3. Rôles et responsabilités

| Acteur | Responsabilité dans l'audit | Limite |
|---|---|---|
| **BUILDER** | **Démontre** ce qu'il a réalisé : rapport, preuves, tests exécutés | Son affirmation n'est pas une preuve ; il ne s'auto-certifie pas |
| **AUDITOR** | **Vérifie directement** le résultat, classe les preuves, rédige le rapport | Ne corrige pas, ne décide pas, ne modifie pas l'état |
| **ORCHESTRATOR** | Analyse le rapport, compare avec l'état, formule une **recommandation** | Une recommandation n'est pas une décision (`GC-05`) |
| **VALIDATOR** | **Prend la décision finale** : accepter, refuser, réserver, suspendre | Aucune décision ne lui est substituable |
| **DOCUMENTATION BUILDER** | Hors boucle d'exécution (`A5`) | Rôle documentaire auxiliaire, ni agent de sprint, ni auditeur |

**Interdictions applicables à AUDITOR :**

- ne corrige **pas** le code qu'il audite ;
- ne modifie **pas** `state.json` ;
- ne modifie **pas** le mandat (`current_sprint.md`) ;
- ne modifie **pas** les décisions validées ni `debt_report/` ;
- ne commite pas, ne pousse pas, ne fusionne pas ;
- ne s'auto-autorise pas : toute action exige un `GO` et un `transition_id` valide (`C22`).

**Règle de séparation :** l'agent qui produit le résultat ne doit pas être l'unique juge de ce résultat (`F3` §4). Cette séparation est procédurale tant qu'une indépendance technique n'est pas prouvée (`PP`).

---

## 4. Sources de référence

### 4.1 Hiérarchie d'autorité

| Rang | Source | Usage |
|---|---|---|
| 1 | Décision humaine explicitement validée | Prime sur tout le reste |
| 2 | Protocole AKORIS le plus récent | Règles communes |
| 3 | Politique spécialisée correspondante | Domaine considéré |
| 4 | Cartographie documentaire | Organisation et statuts |
| 5 | Sources historiques | Contexte, jamais correction silencieuse |
| 6 | Recommandation documentaire | À qualifier explicitement |
| 7 | Proposition du DOCUMENTATION BUILDER | À qualifier explicitement |

### 4.2 Sources du projet à examiner

`state.json`, `state.md` (vue générée, jamais source), `current_sprint.md`, `contexte.md`, `agents.md`, `docs/**` selon le domaine, `sprint_report/`, dépôt Git, sorties de tests, journaux CI, reçus de transition.

**Règle de non-duplication :** chaque notion reste dans sa source unique (`document_map.md` §8). La présente politique **renvoie** aux définitions existantes ; elle ne les recopie pas.

---

## 5. Conditions d'entrée

### 5.1 `readiness_review`

| # | Condition |
|---|---|
| 1 | Périmètre et objectifs consignés |
| 2 | Contrats d'agents disponibles et cohérents entre eux |
| 3 | Permissions **déclarées** et classées sans certification implicite |
| 4 | Configuration Git et état central accessibles |
| 5 | Premier sprint défini |
| 6 | Checkpoint à valider identifié |

### 5.2 `sprint_audit`

| # | Condition |
|---|---|
| 1 | Transition vers AUDITOR valide, avec `transition_id` (`TP`, `C22`) |
| 2 | Reçu de transition déposé et cohérent avec l'état (`A2`) |
| 3 | Mandat audité disponible et versionné |
| 4 | Rapport BUILDER déposé |
| 5 | Commits et modifications accessibles |
| 6 | Critères d'acceptation définis et vérifiables |
| 7 | Tests reproductibles dans l'environnement disponible |

### 5.3 Condition bloquante commune

Toute divergence entre `state.json`, un reçu et l'historique **bloque le contrôle** jusqu'à réconciliation (`A2`, `SM` §7, `RP` §7). Le contrôle n'est pas « passé avec réserve » : il est **arrêté**.

Une condition d'entrée absente est déclarée `NOT_CHECKED` ou `PARTIAL` ; elle n'est **jamais** interprétée comme un succès.

---

## 6. Méthode de contrôle

### 6.1 Séquence (`F3` §11.1)

| # | Étape |
|---|---|
| 1 | Vérifier la transition |
| 2 | Lire le mandat |
| 3 | Lire les exigences et les critères |
| 4 | Inspecter le dépôt |
| 5 | Examiner les commits |
| 6 | Reproduire les tests pertinents |
| 7 | Tester les cas limites et négatifs |
| 8 | Vérifier les modifications hors périmètre |
| 9 | Classer les preuves |
| 10 | Produire le rapport |

### 6.2 Statuts de contrôle

Les statuts normatifs sont ceux de `DP` §5.2 : `PASS`, `FAIL`, `PARTIAL`, `N/A`, `NOT_CHECKED`.

> **Clarification terminologique (`RECOMMANDATION`).** La consigne d'employer `UNKNOWN` pour un contrôle impossible est ici comprise comme le classement `unknown` des permissions (`PP`, `T` §6) : `UNKNOWN` **n'est pas un statut de contrôle** dans `DP` §5.2. Un contrôle impossible est donc `NOT_CHECKED` ou `PARTIAL`, et la **permission** concernée reste `unknown`. Cette clarification est une recommandation de rédaction, non une décision validée.

**Règles :**

1. `NOT_CHECKED` ne vaut jamais `PASS` (`GC-25`).
2. Un contrôle non réalisé est déclaré, jamais omis (`GC-26`).
3. `N/A` exige une justification.
4. Un test non exécuté ne vaut pas `PASS` (§9).
5. Une affirmation de BUILDER n'est pas automatiquement une preuve (§10).

---

## 7. Contrôle du périmètre

| Vérification | Méthode | Écart constaté |
|---|---|---|
| Périmètre réel vs mandat | Comparaison des fichiers modifiés et de la fiche de mandat | Écart au sens de `CC` §1 |
| Actions autorisées vs actions observées | Reçu, commits, journaux | Violation de permission possible (`PP`) |
| Documents devenus faux | Revue des documents référencés | Anomalie **S1** (`CC` §9) |
| Transition utilisée | `transition_id` unique, non réutilisé (`TP`, `C30`) | Divergence bloquante |

**Règle C30 :** une transition `consumed` n'est pas réutilisable et ne revient pas à `authorized` ; elle peut progresser vers `in_progress`, puis `completed`. L'audit vérifie la progression, jamais une réactivation.

Toute extension de périmètre est traitée selon `CC` — jamais validée dans le rapport d'audit.

---

## 8. Contrôle des tâches et critères d'acceptation

1. Vérifier **chaque tâche du mandat, une par une**, avec un statut de contrôle (`F3` §11.1).
2. Confronter chaque critère à une observation directe, pas à une déclaration.
3. Un critère critique couvert par `declared_only` est **refusé** (`DP` §5.1).
4. Une tâche partiellement couverte reçoit `PARTIAL`, avec la part non couverte nommée.
5. L'auditeur n'interprète pas une exigence ambiguë en faveur du résultat : il la signale et propose un `HOLD` (`DP` §8.2).
6. La conclusion par affirmation est l'une des quatre formes de `F3` §11.2 — voir §16.

---

## 9. Contrôle des tests et de la reproductibilité

| Exigence | Contenu |
|---|---|
| Reproduction | Relancer les tests pertinents, avec date, commande exacte et sortie conservée |
| Couverture | Cas limites et cas négatifs inclus (`F3` §11.1) |
| Environnement | Toute différence avec l'environnement de BUILDER est déclarée |
| Résultat | `PASS`, `FAIL`, `PARTIAL` ou `NOT_CHECKED` — jamais déduit d'une affirmation |
| Irréproductibilité | `PARTIAL` ou `NOT_CHECKED`, avec motif ; jamais `PASS` |

**Règle absolue :** un test non exécuté ne vaut pas `PASS`. Un test dont la sortie n'est pas conservée n'est pas une preuve reproductible.

---

## 10. Contrôle des preuves

Les statuts de preuve et la règle de suffisance sont définis dans `DP` §5 — ils ne sont pas repris ici.

**Règles d'audit :**

1. Classer chaque preuve selon `DP` §5.1 avant de l'employer.
2. Privilégier l'inspection directe et la reproduction ; `cross_checked` doit être mentionné comme tel.
3. Une preuve `declared_only` ne valide jamais un critère critique.
4. Une preuve `missing` ou `invalid` interdit de conclure au `PASS`.
5. L'absence de preuve est un **fait constaté** : elle est rapportée, pas comblée par une hypothèse.
6. Les éléments non vérifiés figurent explicitement dans le rapport (§17).

---

## 11. Contrôle Git et des fichiers modifiés

| Point | Vérification |
|---|---|
| Branche | Travail sur branche dédiée, pas directement sur `main` (`F3` §16) |
| Commits | Traçables, cohérents, attribuables |
| Diff | Fichiers modifiés comparés au mandat |
| Conventions | Respect des règles du projet gouverné |
| Secrets | Recherche avant commit et avant fusion (`F3` §16) |
| `main` | Protection **à vérifier, non supposée** (`F3` §16) — maintenue `unknown` (décision **C29**) |
| Fusion | Décision humaine **distincte**, jamais déduite de l'acceptation (`DP` §9) |

Un commit absent, réécrit ou non traçable est une rupture de traçabilité (`RP` §8). La protection de `main` est maintenue `unknown` tant qu'un test concluant n'existe pas.

---

## 12. Contrôle des permissions

Les trois catégories et les cinq classifications sont définies dans `PP` — elles ne sont pas reproduites ici.

**Règles d'audit :**

1. Une permission **déclarée ne vaut pas** permission techniquement appliquée (`GC-36`).
2. Une configuration lue sans test contradictoire reste `unknown`.
3. Aucune permission n'est classée `technical_enforced` sans preuve d'exécution.
4. Une violation qualifiée P0 ou P1 est signalée immédiatement et traitée selon `RP` §11 — elle ne se compense pas par un résultat satisfaisant (`DP` §10).
5. L'indépendance d'AUDITOR est **procédurale** tant que son isolation technique n'est pas prouvée.
6. Le constat détaillé de l'implémentation de référence figure dans `implementations/opencode/agent_permissions.md`.

### 12.1 Tests attendus T1 à T5

| # | Test | Attendu | Statut actuel |
|---|---|---|---|
| T1 | BUILDER édite `state.json` | Refus | **NON EXÉCUTÉ** |
| T2 | BUILDER écrit `state.json` par shell | Refus | **NON EXÉCUTÉ** |
| T3 | ORCHESTRATOR édite `src/**` | Refus | **NON EXÉCUTÉ** |
| T4 | Tentative de fusion ou de push non autorisé vers une branche protégée autre que `main`, dans un dépôt de test | Refus | **NON EXÉCUTÉ** |
| T5 | Tentative équivalente de fusion ou de push non autorisé vers `main`, dans un dépôt de test (décision **C29**) | Refus | **NON EXÉCUTÉ** — test préparé |

Un simple changement de branche (`checkout` ou `switch`) ne suffit pas, à lui seul, à tester le blocage d’une fusion ou d’un push.

Le contrôle consistant à demander à AUDITOR d’éditer `src/**` reste une vérification complémentaire des permissions inter-rôles. Il n’est ni T4 ni un nouveau test T1–T5, et ne reçoit aucun identifiant de test supplémentaire.

**Statut actuel :**
`NON EXÉCUTÉ`

**Justification :**
Ces tests nécessitent le lancement des agents sous leur configuration d'exécution propre. Le DOCUMENTATION BUILDER ne peut pas les certifier depuis son rôle documentaire.

**Conséquence :**
Les permissions concernées restent classées `unknown`.

---

## 13. Contrôle des changements et réserves

| Objet | Vérification | Référence |
|---|---|---|
| Changement déclaré | Identifiant `CHG-` ou `URG-`, analyse d'impact, décision | `CC` |
| Mandat | Version cohérente ; autorisation non périmée | `CC` §6 |
| Réserve | Attributs complets, responsable, échéance, méthode de vérification | `DP` §7.2 |
| `HOLD` | Décision `HOLD`, changement maintenu en `awaiting_decision` | **C31** |
| Reçu ORCHESTRATOR | Déposé dans `docs/governance/receipts/` par le destinataire | Décision **C26** |

**Règle :** l'auditeur constate et qualifie ; il n'accepte pas une réserve à la place du VALIDATOR. Une réserve sans responsable ni échéance est signalée comme défaut de forme, pas validée.

---

## 14. Classification des anomalies

Les gravités **S0 à S3** et les niveaux de violation **P0 à P3** sont définis dans `DP` §4 et §10 — ils ne sont pas redéfinis ici.

**Règles d'audit :**

1. Toute anomalie est **qualifiée** avant d'être rapportée (`GC-42`).
2. Une anomalie non qualifiée interdit de conclure : `HOLD` (`DP` §4).
3. Une anomalie S0 ou S1 ne peut pas être couverte par une réserve (`DP` §7.1).
4. Une violation P0 entraîne un `NO_GO` immédiat et un incident (`RP` §11).
5. L'auditeur **signale** une contradiction entre documents ; il ne la corrige pas silencieusement (`GC`).

---

## 15. Limites de l'audit

### 15.1 Ce que l'audit ne peut pas faire

- certifier une permission technique sans test exécuté ;
- remplacer la décision du VALIDATOR ;
- corriger le code, l'état ou le mandat ;
- garantir l'absence de défaut non observé ;
- valider une affirmation invérifiable ;
- couvrir un périmètre sans l'avoir déclaré.

Toute limite est **écrite dans le rapport**, avec son effet sur la portée de la conclusion.

### 15.2 Points ouverts conservés

| Réf. | Sujet | Statut |
|---|---|---|
| **C25** | Échelle de risque chiffrée — aucune n'existe | `INCONNU` |
| **T1 à T5** | Tests techniques de permissions | `NON EXÉCUTÉ` |
| **C29** | Protection effective de `main` | `unknown` — T5 préparé, non exécuté |

**Décisions désormais intégrées :** **A2** — v2.0 est la structure normative, le pilote v1.0 un écart historique (`SM` §6.1, `reference/state.schema.json`) ; **C13** — `docs/governance/readiness/`, rapport pilote conservé ; **C26** — `docs/governance/receipts/` ; **C27** — aucune durée numérique par défaut, expiration selon mandat et profil ; **C28** — schéma technique créé ; **C29** — protection de `main` maintenue `unknown`. Elles ne sont plus des points ouverts.

> **Rappel.** Aucune de ces décisions ne requalifie une permission en `technical_enforced`. La préparation de T5 ne constitue pas son exécution.

---

## 16. Désaccords et contre-constats

L'auditeur doit pouvoir conclure, pour chaque affirmation de BUILDER (`F3` §11.2) :

| Conclusion | Signification |
|---|---|
| **Confirmée** | Le contrôle direct établit l'affirmation |
| **Partiellement confirmée** | Une partie seulement est établie ; le reste est nommé |
| **Non confirmée** | Aucune preuve directe n'a été trouvée |
| **Contredite** | Le contrôle direct établit le contraire |

**Règles :**

1. Un désaccord est **conservé dans les rapports** : les deux affirmations y figurent, avec leurs preuves.
2. Aucune version n'est « corrigée » pour faire disparaître le désaccord (`GC-41`).
3. Un contre-constat est qualifié : anomalie, divergence documentaire, violation de permission ou incertitude.
4. L'arbitrage appartient au VALIDATOR ; l'ORCHESTRATOR prépare la recommandation.
5. Un désaccord non arbitré conduit à un `HOLD`, pas à un compromis implicite.

---

## 17. Rapport attendu

### 17.1 Contenu minimal (`F3` §11.2)

| # | Élément |
|---|---|
| 1 | Identification : type de contrôle, date, auteur, rôle |
| 2 | Périmètre audité |
| 3 | Limites de l'audit |
| 4 | Sources examinées |
| 5 | Méthode |
| 6 | Transition concernée : `transition_id`, reçu |
| 7 | Tâches vérifiées, une par une, avec statut |
| 8 | Tests reproduits, avec commandes et sorties |
| 9 | Écarts et anomalies qualifiées |
| 10 | Preuves, avec statut selon `DP` §5.1 |
| 11 | Éléments non vérifiés |
| 12 | Comparaison avec le rapport BUILDER |
| 13 | Désaccords conservés |
| 14 | Recommandation — **jamais une décision** |

### 17.2 Forme

- Le rapport est un livrable de AUDITOR ; il n'est pas un état du projet.
- Son statut est **recommandation** : il ne modifie ni `state.json` ni le mandat.
- L'emplacement du rapport de sprint est `audit_report/` ; celui de la `readiness_review` est `docs/governance/readiness/` (décision **C13**).
- Le modèle de rapport est `templates/auditor_report_template.md` — créé en vague 6.

---

## 18. Décision et suite

```text
AUDITOR produit le rapport (constats + recommandation)
        ↓
ORCHESTRATOR analyse et recommande
        ↓
VALIDATOR décide
        ↓
Correction, acceptation, réserve ou changement distinct
```

Les valeurs de décision sont celles de `DP` §3 : `GO`, `GO_WITH_RESERVES`, `NO_GO`, `HOLD`, `CANCELLED`. Elles ne sont pas redéfinies ici.

**Règles de suite :**

1. L'acceptation d'un sprint n'autorise **ni** le sprint suivant, **ni** la fusion vers `main`, **ni** le déploiement, **ni** l'accès à de nouvelles données, **ni** une modification d'architecture (`F3` §15, `DP` §9).
2. Une transition `consumed` progresse vers `in_progress` puis `completed` sans réutilisation (`C30`).
3. Un `HOLD` laisse le changement en `awaiting_decision` avec `decision = HOLD` (`C31`).
4. Toute divergence état/reçu détectée après le rapport est bloquante (`A2`).
5. Un incident identifié pendant l'audit suit `RP` §11.

---

## 19. Profil Lite

| Aspect | Exigence |
|---|---|
| Audits | Ciblés, sur les éléments à risque du mandat |
| Preuves | Déclarées et classées ; inspection directe sur les points critiques |
| Tests | Reproduction des tests pertinents uniquement |
| Rapport | Allégé, mais avec limites et éléments non vérifiés |
| Permissions | `unknown` déclaré ; aucune garantie technique affirmée |

Un contrôle non réalisé reste `NOT_CHECKED` : la réduction d'exigence ne réduit pas l'obligation de vérité.

---

## 20. Profil Standard

| Aspect | Exigence |
|---|---|
| Audits | Audit de chaque sprint (`F3` §4.2) |
| Preuves | Classification complète, comparaison avec le rapport BUILDER |
| Tests | Reproduction des tests pertinents, cas limites inclus |
| Rapport | Structure complète du §17 |
| Réserves | Attributs complets selon `DP` §7.2 |
| Permissions | `unknown` déclaré ; mesures compensatoires documentées |

---

## 21. Profil Reinforced

| Aspect | Exigence |
|---|---|
| Audits | Vérification approfondie des exigences critiques (`F3` §4.3) |
| Preuves | Reproductibilité exigée ; `declared_only` refusé sur tout critère critique |
| Tests | Reproduction indépendante, cas négatifs, environnement contrôlé |
| Sécurité | Recherche de secrets, contrôle des accès, examen des surfaces exposées |
| Reprise | Rollback fondé sur le **risque réel**, pas sur le seul profil (`RP` §10.2, C34) |
| Permissions | Aucune garantie sans test concluant ; sinon mesure compensatoire explicite |

Le profil Reinforced n'autorise **pas** à présenter une permission `unknown` comme `technical_enforced` : il exige davantage de preuves, pas une déclaration plus forte.

---

## 22. Références

| Sujet | Document |
|---|---|
| Vocabulaire `readiness_review` / `sprint_audit` | `reference/terminology.md` §4 |
| Règles communes et statuts épistémiques | `protocol/governance_core.md` |
| Gravités, preuves, réserves, décisions | `protocol/decision_policy.md` §3 à §7 |
| États, invariants, divergence état/reçu | `protocol/state_model.md` |
| Transitions, reçus, `transition_id` | `protocol/transition_policy.md` |
| Classifications de permission, tests T1 à T5 | `protocol/permission_policy.md` |
| Constat technique de l'implémentation | `implementations/opencode/agent_permissions.md` |
| Changements et urgences | `protocol/change_control.md` |
| Incidents, reprises, rollback | `protocol/recovery_policy.md` |
| Sources uniques du corpus | `reference/document_map.md` §8 |
| Modèle de rapport d'audit | `templates/auditor_report_template.md` *(vague 6, créé)* |

---

## 23. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 5) — intégration C19, A2, A5, C22, C30, C31 ; points ouverts conservés |
| 0.2 | 2026-11-20 | Intégration A2, C13, C26, C27, C28, C29 ; T5 préparé, non exécuté |
| 0.3 | 2026-11-21 | Harmonisation de T4/T5 avec `permission_policy.md` ; contrôle AUDITOR/`src/**` conservé comme complément ; tests non exécutés |
