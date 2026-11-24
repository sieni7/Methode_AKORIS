# AKORIS — Carte documentaire

| Champ | Valeur |
|---|---|
| Version | 0.4 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | Inventaire, rôles, autorité, dépendances et statut de chaque document |
| Autorité | Index du corpus documentaire |
| Vague | 1 |

**Sources citées :** `F3` = `AKORIS_consolide.md` · `F2` = `AKORIS_architecture_documentaire.md` · `F1` = `akoris_documentation_builder.md` · `CART` = `00_cartographie.md`.

---

## 1. Objet

Cette carte répond à quatre questions, et à elles seules :

1. **Quels documents existent**, et lesquels sont encore à produire ?
2. **À quoi sert chacun**, et sur quoi fait-il autorité ?
3. **De quoi dépend chacun**, et qui le référence ?
4. **Où se trouve la source unique** d'une information donnée ?

Elle ne contient **aucune règle du protocole**. Les règles sont dans `protocol/`.

---

## 2. Règles de lecture

| Convention | Signification |
|---|---|
| Lien Markdown | Le fichier **existe**. Un lien cassé est un défaut à corriger. |
| Chemin en `code` | Le fichier est **planifié** mais n'existe pas encore. Ce n'est pas un lien. |
| `SOURCE` | Document d'entrée, non produit par le DOCUMENTATION BUILDER. |
| `TRAVAIL` | Document de travail, non normatif. |
| `EXISTANT` | Produit et présent dans le dossier. |
| `PLANIFIÉ (vN)` | À produire en vague N. |

> **Règle de maintenance :** un fichier créé devient un lien. Un fichier supprimé redevient un chemin en `code`. Cette règle évite les liens morts et empêche de confondre l'existant avec le prévu.

**État du corpus au 2026-11-21 :** 34 documents produits sur 34 (dont 4 prompts et 7 modèles de la vague 6, 4 documents OpenCode intégrés et 3 documents de la vague 7), plus la cartographie et le schéma technique `reference/state.schema.json` (hors décompte des documents). Le corpus est en attente de validation du VALIDATOR.

---

## 3. Vue d'ensemble

```text
documentation/
├── README.md                      [x] vague 1 — point d'entrée
├── 00_cartographie.md             [x] vague 0 — TRAVAIL
├── changelog.md                   [x] vague 1 — journal du cadre
│
├── _sources/
│   ├── AKORIS_consolide.md        [x] source F3 — Niveau 2
│   ├── AKORIS_architecture_documentaire.md [x] source F2 — Niveau 3
│   └── akoris_documentation_builder.md [x] source F1 — Niveau 4
│
├── protocol/
│   ├── governance_core.md         [x] vague 1 — socle
│   ├── profile_standard.md        [x] vague 2 — profil par défaut
│   ├── profile_lite.md            [x] vague 2
│   ├── profile_reinforced.md      [x] vague 2
│   ├── state_model.md             [x] vague 3
│   ├── transition_policy.md       [x] vague 3 — reçus
│   ├── permission_policy.md       [x] vague 3
│   ├── decision_policy.md         [x] vague 4
│   ├── change_control.md          [x] vague 4
│   ├── recovery_policy.md         [x] vague 4
│   ├── audit_policy.md            [x] vague 5
│   └── getting_started.md         [x] vague 7 — manuel
│
├── implementations/
│   └── opencode/
│       ├── agent_permissions.md   [x] vague 3 — constat
│       ├── README.md              [x] intégration — présentation
│       ├── frontmatter_reference.md [x] intégration — référence
│       ├── environment_requirements.md [x] intégration — prérequis
│       └── limitations.md         [x] intégration — limites
│
├── prompts/
│   ├── akoris_orchestrator_bootstrap.md [x] vague 6
│   ├── akoris_builder_bootstrap.md      [x] vague 6
│   ├── akoris_auditor_bootstrap.md      [x] vague 6
│   └── akoris_documentation_builder.md  [x] vague 6
│
├── templates/
│   ├── orchestrator_report_template.md  [x] vague 6
│   ├── builder_report_template.md       [x] vague 6
│   ├── auditor_report_template.md       [x] vague 6
│   ├── decision_template.md             [x] vague 6
│   ├── change_request_template.md       [x] vague 6
│   ├── reserve_template.md              [x] vague 6
│   └── transition_receipt_template.md   [x] vague 6
│
└── reference/
    ├── terminology.md             [x] vague 1 — vocabulaire
    ├── document_map.md            [x] vague 1 — ce document
    ├── state.schema.json          [x] maintenance — schéma v2.0
    ├── traceability_map.md        [x] vague 7 — traçabilité
    └── versioning_policy.md       [x] vague 7 (A7)
```

