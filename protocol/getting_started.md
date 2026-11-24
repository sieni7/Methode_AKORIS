# AKORIS — Guide de démarrage

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-21 |
| Statut | **VALIDÉ PAR LE VALIDATOR — 2026-11-21** |
| Portée | Parcours complet : découverte, cadrage, profil, mandat, transition, exécution, rapport, audit, décision, changements, incidents, clôture |
| Autorité | Synthèse pédagogique orientée vers les références — **non normative** |
| Vague | 7 |

**Sources citées :** [README.md](../README.md) · [terminology.md](../reference/terminology.md) (`T`) · [document_map.md](../reference/document_map.md) (`DM`) · [governance_core.md](governance_core.md) (`GC`) · [state_model.md](state_model.md) (`SM`) · [transition_policy.md](transition_policy.md) (`TP`) · [permission_policy.md](permission_policy.md) (`PP`) · [decision_policy.md](decision_policy.md) (`DP`) · [change_control.md](change_control.md) (`CC`) · [recovery_policy.md](recovery_policy.md) (`RP`) · [audit_policy.md](audit_policy.md) (`AP`) · profils [Standard](profile_standard.md), [Lite](profile_lite.md), [Reinforced](profile_reinforced.md) · [traceability_map.md](../reference/traceability_map.md) · [versioning_policy.md](../reference/versioning_policy.md) · prompts et modèles `prompts/`, `templates/`.

---

## 0. Comment utiliser ce guide

Ce guide **oriente** : il dit quel document lire, à quel moment, et quelle décision attendre. Il ne remplace aucune politique et n'ajoute aucune règle ni aucun seuil.

| Convention | Signification |
|---|---|
| Lien Markdown | Document existant dans ce dépôt — à lire |
| Chemin en `code` (`state.json`, `current_sprint.md`, `docs/**`…) | Objet du **projet gouverné**, décrit ici mais non présent dans ce dépôt |
| `À RENSEIGNER` | Valeur à fournir par le projet ; aucun exemple n'en tient lieu |
| **Exemple** | Illustration uniquement ; aucune donnée réelle n'est représentée |
| `FAIT` / `HYPOTHÈSE` / `RECOMMANDATION` / `À ARBITRER` / `INCONNU` | Statuts épistémiques de `T` §7 (`GC-18`) |

Deux règles structurantes :

1. **Une information, un fichier.** La source unique de chaque information est recensée dans `DM` §8. Ce guide renvoie ; il ne recopie pas.
2. **Le cadre est agnostique de l'outil.** Les particularités d'OpenCode sont décrites séparément dans [implementations/opencode/README.md](../implementations/opencode/README.md). Ce chapitre n'en dépend pas.

> **Avertissement.** Ce guide n'est pas un méga prompt (`T` §1), pas une garantie de sécurité (`GC-36`), pas un état de projet (`GC-54`) et pas une décision validée. Statut des trois livrables V7 (ce guide, `reference/traceability_map.md`, `reference/versioning_policy.md`) : **VALIDÉ PAR LE VALIDATOR — 2026-11-21**. Cette validation porte uniquement sur ces trois livrables ; elle ne vaut ni validation générale du corpus ni autorisation d'exécution. Les autres documents du corpus restent soumis à leur statut propre.

> **Rôle documentaire (A5).** DOCUMENTATION BUILDER est un rôle **auxiliaire**, hors de la boucle d'exécution applicative : il rédige et maintient ce guide, il n'audite pas et il ne décide pas. Les rôles ci-dessous sont ceux du cycle d'exécution.

---

## 1. Découverte et cadrage

### 1.1 Parcours de lecture

| Ordre | Document | Ce que vous y trouvez |
|---|---|---|
| 1 | [README.md](../README.md) | Objet du cadre, organisation, état d'avancement |
| 2 | [terminology.md](../reference/terminology.md) | Vocabulaire unique ; confusions à éviter (§8) |
| 3 | [governance_core.md](governance_core.md) | Règles communes obligatoires, tous profils |
| 4 | [document_map.md](../reference/document_map.md) | Où se trouve chaque information, sources uniques |
| 5 | Le présent guide | Ordre des opérations et renvois |

### 1.2 Questions du cadrage

