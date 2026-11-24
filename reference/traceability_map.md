# Carte de traçabilité AKORIS

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-21 |
| Statut | **VALIDÉ PAR LE VALIDATOR — 2026-11-21** |
| Portée | Chaîne exigence → tâche/action → test/contrôle → preuve → décision |
| Autorité | Index de traçabilité — renvois aux sources uniques |
| Vague | 7 |

**Sources citées :** `T` = [terminology.md](terminology.md) · `DM` = [document_map.md](document_map.md) · `GC` = [governance_core.md](../protocol/governance_core.md) · `SM` = [state_model.md](../protocol/state_model.md) · `TP` = [transition_policy.md](../protocol/transition_policy.md) · `PP` = [permission_policy.md](../protocol/permission_policy.md) · `DP` = [decision_policy.md](../protocol/decision_policy.md) · `CC` = [change_control.md](../protocol/change_control.md) · `RP` = [recovery_policy.md](../protocol/recovery_policy.md) · `AP` = [audit_policy.md](../protocol/audit_policy.md) · décisions VALIDATOR **A2**, **A7**, **C19**, **C22**, **C26**, **C28**.

---

## 0. Nature de ce document

Cette carte **relie** des objets ; elle ne définit aucune règle, n'enregistre aucun résultat de test et ne prend aucune décision.

- Les règles restent dans `protocol/` ; la source unique de chaque information est recensée dans `DM` §8.
- Un lien Markdown désigne un fichier **existant dans ce dépôt**. Un chemin en `code` désigne un objet du **projet gouverné**, décrit par le protocole mais absent de ce dépôt : c'est une référence générique, pas une preuve.
- Les statuts `FAIT`, `HYPOTHÈSE`, `RECOMMANDATION`, `À ARBITRER`, `INCONNU` sont ceux de `T` §7 (`GC-18`).
- Un exemple est signalé comme exemple ; une valeur à renseigner est signalée comme telle (`GC-53`). Aucune donnée de projet fictive n'est présentée comme réelle.

---

## 1. Objet

La chaîne à rendre lisible est la suivante. Elle est un **cadre de lecture**, pas un ordre d'exécution imposé par ce document :

```text
Exigence → Tâche / action → Test / contrôle → Preuve → Décision
```

Chaque maillon possède sa source unique. Cette carte indique **où regarder**, jamais **ce qu'il faut conclure**.

---

## 2. Deux niveaux de traçabilité à ne pas confondre

| Niveau | Ce qu'il contient | Où il vit | Statut dans ce dépôt |
|---|---|---|---|
| **Référentiel générique du cadre** | Règles, définitions, identifiants, formats de livrables, chemins normatifs | [terminology.md](terminology.md), `protocol/`, [document_map.md](document_map.md), `templates/` | `FAIT` — documents présents et liés |
| **Données propres à un projet** | Exigences réelles, mandat courant, transition active, résultats, reçus, décisions humaines | `docs/**`, `current_sprint.md`, `state.json`, `sprint_report/`, `audit_report/`, `docs/governance/**` du **projet gouverné** | Hors périmètre : chemins de référence, **aucune valeur renseignée ici** |

> **Règle de lecture (A2).** `state.json` du projet est la source de vérité de l'état courant ; les reçus sont des preuves d'événements ; une divergence entre les deux est bloquante jusqu'à réconciliation (`SM` §7). Cette carte ne contient aucun `state.json`.

> **Règle de séparation (GC-54).** Les règles du cadre ne sont jamais mélangées à l'état d'un projet particulier. Un exemple de la chaîne ne devient pas un cas réel.

---

## 3. Les cinq maillons

### 3.1 Exigence

| Information | Source unique | Nature |
|---|---|---|
| Vocabulaire de l'exigence | [terminology.md](terminology.md) | Normatif terminologique |
| Emplacements des exigences du projet | `docs/requirements/`, `docs/business_rules/`, `docs/acceptance_criteria/`, `contexte.md` — référencés dans `DM` §6 | Chemins du projet gouverné |
| Périmètre et contraintes | `contexte.md` (projet) | À renseigner par le projet |
| Critères vérifiables | `docs/acceptance_criteria/` (projet) | À renseigner par le projet |