---

## 4. Fiches détaillées

### 4.1 Racine

| Fichier | Rôle | Autorité de contenu | Dépend de | Vague | Statut |
|---|---|---|---|---|---|
| `README.md` | Point d'entrée : objet, organisation, parcours de lecture, état d'avancement | Présentation | terminology, document_map | 1 | EXISTANT |
| `00_cartographie.md` | Analyse de l'existant : inventaire, doublons, contradictions, arbitrages | Diagnostic | sources | 0 | TRAVAIL |
| `changelog.md` | Journal du cadre : version, date, nature, documents affectés | Historique | A7 | 1 puis 7 | EXISTANT |

### 4.2 `protocol/` — normes

| Fichier | Rôle | Autorité de contenu | Dépend de | Vague | Statut |
|---|---|---|---|---|---|
| `governance_core.md` | Socle obligatoire, 54 règles communes | Normatif, tous profils | terminology | 1 | EXISTANT |
| `profile_standard.md` | Profil par défaut : checkpoints, rôles complets, audit par sprint | Niveau d'exigence | governance_core | 2 | EXISTANT |
| `profile_lite.md` | Faible risque : exigences minimales, audit ciblé | Niveau d'exigence | profile_standard | 2 | EXISTANT |
| `profile_reinforced.md` | Risque élevé : sécurité, preuves reproductibles, rollback | Niveau d'exigence | profile_standard | 2 | EXISTANT |
| `state_model.md` | États projet/sprint/transition, invariants, structure d'état | Normatif | governance_core | 3 | EXISTANT |
| `transition_policy.md` | Transitions, reçus, consommation, expiration, invalidation | Normatif | state_model | 3 | EXISTANT |
| `permission_policy.md` | Trois niveaux de permission, matrice, vérification effective | Normatif | state_model | 3 | EXISTANT |
| `decision_policy.md` | Valeurs de décision, gravités, preuves, réserves | Normatif | governance_core | 4 | EXISTANT |
| `change_control.md` | Changements, classification, impact, effet sur le mandat | Normatif | decision_policy | 4 | EXISTANT |
| `recovery_policy.md` | Blocage, suspension, reprise, rollback, incident | Normatif | state_model | 4 | EXISTANT |
| `audit_policy.md` | Méthode d'audit, `readiness_review`, `sprint_audit`, limites, désaccords | Normatif | decision_policy, permission_policy | 5 | EXISTANT |
| [getting_started.md](../protocol/getting_started.md) | Manuel complet, pédagogique, orienté références | Synthèse | tout | 7 | EXISTANT |

### 4.3 `implementations/opencode/` — implémentation de référence

Périmètre : **configuration et limites d'un environnement donné**. Aucune règle de gouvernance n'y est créée ; elles sont appliquées ou non.