Le cadrage est préparé par ORCHESTRATOR et **validé par le VALIDATOR** au checkpoint **CP1** (`T` §3, `SM` §2).

| À cadrer | Où regarder | Valeur |
|---|---|---|
| Vision, problème, périmètre, exclusions | `contexte.md` (projet) | `À RENSEIGNER` |
| Exigences fonctionnelles et non fonctionnelles | `docs/requirements/` (projet) | `À RENSEIGNER` |
| Règles métier | `docs/business_rules/` (projet) | `À RENSEIGNER` |
| Critères d'acceptation | `docs/acceptance_criteria/` (projet) | `À RENSEIGNER` |
| Architecture et décisions techniques | `docs/architecture/`, `docs/adr/` (projet) | `À RENSEIGNER` |
| État courant | `state.json` (projet) | `À RENSEIGNER` |
| Chaîne exigence → décision | [traceability_map.md](../reference/traceability_map.md) | Cadre méthodologique |

**Ce que le VALIDATOR décide ici :** validation du cadrage (CP1), choix du profil, et tout arbitrage des contradictions (`GC-04`, `GC-09`). Une recommandation d'ORCHESTRATOR ne le remplace pas (`GC-05`).

> **Aucune action opérationnelle ne démarre avant la validation du checkpoint concerné** (`GC-49`). La transition est le mécanisme qui l'impose (§4).

---

## 2. Choisir le profil

Le profil fixe le **niveau de contrôle** ; il ne modifie aucun principe. Trois profils sont maintenus dans la doctrine :

| Profil | Usage | Document |
|---|---|---|
| Standard — **par défaut** | Projet logiciel réel | [profile_standard.md](profile_standard.md) |
| Lite | Prototype, faible exposition, réversibilité | [profile_lite.md](profile_lite.md) |
| Reinforced | Données sensibles, obligations, risque élevé | [profile_reinforced.md](profile_reinforced.md) |

Points à retenir, sans développer les politiques :

- Le profil est **choisi par le VALIDATOR avant CP1, enregistré puis verrouillé** (`GC-09`, `INV-11`).
- Un profil ajoute des exigences ; il ne retire jamais une règle du socle (`GC-01`, `GC-02`).
- **C25** : aucune échelle de risque chiffrée n'existe. Le choix est qualitatif et tracé ; aucun seuil n'est à inventer.
- **A3** : la disponibilité des profils dans l'implémentation de référence est déclarée séparément et n'est **pas établie**. Le pilote connu ne satisfait aucun des trois. Ce constat n'est pas une doctrine.
- Un changement de profil est un **changement majeur** : motif, analyse d'impact, décision VALIDATOR, réévaluation des contrôles (`CC` §8).

---

## 3. Mandat et checkpoints

### 3.1 Mandat

Le mandat courant est porté par `current_sprint.md` (projet) et versionné (`T` §3, `GC-30`). Il borne le périmètre : tâches, actions autorisées, critères, exclusions, version.

| Élément | Où | Statut |
|---|---|---|
| Périmètre autorisé | `current_sprint.md` | `À RENSEIGNER` |
| Version du mandat | `mandate_version` (`TP` §2) | `À RENSEIGNER` |
| Sprint concerné | `sprint_id`, `sprints/roadmap.md` | `À RENSEIGNER` |
| Forme du rapport attendu | [builder_report_template.md](../templates/builder_report_template.md) | Modèle existant |

### 3.2 Checkpoints

| Checkpoint | Objet | Décideur | Condition de passage (`SM` §2.2) |
|---|---|---|---|
| **CP1** | Cadrage | VALIDATOR | Avant toute conception |
| **CP2** | Conception et planification | VALIDATOR | Avant préparation opérationnelle |
| **CP3** | Préparation opérationnelle | VALIDATOR | Avant la première transition |

Un contrôle de préparation — la `readiness_review` — précède CP3 (`AP` §2 et §5.1, décision **C19**). Son emplacement doctrinal est `docs/governance/readiness/` (décision **C13**) ; le rapport historique du pilote est conservé sans être promu en source concurrente.

> Les tables de transitions entre états de `SM` §2.2 et §3.2 portent le statut `RECOMMANDATION` : elles ne sont pas validées. Les checkpoints, eux, sont définis dans la doctrine.