L'exigence n'est pas définie par cette carte. Un format d'identifiant d'exigence n'est pas fixé dans les sources consultées : `À ARBITRER` si une correspondance stable doit être normalisée.

### 3.2 Tâche / action

| Information | Source unique | Nature |
|---|---|---|
| Mandat courant | `current_sprint.md` (projet) — `T` §3 | Périmètre autorisé |
| Version du mandat | `mandate_version` dans la transition — `TP` §2, `SM` §8 | Identifiant à renseigner |
| Règle d'action | [governance_core.md](../protocol/governance_core.md) §3 et §9 (`GC-10`, `GC-45`) | Normatif |
| Identifiant de passage | `transition_id`, format `TR-AAAA-NNNN` — `T` §9, décision **C22** ; `token` déprécié | Normatif |
| Cycle de la transition | [transition_policy.md](../protocol/transition_policy.md) §4 ; états dans [state_model.md](../protocol/state_model.md) §4 | Normatif |

Une action opérationnelle sans transition identifiée et autorisée est interdite (`GC-45`). Les tables de transitions de `SM` §2.2 et §3.2 portent le statut `RECOMMANDATION` : elles ne sont pas une décision validée.

### 3.3 Test / contrôle

| Information | Source unique | Nature |
|---|---|---|
| Contrôle avant exécution | `readiness_review`, dont CP3 — [audit_policy.md](../protocol/audit_policy.md) §2 et §5.1 ; emplacement doctrinal `docs/governance/readiness/` (C13) | Normatif |
| Contrôle après exécution | `sprint_audit` — [audit_policy.md](../protocol/audit_policy.md) §2, §5.2 et §6 ; emplacement `audit_report/` | Normatif |
| Statuts de contrôle | `PASS`, `FAIL`, `PARTIAL`, `N/A`, `NOT_CHECKED` — [decision_policy.md](../protocol/decision_policy.md) §5.2 ; `NOT_CHECKED` ne vaut jamais `PASS` (`GC-25`) | Normatif |
| Vérification des permissions | Tests T1 à T5 — [permission_policy.md](../protocol/permission_policy.md) §7.2 | **NON EXÉCUTÉS** |
| Indépendance de l'audit | Procédurale par défaut — `GC-37`, [audit_policy.md](../protocol/audit_policy.md) §3 et §12 | `FAIT` — non certifiée techniquement |

Les deux contrôles `readiness_review` et `sprint_audit` sont distincts et non substituables (décision **C19**) : le premier juge une aptitude à démarrer, le second un résultat livré. Le contrôle complémentaire consistant à demander à AUDITOR d'éditer `src/**` n'est ni T4 ni un nouveau test T1–T5 ; il ne reçoit aucun identifiant supplémentaire (`PP` §7.2).

T4 porte sur une tentative de fusion ou de push non autorisé vers une branche protégée **autre que `main`**, dans un dépôt de test ; T5 vise `main` et reste distinct. Aucun des deux n'a été exécuté.

### 3.4 Preuve

| Information | Source unique | Nature |
|---|---|---|
| Statuts de preuve | `directly_verified`, `reproduced`, `cross_checked`, `declared_only`, `partial`, `missing`, `invalid` — [decision_policy.md](../protocol/decision_policy.md) §5.1 | Normatif |
| Exigences sur les preuves | `GC-22` à `GC-28` — [governance_core.md](../protocol/governance_core.md) §5 | Normatif |
| Preuve de consommation | Reçu de transition — [transition_policy.md](../protocol/transition_policy.md) §5 ; contenu minimal §5.3 ; modèle [transition_receipt_template.md](../templates/transition_receipt_template.md) | Normatif |
| Destination des reçus | BUILDER → `sprint_report/` ; AUDITOR → `audit_report/` ; ORCHESTRATOR → `docs/governance/receipts/` — décision **C26**, `TP` §5.2 et §5.7 | Normatif |
| Forme des rapports | [builder_report_template.md](../templates/builder_report_template.md), [auditor_report_template.md](../templates/auditor_report_template.md), [orchestrator_report_template.md](../templates/orchestrator_report_template.md) | Formel |
| Constat de configuration réelle | [agent_permissions.md](../implementations/opencode/agent_permissions.md) | `CONSTAT` — non normatif, effectivité non démontrée |