| Fichier | Rôle | Autorité de contenu | Dépend de | Vague | Statut |
|---|---|---|---|---|---|
| `agent_permissions.md` | Matrice des permissions **effectivement** configurées, avec preuves | Constat technique | permission_policy | 3 | EXISTANT |
| [frontmatter_reference.md](../implementations/opencode/frontmatter_reference.md) | Schéma `permissions` d'OpenCode, sémantique des règles | Référence outil | doc OpenCode V2 | maintenance | EXISTANT |
| [environment_requirements.md](../implementations/opencode/environment_requirements.md) | Hypothèses d'environnement et prérequis | Descriptif | A8 | maintenance | EXISTANT |
| [limitations.md](../implementations/opencode/limitations.md) | Ce que l'environnement ne garantit pas | Descriptif | agent_permissions | maintenance | EXISTANT |
| [README.md](../implementations/opencode/README.md) (implémentation) | Comment AKORIS est implémenté dans OpenCode | Descriptif | A8 | maintenance | EXISTANT |

### 4.4 `prompts/` — amorçage des rôles

| Fichier | Rôle | Autorité | Dépend de | Vague | Statut |
|---|---|---|---|---|---|
| [akoris_orchestrator_bootstrap.md](../prompts/akoris_orchestrator_bootstrap.md) | Démarrer ORCHESTRATOR : identité, documents à lire, interdictions, première question | Opératoire | governance_core, profils, state_model | 6 | EXISTANT |
| [akoris_builder_bootstrap.md](../prompts/akoris_builder_bootstrap.md) | Démarrer BUILDER : vérification du GO, périmètre, tests, rapport | Opératoire | governance_core, permission_policy | 6 | EXISTANT |
| [akoris_auditor_bootstrap.md](../prompts/akoris_auditor_bootstrap.md) | Démarrer AUDITOR : inspection directe, preuves, rapport | Opératoire | audit_policy | 6 | EXISTANT |
| [akoris_documentation_builder.md](../prompts/akoris_documentation_builder.md) | Démarrer le rôle documentaire | Opératoire | document_map | 6 | EXISTANT |

### 4.5 `templates/` — modèles

| Fichier | Rôle | Dépend de | Vague | Statut |
|---|---|---|---|---|
| [orchestrator_report_template.md](../templates/orchestrator_report_template.md) | Rapport d'analyse et de recommandation | decision_policy, change_control | 6 | EXISTANT |
| [builder_report_template.md](../templates/builder_report_template.md) | Rapport de sprint | decision_policy, audit_policy | 6 | EXISTANT |
| [auditor_report_template.md](../templates/auditor_report_template.md) | Rapport d'audit | audit_policy | 6 | EXISTANT |
| [decision_template.md](../templates/decision_template.md) | Décision du VALIDATOR | decision_policy | 6 | EXISTANT |
| [change_request_template.md](../templates/change_request_template.md) | Fiche de changement | change_control | 6 | EXISTANT |
| [reserve_template.md](../templates/reserve_template.md) | Réserve et plan de résolution | decision_policy | 6 | EXISTANT |
| [transition_receipt_template.md](../templates/transition_receipt_template.md) | Reçu de transition | transition_policy | 6 | EXISTANT |

### 4.6 `reference/` — navigation et référentiels

| Fichier | Rôle | Autorité | Dépend de | Vague | Statut |
|---|---|---|---|---|---|
| `terminology.md` | Vocabulaire unique du cadre | Normatif terminologique | — | 1 | EXISTANT |
| `document_map.md` | Cette carte | Index | terminology | 1 | EXISTANT |
| [traceability_map.md](traceability_map.md) | Chaîne information → décision → preuve | Traçabilité | tout | 7 | EXISTANT |
| [versioning_policy.md](versioning_policy.md) | Ce qui est versionné, comment, et par qui | Normatif | A7 | 7 | EXISTANT |
| `state.schema.json` | Schéma technique de `state.json` pour AKORIS v2.0 | Technique | state_model, décision **A2** | maintenance | EXISTANT |

### 4.7 Identifiants de documents — table centrale (A12)

Cette table recense les sigles de documents utilisés dans les renvois. Elle n'est pas un glossaire métier et ne remplace pas les définitions locales des lignes « Sources citées ».