---

## 4. Transitionner

C'est le point le plus fréquemment contourné : **aucune action opérationnelle sans transition identifiée et autorisée** (`GC-45`).

### 4.1 Les cinq notions à ne pas confondre

| Notion | Acte | Acteur | Preuve |
|---|---|---|---|
| **Autorisation** | Permettre l'action | VALIDATOR | `authorized_at`, `authorized_by`, `decision_id` |
| **Consommation** | Accepter et utiliser l'autorisation | Agent destinataire | Reçu de transition |
| **Exécution** | Réaliser l'action | Agent destinataire | Commits, journaux, rapport |
| **Achèvement** | Produire le résultat | Agent destinataire | `result_report`, `completed_at` |
| **Acceptation** | Accepter le résultat | VALIDATOR | Décision (`GO`, `GO_WITH_RESERVES`, …) |

Référence complète : `TP` §3. Une autorisation non consommée n'a produit aucun effet ; une consommation non exécutée est un écart (`TP` §3).

### 4.2 Mécanisme

| Étape | Où regarder |
|---|---|
| Anatomie de la transition, 16 champs | `TP` §2 ; [state.schema.json](../reference/state.schema.json) |
| Identifiant normatif | `transition_id`, format `TR-AAAA-NNNN` — **C22** ; `token` déprécié |
| Cycle de vie | `TP` §4 ; états dans `SM` §4 |
| Contrôles avant consommation (9 points) | `TP` §5.4 |
| Reçu : contenu minimal, unicité, non-modification | `TP` §5.3 à §5.6 ; [transition_receipt_template.md](../templates/transition_receipt_template.md) |
| Destination du reçu | BUILDER → `sprint_report/` ; AUDITOR → `audit_report/` ; ORCHESTRATOR → `docs/governance/receipts/` — **C26** |
| Expiration | `TP` §7 — aucune durée numérique par défaut (**C27**) |
| Invalidation sur changement | `TP` §8, `CC` §6 — nouvelle version, nouvel identifiant, nouveau `GO` |

> **Preuve (A2).** `state.json` est la source de vérité ; le reçu est une preuve d'événement, pas une seconde vérité. Une divergence est bloquante jusqu'à réconciliation (`SM` §7). Le reçu n'est pas une preuve cryptographique (`GC-48`).

---

## 5. Exécuter

| Point | Règle et renvoi |
|---|---|
| Périmètre | BUILDER n'agit que dans le mandat autorisé (`GC-10`) ; toute extension est un changement (`CC` §1) |
| Fichiers interdits | BUILDER n'écrit ni `state.json`, ni `state.md`, ni `audit_report/`, ni une décision validée (`GC-13`) ; ORCHESTRATOR n'écrit pas `src/**` en sprint sauf autorisation explicite (`GC-11`) |
| Fusion | Aucune fusion directe vers `main` par BUILDER (`GC-14`) ; décision humaine distincte (`GC-07`) |
| Tests et preuves | Commits traçables, résultats conservés, preuves classées (`GC-23`, `DP` §5.1) ; `NOT_CHECKED` ne vaut jamais `PASS` (`GC-25`) |
| Secrets | Aucun secret dans rapport, commit ou journal ; recherche avant commit et fusion (`GC-33`, `GC-34`) |
| Prompt d'amorçage | [akoris_builder_bootstrap.md](../prompts/akoris_builder_bootstrap.md) ; [akoris_orchestrator_bootstrap.md](../prompts/akoris_orchestrator_bootstrap.md) |

**Exemple — illustratif.** Un mandat pourrait demander une tâche `À RENSEIGNER`, sous la transition `TR-2026-NNNN`, avec un commit `À RENSEIGNER` et une sortie de test `À RENSEIGNER`. Ces marqueurs ne sont pas des données réelles.

---

## 6. Rapporter et contrôler

### 6.1 Rapports

| Livrable | Rédacteur | Modèle |
|---|---|---|
| Rapport de sprint | BUILDER | [builder_report_template.md](../templates/builder_report_template.md) |
| Analyse et recommandation | ORCHESTRATOR | [orchestrator_report_template.md](../templates/orchestrator_report_template.md) |
| Rapport d'audit | AUDITOR | [auditor_report_template.md](../templates/auditor_report_template.md) |