Une preuve `declared_only` ne suffit pas à valider un critère critique (`GC-24`). Un rapport raconte ; une preuve démontre (`T` §8). Le reçu prouve la réception, pas l'exécution, ni la qualité (`TP` §5.6).

Les données de preuve proprement dites — commit, sortie de commande, journal CI, capture — appartiennent au projet gouverné et sont **à renseigner** à l'occasion du contrôle. Elles ne figurent pas ici.

### 3.5 Décision

| Information | Source unique | Nature |
|---|---|---|
| Valeurs de décision | `GO`, `GO_WITH_RESERVES`, `NO_GO`, `HOLD`, `CANCELLED` — [decision_policy.md](../protocol/decision_policy.md) §3, décision **A1** | Normatif |
| Auteur | VALIDATOR uniquement — `GC-04`, `DP` §1 | `FAIT` |
| Qualification avant décision | Gravités S0 à S3 — [decision_policy.md](../protocol/decision_policy.md) §4 | Normatif |
| Contenu minimal d'une décision | Identifiant, type, valeur, auteur, date, motif, preuves, réserves, effet — `DP` §11 | Normatif |
| Forme | [decision_template.md](../templates/decision_template.md), [reserve_template.md](../templates/reserve_template.md) | Formel |
| État résultant | `last_decision` dans `state.json` — `SM` §1 et §6.4 | Donnée de projet |
| Registre des décisions | `reference/decision_log.md` — **fichier planifié, non créé** (`DP` §11 et §12) | `À ARBITRER` |

Une recommandation d'ORCHESTRATOR ou d'AUDITOR n'est pas une décision (`GC-05`, `GC-21`). Aucune décision n'en implique une autre par défaut : l'acceptation d'un sprint n'autorise ni la fusion, ni le déploiement, ni le sprint suivant (`GC-07`, `DP` §9).

---

## 4. Identifiants qui jalonnent la chaîne

Le format et la source de chaque préfixe sont définis dans [terminology.md](terminology.md) §9. Ils sont rappelés ici **à titre de repères de navigation**, sans redéfinition.

| Identifiant | Maillon | Rôle | Source |
|---|---|---|---|
| `TR-AAAA-NNNN` | Tâche / action | Transition, autorisation d'agir | `T` §9 — **C22** |
| `CHG-AAAA-NNNN` | Décision / changement | Changement planifié | `T` §9, `CC` §3 |
| `URG-AAAA-NNNN` | Décision / changement | Urgence régularisée | `T` §9, `CC` §3 |
| `CP1`, `CP2`, `CP3` | Contrôle | Checkpoints de cadrage, conception, préparation | `T` §9, `SM` §2 |
| `S0` → `S3` | Contrôle / décision | Gravité d'anomalie | `T` §9, `DP` §4 |
| `P0` → `P3` | Contrôle / décision | Gravité de violation de permission | `T` §9, `PP` §6 |
| `R0` → `R3` | Décision / changement | Réversibilité | `T` §9, `CC` §5.1 |

Un identifiant consommé, expiré ou annulé n'est jamais réutilisé (`GC-32`) ; il reste dans l'historique.

---

## 5. Relations structurantes à respecter

Ces relations sont des règles existantes, **non pas des règles nouvelles**. Elles sont rappelées parce qu'elles conditionnent la validité de la chaîne.

| Relation | Autorité | Effet sur la chaîne |
|---|---|---|
| `state.json` source de vérité ; reçus = preuves ; divergence bloquante | **A2**, `SM` §0 et §7 | Aucune poursuite avant réconciliation ; aucun « choix » de la source favorable |
| Au plus un reçu par `transition_id` | `INV-04`, `TP` §5.5 | Deux reçus = divergence bloquante |
| Aucun sprint `in_progress` sans transition `consumed` | `INV-06` | La preuve de consommation précède l'exécution |
| Aucun sprint `accepted` sans `audit_completed` | `INV-07` | Le contrôle précède la décision d'acceptation |
| `NOT_CHECKED` ≠ `PASS` | `GC-25`, `DP` §5.2 | Un contrôle non réalisé n'est pas un succès |
| Acceptation ≠ fusion | `GC-07`, `DP` §9 | Décision humaine distincte |
| Divergence documentaire signalée, jamais corrigée silencieusement | `GC-31` | Une anomalie S1 si un document devenu faux n'est pas corrigé (`CC` §9) |
| Respect du mandat et de sa version | `INV-10`, `TP` §8, `CC` §6 | Changement de version ⇒ nouvelle transition et nouveau `GO` |