| Sigle | Titre | Chemin vérifié |
|---|---|---|
| `T` | Terminologie AKORIS | [terminology.md](terminology.md) |
| `DM` | AKORIS — Carte documentaire | [document_map.md](document_map.md) |
| `GC` | AKORIS — Socle de gouvernance | [governance_core.md](../protocol/governance_core.md) |
| `SM` | Modèle d'état | [state_model.md](../protocol/state_model.md) |
| `TP` | Politique des transitions | [transition_policy.md](../protocol/transition_policy.md) |
| `PP` | Politique des permissions | [permission_policy.md](../protocol/permission_policy.md) |
| `DP` | Politique de décision | [decision_policy.md](../protocol/decision_policy.md) |
| `CC` | Contrôle des changements | [change_control.md](../protocol/change_control.md) |
| `RP` | Politique de reprise et d'incident | [recovery_policy.md](../protocol/recovery_policy.md) |
| `AP` | Audit Policy | [audit_policy.md](../protocol/audit_policy.md) |
| `CART` | AKORIS — Cartographie documentaire | [00_cartographie.md](../00_cartographie.md) |
| `CHL` | Changelog — cadre documentaire AKORIS | [changelog.md](../changelog.md) |
| `F1` | Prompt — AKORIS Documentation Builder | [akoris_documentation_builder.md](../_sources/akoris_documentation_builder.md) |
| `F2` | AKORIS — Architecture documentaire et organisation recommandées | [AKORIS_architecture_documentaire.md](../_sources/AKORIS_architecture_documentaire.md) |
| `F3` | AKORIS | [AKORIS_consolide.md](../_sources/AKORIS_consolide.md) |

### 4.8 Rôles de lecture par parcours (A17)

Les rôles ci-dessous décrivent l'usage pédagogique vérifié dans `README.md` §3 et le contenu des fiches du présent document. Ils n'établissent aucun classement d'importance universel et ne modifient pas l'autorité normative des documents.

| Document | Parcours | Rôle de lecture | Autorité de contenu (distincte du rôle) |
|---|---|---|---|
| `README.md` | Découvrir | Point d'entrée du parcours | Présentation |
| [terminology.md](terminology.md) | Découvrir | Vocabulaire et confusions à éviter | Normatif terminologique |
| [governance_core.md](../protocol/governance_core.md) | Découvrir, Appliquer | Socle commun, règles obligatoires | Normatif, tous profils |
| [document_map.md](document_map.md) | Découvrir, Maintenir | Repérage et dépendances | Index du corpus |
| [getting_started.md](../protocol/getting_started.md) | Découvrir | Ordre des opérations et renvois | Synthèse — livrable V7 validé |
| [profile_standard.md](../protocol/profile_standard.md) | Appliquer | Profil par défaut | Niveau d'exigence |
| [state_model.md](../protocol/state_model.md) | Appliquer | États et structure d'état | Normatif |
| [transition_policy.md](../protocol/transition_policy.md) | Appliquer | Transitions et reçus | Normatif |
| [permission_policy.md](../protocol/permission_policy.md) | Appliquer | Permissions et vérification | Normatif |
| Amorçage du rôle (§4.4) | Appliquer | Mise en route de l'agent | Opératoire |
| [00_cartographie.md](../00_cartographie.md) | Maintenir | Diagnostic historique et arbitrages | Document de travail |
| [traceability_map.md](traceability_map.md) | Maintenir | Chaîne information → décision → preuve | Traçabilité |
| [versioning_policy.md](versioning_policy.md) | Maintenir | Catégories et règles de version | Normatif — livrable V7 validé |
| [changelog.md](../changelog.md) | Maintenir | Journal du cadre | Non normatif |

---

## 5. Sources externes

Ces documents **ne font pas partie** de la documentation produite. Ils alimentent la rédaction.