Le rapport de BUILDER est une **source d'information**, pas la source première de vérité : l'auditeur vérifie directement (`AP` §1, `GC-22`). L'agent qui produit un résultat ne peut pas en être l'unique juge (`GC-17`).

### 6.2 Deux contrôles distincts (C19)

| | `readiness_review` | `sprint_audit` |
|---|---|---|
| Moment | **Avant** exécution, dont CP3 | **Après** exécution |
| Question | « Les conditions sont-elles réunies ? » | « Ce qui a été livré est-il conforme ? » |
| Entrée | Cadrage, contrats, permissions, Git, état central | Mandat, commits, tests, critères, reçu |
| Emplacement | `docs/governance/readiness/` (C13) | `audit_report/` |

Règles et méthode : `AP` §2, §5, §6, §8 à §11. Les désaccords sont conservés, jamais lissés. L'indépendance d'AUDITOR est **procédurale** tant qu'une isolation technique n'est pas prouvée (`GC-37`, `AP` §3). Prompt : [akoris_auditor_bootstrap.md](../prompts/akoris_auditor_bootstrap.md).

---

## 7. Décider

Seul le **VALIDATOR** décide (`GC-04`). ORCHESTRATOR et AUDITOR recommandent ; BUILDER rapporte (`DP` §1).

| Étape | Renvoi |
|---|---|
| Cinq valeurs autorisées | `GO`, `GO_WITH_RESERVES`, `NO_GO`, `HOLD`, `CANCELLED` — `DP` §3, décision **A1** |
| Qualification avant décision | Gravités S0 à S3 — `DP` §4 ; `GC-42` |
| Suffisance des preuves | `DP` §5 ; une preuve `declared_only` ne suffit pas pour un critère critique (`GC-24`) |
| Conditions cumulatives du `GO` | Neuf conditions — `DP` §6 |
| Réserves | Dix attributs obligatoires ; S0/S1 jamais couvertes — `DP` §7 |
| `HOLD` | Six motifs ; **`HOLD` n'est pas un refus** — `DP` §8.2 |
| Forme | [decision_template.md](../templates/decision_template.md), [reserve_template.md](../templates/reserve_template.md) |
| Trace | `last_decision` dans `state.json` ; registre `reference/decision_log.md` **planifié, non créé** (`DP` §11) |

> **Décisions dérivées (`DP` §9, `GC-07`).** L'acceptation n'entraîne ni fusion, ni déploiement, ni sprint suivant, ni accès à de nouvelles données, ni modification d'architecture. Chacun exige sa propre décision.

---

## 8. Gérer les changements

Un changement est un écart volontaire et tracé à ce qui était autorisé. Ce qui est interdit n'est pas de changer, mais de changer sans le dire (`CC` §0).

| Étape | Renvoi |
|---|---|
| Définir ce qui est un changement | Dix éléments — `CC` §1 |
| Identifier | `CHG-AAAA-NNNN` ou `URG-AAAA-NNNN` — `CC` §3 |
| Classer | Éditorial, mineur, majeur, critique/urgent — `CC` §2 (critères `RECOMMANDATION`) |
| Analyser l'impact | Huit dimensions ; réversibilité R0 à R3 — `CC` §5 |
| Effet sur le mandat | `CC` §6 : ancienne autorisation invalidée, nouvelle version, nouvelle transition, nouveau `GO` |
| Urgence | Confinement immédiat **sans supprimer** traçabilité ni audit a posteriori — `CC` §7 |
| Forme et emplacement | [change_request_template.md](../templates/change_request_template.md) ; `docs/governance/changes/` (projet) |

Un changement approuvé n'autorise pas l'exécution : celle-ci exige un mandat et une transition (`GC-45`).

---

## 9. Incidents et reprise