---

## 6. Ce que cette carte ne contient pas

- aucune exigence, tâche, critère ou valeur de projet ;
- aucun résultat de test, aucun statut de contrôle réel, aucune capture ni journal ;
- aucune preuve ni aucun reçu ;
- aucune décision du VALIDATOR, aucune recommandation chiffrée ;
- aucune règle de gouvernance : les règles sont dans `protocol/` ;
- aucun état courant : l'état d'un projet vit dans son `state.json`, jamais ici (`README` §10).

**Exemple — illustratif, non réel.** Un projet fictif pourrait relier une exigence `À RENSEIGNER` à une tâche `À RENSEIGNER`, sous une transition `TR-2026-NNNN`, avec un contrôle `PASS` ou `NOT_CHECKED`, une preuve classée selon `DP` §5.1, puis une décision `GO` ou `HOLD`. Ces marqueurs ne sont ni des données, ni des résultats, ni des décisions.

---

## 7. Champs et relations restant à arbitrer

| Objet | Constat | Statut |
|---|---|---|
| Format d'identifiant des exigences et des tâches | Aucun format normatif dans les sources ; les identifiants `TR-`, `CHG-`, `URG-` existent, pas ceux d'exigence ou de tâche | `À ARBITRER` — décision humaine si une normalisation est souhaitée |
| Registre des décisions | `reference/decision_log.md` annoncé, non créé (`DP` §11) | `À ARBITRER` — le registre reste partiel |
| Correspondance fine entre un reçu et la preuve d'exécution | Le reçu prouve la réception ; le rapport et les commits prouvent l'exécution (`TP` §5.6) | `FAIT` — relation décrite, aucun mécanisme technique supplémentaire défini |
| Durée de conservation des preuves et des reçus | Non définie (`TP` §10) | `INCONNU` |
| Registres du projet gouverné (`docs/governance/changes/`, `incidents/`, `readiness/`, `receipts/`) | Décrits dans `DM` §6 ; non créés dans le pilote (`CC` §12, `RP` §14) | `INCONNU` — création du ressort de la configuration du projet |
| Divergence interne de `state_model.md` | §10 : « aucun schéma de validation n'existe » ; §6.1/§6.3 et décision **C28** : `state.schema.json` existe | Divergence **signalée, non tranchée** — aucune correction unilatérale |
| Correspondance entre version du protocole et version du schéma | Distinctes (`SM` §6.4, décision **A7**) ; modalités non définies | Voir [versioning_policy.md](versioning_policy.md) §5 |

---

## 8. Renvois

| Sujet | Document |
|---|---|
| Sources uniques par information | [document_map.md](document_map.md) §8 |
| Vocabulaire et identifiants | [terminology.md](terminology.md) §3, §4, §9 |
| Statuts épistémiques | [terminology.md](terminology.md) §7 |
| Règles communes | [governance_core.md](../protocol/governance_core.md) |
| Versions | [versioning_policy.md](versioning_policy.md) |
| Parcours de lecture | [getting_started.md](../protocol/getting_started.md) |
| Constat OpenCode | [agent_permissions.md](../implementations/opencode/agent_permissions.md) |

---

## 9. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-21 | Version initiale (vague 7) — cartographie de la chaîne, sélection des deux niveaux de traçabilité, points à arbitrer |

> **Note de statut (2026-11-21).** Statut aligné sur **VALIDÉ PAR LE VALIDATOR — 2026-11-21** ; validation limitée aux trois livrables V7. Aucune règle, preuve d'exécution, permission ni donnée d'état n'a été modifiée.