| Fichier | Rôle | Autorité | Statut |
|---|---|---|---|
| [AKORIS_consolide.md](../_sources/AKORIS_consolide.md) | Référence doctrinale du cadre (v1.0) | **Niveau 2** — prime sur tout sauf décision humaine | SOURCE |
| [AKORIS_architecture_documentaire.md](../_sources/AKORIS_architecture_documentaire.md) | Plan d'architecture et d'organisation | **Niveau 3** | SOURCE |
| [akoris_documentation_builder.md](../_sources/akoris_documentation_builder.md) | Mandat et méthode du rédacteur documentaire | **Niveau 4** | SOURCE |
| `C:\demo_web - Copie\*` | Projet pilote : manuel v1, contrats, état, rapports, ADR | **Niveau 5** — matériau, non doctrinal | SOURCE (A6) |

**Règle :** aucun contenu du pilote n'est promu en règle du protocole sans décision explicite. Le pilote fournit des **formes** et des **preuves d'implémentation**, pas des **normes**.

**Convention de travail (A4) — état courant :** le déplacement des sources F1–F3 vers `documentation/_sources/` a été décidé et appliqué le 2026-11-21 (arbitrage A13). Ce déplacement ne modifie pas la hiérarchie d'autorité documentaire : F3 conserve le Niveau 2, F2 le Niveau 3 et F1 le Niveau 4. `_sources/` n'est pas un répertoire d'archives non normatives. `00_cartographie.md` reste à la racine. La convention initiale de A4, qui maintenait les sources à la racine pendant les vagues 1 à 5, est conservée comme trace historique de cette décision.

---

## 6. Documents du projet gouverné (hors périmètre)

Ces fichiers appartiennent au **projet gouverné**, pas à la documentation AKORIS. Ils sont listés ici parce que le protocole les référence en permanence.

| Élément | Rôle | Source unique de |
|---|---|---|
| `state.json` | État opérationnel machine | État courant |
| `state.md` | Vue lisible générée | — (jamais une source) |
| `current_sprint.md` | Mandat du sprint courant | Périmètre autorisé |
| `contexte.md` | Synthèse du projet | Vision, périmètre, contraintes |
| `agents.md` | Contrats d'agents du projet | Permissions du projet |
| `docs/business_rules/` | Règles métier validées | Règles métier |
| `docs/use_cases/` | Cas d'utilisation | Parcours attendus |
| `docs/requirements/` | Exigences | Exigences |
| `docs/acceptance_criteria/` | Critères vérifiables | Critères |
| `docs/architecture/` | Architecture | Structure technique |
| `docs/adr/` | Décisions techniques | Compromis techniques |
| `docs/security/` | Exigences et contrôles de sécurité | Sécurité |
| `docs/risks/` | Registre des risques | Risques |
| `docs/governance/changes/` | Fiches de changement | Changements |
| `docs/governance/incidents/` | Incidents | Incidents |
| `docs/governance/readiness/` | Revues de préparation | `readiness_review` |
| `docs/governance/receipts/` | Reçus de transition (tous destinataires) | Reçus ORCHESTRATOR inclus |
| `sprints/roadmap.md` | Planification | Ordre des incréments |
| `sprint_report/` | Rapports BUILDER | Résultats de sprint |
| `audit_report/` | Rapports AUDITOR | Constats d'audit |
| `debt_report/` | Réserves et dette | Dette acceptée |

> **Décision C13 appliquée :** l'emplacement normatif de la `readiness_review` est `docs/governance/readiness/`. Le rapport historique du pilote `docs/governance/initialization_readiness_report.md` est **conservé** comme preuve historique ; il n'est ni réécrit ni promu en source concurrente.

> **Décision C26 appliquée :** le reçu d'ORCHESTRATOR est déposé dans `docs/governance/receipts/`, par le destinataire lui-même (`transition_policy.md` §5.2).

---

## 7. Autorité de rédaction

Qui fait autorité sur le **contenu** d'un document. Ce tableau ne décrit pas les permissions d'accès : la matrice contraignante est dans `permission_policy.md`.