| Situation | Renvoi |
|---|---|
| Blocage — situation subie | `RP` §3 ; projet `blocked`, constat tracé, décision du VALIDATOR |
| Suspension — décision du VALIDATOR | `RP` §4 ; autorisations suspendues, non prolongées |
| Interruption d'agent | `RP` §5 ; règle de continuation `RECOMMANDATION` (§5.2) |
| État invalide | `RP` §6 ; réconcilier, jamais « réparer » en réécrivant |
| Divergence état/reçu | `SM` §7, `RP` §7 ; **bloquante** (A2) |
| Perte de preuve | `RP` §8 ; une preuve perdue ne se remplace pas par une déclaration |
| Rollback | `RP` §10 ; décision **C34** : exigence fondée sur le risque réel, le profil ne fixant qu'un plancher ; `state.json` ne se restaure jamais |
| Incident de sécurité | `RP` §11 : confiner, préserver, alerter, bloquer, qualifier, auditer, corriger, régulariser ; au minimum **S0** (`GC-35`) |
| Clôture d'incident | `RP` §12 : cause, mesures, décision, trace dans `docs/governance/incidents/` |

---

## 10. Clôture

| Niveau | Renvoi |
|---|---|
| Sprint | `audit_completed` → `accepted` / `accepted_with_reserves` / `rejected` (`SM` §3.2) ; réserves dans `debt_report/` ; **fusion puis clôture sont des actes distincts** (`SM` §3.2, `GC-07`) |
| Projet | `completed` ou `cancelled`, états terminaux non réactivables (`SM` §2.2) |
| Bilan | Décision du VALIDATOR sur la clôture ; risques résiduels acceptés explicitement (`DP` §2 et §9) |
| Traçabilité | Reçus, transitions, preuves, décisions et incidents conservés (`TP` §10, `RP` §12) |
| Durée de conservation | `INCONNU` — non définie dans les sources (`TP` §10) |

---

## 11. Récapitulatif des décisions du VALIDATOR

Aucune décision listée ici ne peut être déléguée à un agent ni déduite d'une autre (`GC-04`, `GC-05`, `GC-07`).

| Décision | Moment | Référence |
|---|---|---|
| Choix et verrouillage du profil | Avant CP1 | `GC-09`, `CC` §8 |
| Validation CP1, CP2, CP3 | Fin de phase | `SM` §2.2, `AP` §5.1 |
| Autorisation de chaque transition | Avant consommation | `TP` §2, §4 |
| Acceptation, réserve, refus, `HOLD` ou annulation | Après audit | `DP` §3 |
| Changement, urgence, changement de profil | Selon le cas | `CC` §2, §7, §8 |
| Levée de blocage, suspension, reprise, clôture d'incident | Selon le cas | `RP` §3, §4, §9, §12 |
| Fusion vers `main`, déploiement, sprint suivant, nouvel accès, architecture | Actes distincts | `DP` §9 |
| Clôture de projet | Fin de vie | `DP` §2 |

---

## 12. Exemple de parcours — illustratif, non réel

> **Exemple.** Tous les marqueurs ci-dessous sont `À RENSEIGNER` ; aucun ne correspond à un projet réel.

```text
Cadrage       → contexte.md et docs/requirements/ : À RENSEIGNER
Profil        → choisi et verrouillé par le VALIDATOR : À RENSEIGNER
Checkpoint    → CP1 validé : À RENSEIGNER (date, décision)
Mandat        → current_sprint.md, mandate_version : À RENSEIGNER
Transition    → TR-2026-NNNN, autorisée par le VALIDATOR : À RENSEIGNER
Consommation  → reçu déposé par le destinataire : À RENSEIGNER
Contrôle      → readiness_review puis sprint_audit : statuts PASS / NOT_CHECKED à renseigner
Preuve        → classe selon DP §5.1 : À RENSEIGNER
Décision      → GO / GO_WITH_RESERVES / NO_GO / HOLD / CANCELLED : À RENSEIGNER
Suite         → fusion : décision distincte, À RENSEIGNER
```

Cet enchaînement ne fixe aucun délai, aucun seuil et aucune valeur : il montre seulement l'ordre des références à consulter.

---

## 13. Travail avec l'implémentation OpenCode

Le protocole reste **agnostique de l'outil**. Pour une configuration concrète, consulter :

| Sujet | Document |
|---|---|
| Vue d'ensemble et frontière | [implementations/opencode/README.md](../implementations/opencode/README.md) |
| Relevé des règles observées | [implementations/opencode/agent_permissions.md](../implementations/opencode/agent_permissions.md) |
| Limites constatées | [implementations/opencode/limitations.md](../implementations/opencode/limitations.md) |
| Prérequis de reproduction | [implementations/opencode/environment_requirements.md](../implementations/opencode/environment_requirements.md) |
| Forme du frontmatter observé | [implementations/opencode/frontmatter_reference.md](../implementations/opencode/frontmatter_reference.md) |