| Document | Rédacteur | Validateur |
|---|---|---|
| `protocol/*` | DOCUMENTATION BUILDER | VALIDATOR |
| `implementations/opencode/*` | DOCUMENTATION BUILDER, sur constat technique | VALIDATOR |
| `prompts/*` | DOCUMENTATION BUILDER | VALIDATOR |
| `templates/*` | DOCUMENTATION BUILDER | VALIDATOR |
| `reference/*` | DOCUMENTATION BUILDER | VALIDATOR |
| `state.json` | ORCHESTRATOR | VALIDATOR |
| `state.md` | généré | — |
| `current_sprint.md` | ORCHESTRATOR | VALIDATOR |
| `sprint_report/` | BUILDER | AUDITOR, VALIDATOR |
| `audit_report/` | AUDITOR | VALIDATOR |
| `debt_report/` | ORCHESTRATOR | VALIDATOR |
| `docs/*` | ORCHESTRATOR | VALIDATOR |

---

## 8. Sources uniques par information

Une information, un fichier. Toute duplication est un défaut.

| Information | Source unique |
|---|---|
| Vocabulaire | `reference/terminology.md` |
| Règles communes | `protocol/governance_core.md` |
| Niveau d'exigence par risque | `protocol/profile_*.md` |
| États et invariants | `protocol/state_model.md` |
| Transitions et reçus | `protocol/transition_policy.md` |
| Décisions, gravités, preuves, réserves | `protocol/decision_policy.md` |
| Changements et urgences | `protocol/change_control.md` |
| Audit | `protocol/audit_policy.md` |
| Règles de permission | `protocol/permission_policy.md` |
| Configuration réelle des permissions | `implementations/opencode/agent_permissions.md` |
| Limites de l'environnement | `implementations/opencode/limitations.md` |
| Reprises et incidents | `protocol/recovery_policy.md` |
| Schéma technique de `state.json` | `reference/state.schema.json` |
| Forme des livrables | `templates/*` |
| Carte du corpus | `reference/document_map.md` |
| Traçabilité | `reference/traceability_map.md` |
| Versions | `reference/versioning_policy.md` |
| État courant | `state.json` |
| Mandat courant | `current_sprint.md` |

---

## 9. Dépendances

```text
terminology
    │
    ├── governance_core ──────────────┐
    │        │                        │
    │        ├── profile_standard     │
    │        │        ├── profile_lite
    │        │        └── profile_reinforced
    │        │                        │
    │        └── state_model ─────────┤
    │                 ├── transition_policy
    │                 ├── permission_policy ── implementations/opencode/*
    │                 ├── decision_policy ── change_control
    │                 │        └── recovery_policy
    │                 └── audit_policy
    │
    ├── document_map
    └── README
                     prompts/* ── dépendent de tout le socle
                     templates/* ── dépendent des politiques
                     getting_started ── dépend de tout
```

**Conséquence :** un document ne se rédige jamais avant ses dépendances. C'est ce qui fixe l'ordre des vagues.

---

## 10. Maintenance de cette carte

| Événement | Action |
|---|---|
| Un fichier est créé | Passer le chemin en lien, mettre `EXISTANT` |
| Un fichier est supprimé | Repasser en `code`, statut `SUPPRIMÉ` avec date |
| Un document change de rôle | Mettre à jour §4 et §8 |
| Une source d'autorité change | Mettre à jour §5 et §8 |
| Une vague est close | Mettre à jour §3 et le compteur |

La carte est mise à jour **à chaque fin de vague**, jamais en cours de rédaction.

---

## 11. Points ouverts

| Point | Impact |
|---|---|
| **C25** — échelle de risque chiffrée | Aucune n'existe : le choix de profil reste qualitatif |
| **T1→T5** | Tests non exécutés : aucune permission n'est `technical_enforced` ; protection de `main` maintenue `unknown` |
| Sources à la racine | 3 fichiers non déplacés, décision distincte |
| **A7 / catégories de versions** | `À ARBITRER` — divergences entre A7 (5 catégories), `00_cartographie.md` §7 (4 axes) et F2 §16 signalées dans [versioning_policy.md](versioning_policy.md) §4 ; aucune harmonisation |
| **Schéma de validation de `state.json`** | Divergence interne de `state_model.md` signalée (§6/§6.1 vs §10), non tranchée — [traceability_map.md](traceability_map.md) §7 |

### 11.1 Arbitrages tranchés — hors points ouverts

| Réf. | Objet | Statut |
|---|---|---|
| **A2** | Sérialisation de `state.json` | **Tranché** — Norme AKORIS v2.0 ; pilote v1.0 écart historique |
| **A5** | Statut du rôle documentaire | **Tranché** — rôle documentaire auxiliaire, hors boucle d'exécution applicative |
| **C13** | Emplacement de la `readiness_review` | **Tranché** — `docs/governance/readiness/` ; rapport pilote conservé |
| **C19** | `readiness_review` / `sprint_audit` | **Tranché** — deux contrôles distincts, retiré des points ouverts |
| **C26** | Reçu pour ORCHESTRATOR | **Tranché** — `docs/governance/receipts/` |
| **C27** | Expiration des transitions | **Tranché** — aucune durée numérique par défaut |
| **C28** | Schéma d'état | **Tranché** — `reference/state.schema.json` |
| **C29** | Protection de `main` | **Tranché** — statut `unknown` conservé, T5 préparé |

Les incohérences documentaires résiduelles I1 à I5 sont traitées par la présente maintenance.

---

## 12. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 1) — 34 fichiers cibles, 4 produits |
| 0.2 | 2026-11-20 | Vagues 2 et 3 closes — 11 produits ; 4 fichiers d'implémentation à planifier |
| 0.3 | 2026-11-20 | Vague 4 close — 14 produits |
| 0.4 | 2026-11-20 | Vague 5 close — 15 produits |

> **Note de maintenance (I4/I5).** L'en-tête reste fixé à `Version 0.4` par décision explicite. La création de `changelog.md` porte le compteur courant à 16/34 (§2) sans ouvrir de nouvelle version d'en-tête. L'entrée 0.4 ci-dessus enregistre l'état à la clôture de la vague 5 ; elle n'est pas réécrite.

> **Note de maintenance (vague 6, 2026-11-20).** Les quatre prompts et sept modèles de la vague 6 sont présents ; le compteur passe à 27/34 (§2). L'en-tête reste fixé à `Version 0.4` et l'entrée 0.4 ci-dessus n'est pas réécrite. Aucun livrable de la vague 7 n'est créé.

> **Note d'intégration (2026-11-21).** Les quatre documents `implementations/opencode/` issus de l'archive sont intégrés ; le compteur passe à 31/34 (§2). La vague 7 n'est pas engagée : `protocol/getting_started.md`, `reference/traceability_map.md` et `reference/versioning_policy.md` restent à produire. Les notes de maintenance antérieures ne sont pas réécrites.

> **Note de clôture (vague 7, 2026-11-21).** Les trois livrables sont créés, liés et marqués `EXISTANT` (§3, §4.2, §4.6) ; le compteur passe à 34/34 (§2). L'en-tête reste fixé à `Version 0.4` et la note d'intégration ci-dessus, qui décrivait l'état avant la vague 7, n'est pas réécrite. Les trois documents restent **PROPOSITION — à valider par le VALIDATOR** ; aucun test T1 à T5 n'a été exécuté et aucune permission n'est certifiée.

> **Note corrective (2026-11-21 — arbitrage A03).** La note de clôture ci-dessus décrivait l'état avant validation et est conservée comme trace historique. Les trois livrables V7 concernés sont `protocol/getting_started.md`, `reference/traceability_map.md` et `reference/versioning_policy.md` : leurs en-têtes portent **VALIDÉ PAR LE VALIDATOR — 2026-11-21**. Cette validation ciblée ne s'étend pas au reste du corpus, qui conserve son statut propre ; elle ne vaut ni validation générale ni autorisation d'exécution. Aucun test T1 à T5 n'a été exécuté et aucune permission n'est certifiée.