**État déclaré dans le constat disponible :** T1 à T5 sont `NON EXÉCUTÉS`, les permissions restent `unknown`, la protection de `main` reste `unknown`. Aucune permission n'est certifiée `technical_enforced` ; l'indépendance d'AUDITOR est procédurale. T4 porte sur une tentative de fusion ou de push non autorisé vers une branche protégée autre que `main`, en dépôt de test ; T5 vise `main`. Le contrôle AUDITOR/`src/**` reste complémentaire, hors T1–T5 (`PP` §7.2, `AP` §12.1).

Ce guide n'exécute aucun test et ne met à jour aucun statut de permission.

---

## 14. Limites et points ouverts

| Objet | Statut |
|---|---|
| Tables de transitions projet/sprint | `RECOMMANDATION` — `SM` §2.2 et §3.2 |
| Procédure de reprise après interruption | `RECOMMANDATION` — `RP` §5.2 |
| Échelle de risque chiffrée (C25) | `INCONNU` — choix qualitatif |
| Seuils de classement des changements, RTO/RPO, durée de conservation | `INCONNU` — `CC` §12, `RP` §14, `TP` §10 |
| Registres projet (`docs/governance/…`, `reference/decision_log.md`) | Non créés / planifiés — `DP` §11, `CC` §12, `RP` §14 |
| Numérotation des versions, règles major/minor/patch, migration | `À ARBITRER` — [versioning_policy.md](../reference/versioning_policy.md) §5 |
| Catégories de versions | Divergence `A7` / `00_cartographie.md` / F2 §16 signalée, non tranchée — `versioning_policy.md` §4 |
| Schéma de validation de `state.json` | Divergence interne de `SM` signalée (§6/§6.1 vs §10), non tranchée |
| Tests T1 à T5, permissions, protection de `main` | `NON EXÉCUTÉS` / `unknown` / `unknown` — aucun test réalisé |

Les contradictions se signalent au VALIDATOR ; elles ne se corrigent pas unilatéralement (`GC-31`).

---

## 15. Renvois rapides

| Besoin | Document |
|---|---|
| Vocabulaire | [terminology.md](../reference/terminology.md) |
| Règles communes | [governance_core.md](governance_core.md) |
| Niveau d'exigence | profils [Standard](profile_standard.md), [Lite](profile_lite.md), [Reinforced](profile_reinforced.md) |
| États et invariants | [state_model.md](state_model.md) |
| Transitions et reçus | [transition_policy.md](transition_policy.md) |
| Permissions | [permission_policy.md](permission_policy.md) |
| Décisions | [decision_policy.md](decision_policy.md) |
| Changements | [change_control.md](change_control.md) |
| Reprise et incidents | [recovery_policy.md](recovery_policy.md) |
| Audit | [audit_policy.md](audit_policy.md) |
| Traçabilité | [traceability_map.md](../reference/traceability_map.md) |
| Versions | [versioning_policy.md](../reference/versioning_policy.md) |
| Sources uniques | [document_map.md](../reference/document_map.md) §8 |
| Amorçage des rôles | [prompts/akoris_orchestrator_bootstrap.md](../prompts/akoris_orchestrator_bootstrap.md), [prompts/akoris_builder_bootstrap.md](../prompts/akoris_builder_bootstrap.md), [prompts/akoris_auditor_bootstrap.md](../prompts/akoris_auditor_bootstrap.md), [prompts/akoris_documentation_builder.md](../prompts/akoris_documentation_builder.md) |
| Forme des livrables | `templates/` — sept modèles existants |

---

## 16. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-21 | Version initiale (vague 7) — parcours complet orienté références, décisions du VALIDATOR, exemples marqués, statuts préservés |

> **Note de statut (2026-11-21).** Statut aligné sur **VALIDÉ PAR LE VALIDATOR — 2026-11-21** ; validation limitée aux trois livrables V7. Aucune règle, preuve d'exécution, permission ni donnée d'état n'a été modifiée.
