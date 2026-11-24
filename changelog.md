# Changelog — cadre documentaire AKORIS

| Champ | Valeur |
|---|---|
| Version | 0.3 |
| Date | 2026-11-21 |
| Statut | **Journal de maintenance — non normatif** |
| Portée | Centralisation des historiques de version déjà présents dans le corpus |
| Autorité | Traçabilité — source unique du journal du cadre |
| Vague | 1 (création différée en maintenance) |

**Historiques repris et référencés :** [README.md §12](README.md), [reference/document_map.md §12](reference/document_map.md), [reference/terminology.md §12](reference/terminology.md), [implementations/opencode/agent_permissions.md §10](implementations/opencode/agent_permissions.md).

---

## 0. Objet

Ce fichier consigne **les évolutions de la documentation du cadre**, et non les évolutions du projet gouverné.

Il ne contient aucune règle de gouvernance. Les règles sont dans `protocol/`.

> **Règle (README §8, règle 8).** Toute évolution de la documentation est tracée ici avec version, date et documents affectés. Ce journal est distinct de l'historique de version interne de chaque document.

> **Règle de centralisation (I5).** Le présent fichier **reprend et référence** les historiques déjà existants. Il ne modifie rétroactivement aucun d'entre eux : les fichiers source cités ci-dessus restent l'autorité de leur propre historique.

---

## 1. Journal

| Réf. | Date | Nature | Documents affectés | Décisions appliquées |
|---|---|---|---|---|
| V0 | 2026-11-20 | Vague 0 — analyse de l'existant | `00_cartographie.md` | — |
| V1 | 2026-11-20 | Vague 1 — socle documentaire | `README.md`, `reference/terminology.md`, `reference/document_map.md`, `protocol/governance_core.md` | A4, A5 (partiel), A6, A8 |
| V2 | 2026-11-20 | Vague 2 — profils de gouvernance | `protocol/profile_standard.md`, `protocol/profile_lite.md`, `protocol/profile_reinforced.md` | A3, A7 |
| V3 | 2026-11-20 | Vague 3 — état, transitions, permissions | `protocol/state_model.md`, `protocol/transition_policy.md`, `protocol/permission_policy.md`, `implementations/opencode/agent_permissions.md` | A2 (partiel), C22, C24 |
| V4 | 2026-11-20 | Vague 4 — décisions, changements, reprises | `protocol/decision_policy.md`, `protocol/change_control.md`, `protocol/recovery_policy.md`, `protocol/state_model.md`, `README.md`, `reference/document_map.md` | A1, C30, C31, C32, C33, C34 |
| V5 | 2026-11-20 | Vague 5 — politique d'audit | `protocol/audit_policy.md`, `README.md`, `reference/document_map.md` | C19, A2 (provisoire), A5, C22, C30, C31 |
| P5 | 2026-11-20 | Corrections préalables avant maintenance — **pas la vague 6** | `reference/terminology.md`, `implementations/opencode/agent_permissions.md`, `protocol/recovery_policy.md` | C19, A5, C34 |
| M1 | 2026-11-20 | Maintenance I1 à I5 | `README.md`, `reference/document_map.md`, `changelog.md`, `reference/state.schema.json`, `protocol/state_model.md`, `protocol/transition_policy.md`, `protocol/audit_policy.md`, `implementations/opencode/agent_permissions.md`, `protocol/permission_policy.md`, `reference/terminology.md` | A2, C13, C26, C27, C28, C29 |
| M2 | 2026-11-20 | Maintenance de cohérence — vague 6 (sans vague 7) | `README.md`, `reference/document_map.md`, `changelog.md`, `00_cartographie.md`, `protocol/transition_policy.md`, `protocol/audit_policy.md` | C26 (alignement de mention) ; état v6 reflété ; aucune nouvelle décision |
| V7 | 2026-11-21 | Vague 7 — manuel, traçabilité, versionnement ; compteur 34/34 | `reference/traceability_map.md`, `reference/versioning_policy.md`, `protocol/getting_started.md`, `README.md`, `reference/document_map.md`, `changelog.md` | A7, A2, C22, C26, C27, C28 référencées ; aucune nouvelle décision |
| — | 2026-11-21 | Validation partielle V7 par le VALIDATOR — trois livrables uniquement | `protocol/getting_started.md`, `reference/traceability_map.md`, `reference/versioning_policy.md`, `README.md`, `changelog.md` | Aucune nouvelle règle ; aucun test, droit ni état de projet modifié |
| A05-1 | 2026-11-21 | Complément de journal (arbitrage A05), enregistré le 2026-11-21 : historique `README.md` 0.7 — intégration des quatre documents OpenCode, compteur 31/34 | `README.md` | Aucune nouvelle décision ; date lue dans l'historique source |
| A05-2 | 2026-11-21 | Complément de journal (arbitrage A05), enregistré le 2026-11-21 : historique `protocol/audit_policy.md` 0.3 — harmonisation T4/T5 | `protocol/audit_policy.md` | Aucune nouvelle décision ; date lue dans l'historique source |
| A05-3 | 2026-11-20 | Complément de journal (arbitrage A05), enregistré le 2026-11-21 : historique `protocol/permission_policy.md` 0.3 — harmonisation documentaire de T4 | `protocol/permission_policy.md` | Aucune nouvelle décision ; date **2026-11-20** lue dans l'historique source |
| A01/A02 | 2026-11-21 | Arbitrage A01 : énumérations projet/sprint du schéma alignées sur le modèle, `checkpointStatus` défini dans le modèle ; arbitrage A02 : §10 corrigé | `protocol/state_model.md`, `reference/state.schema.json` | Validation JSON Schema `NON VÉRIFIÉE` ; lien de `checkpointStatus` avec les règles de revue restant à arbitrer |
| A03 | 2026-11-21 | Note corrective V7 ajoutée sans réécrire la note de clôture | `reference/document_map.md` | Validation ciblée sur trois livrables ; aucune validation générale |
| A04 | 2026-11-21 | En-tête aligné sur la dernière entrée d'historique (0.3 / 2026-11-21) | `protocol/audit_policy.md` | Aucune règle de versionnement inventée |
| A06 | 2026-11-21 | Parcours « Découvrir » aligné sur l'ordre du guide V7 | `README.md` | Guide validé non modifié |
| A07 | 2026-11-21 | Bandeau historique ajouté à la cartographie, avec renvoi à la définition courante de T4 | `00_cartographie.md` | Aucun test ni permission requalifié |
| A08/A11/A16 | 2026-11-21 | Inventaires remis au rapport ; migration du pilote différée sans modification | — | Aucune normalisation ni procédure créée |
| A09/A10/A14/A15 | 2026-11-21 | Clarification des sources et statuts, décision « pas de version de profil dans l'état », distinction A7/F2 §16 et règles de versionnement prospectives | `reference/versioning_policy.md` | Aucune application rétroactive ; compatibilité AKORIS restant à arbitrer |
| A12/A17 | 2026-11-21 | Table centrale des sigles de documents et rôles de lecture par parcours ajoutés | `reference/document_map.md` | Aucun classement universel ni renommage numérique |
| A13 | 2026-11-21 | Déplacement des sources F1–F3 vers `_sources/` sans changement de contenu ; liens, carte §5 et journal mis à jour | sources F1–F3, `reference/document_map.md`, `prompts/akoris_documentation_builder.md`, `reference/versioning_policy.md`, `changelog.md` | Hiérarchie d'autorité inchangée ; `00_cartographie.md` maintenu à la racine |
| A01-complément | 2026-11-21 | Correction post-exécution : §2.3 de `state_model.md` aligné sur l'arbitrage A01 — type de revue distinct du statut, aucune matrice de correspondance définie ; mention « restant à arbitrer » retirée | `protocol/state_model.md` | Décision déjà prise ; aucune nouvelle règle |
| A09/A14/A15-complément | 2026-11-21 | Précisions arbitrées : rôles des sources avec preuves et `NON DÉTERMINÉ`, correspondance A7/F2 §16 sans catégorie nouvelle, règles SemVer AKORIS approuvées (major/minor/patch, incrément événementiel, approbation du VALIDATOR) | `reference/versioning_policy.md` | Aucune application rétroactive ; révision documentaire simple |
| A01/A15-traces | 2026-11-21 | Les mentions « restant à arbitrer » des lignes A01/A02 et A09/A10/A14/A15 ci-dessus décrivent l'état antérieur et sont conservées comme traces ; les points sont désormais décidés (voir lignes complémentaires) | `changelog.md` | Aucune réécriture d'historique |

---

## 2. Historiques source centralisés

Les tableaux ci-dessous sont des **copies de centralisation**. Aucune ligne n'a été réécrite dans son fichier d'origine.

### 2.1 [README.md §12](README.md)

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 1) |
| 0.2 | 2026-11-20 | Mise à jour après vagues 2 et 3 : 11/34, liens profils et politiques |
| 0.3 | 2026-11-20 | Mise à jour après vague 4 : 14/34 |
| 0.4 | 2026-11-20 | Mise à jour après vague 5 : 15/34 |
| 0.5 | 2026-11-20 | Maintenance I1-I2 et intégration des décisions A2, C13, C26, C27, C28, C29 : 16/34 |
| 0.6 | 2026-11-20 | Maintenance de cohérence — vague 6 : 4 prompts et 7 modèles réalisés, compteur 27/34 |
| 0.7 | 2026-11-21 | Intégration des quatre documents OpenCode de l'archive : compteur 31/34 ; vague 7 non engagée |
| 0.8 | 2026-11-21 | Vague 7 : guide de démarrage, carte de traçabilité et politique de versionnement rédigés, puis validés par le VALIDATOR ; compteur 34/34 ; validation partielle |

### 2.2 [reference/document_map.md §12](reference/document_map.md)

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 1) — 34 fichiers cibles, 4 produits |
| 0.2 | 2026-11-20 | Vagues 2 et 3 closes — 11 produits ; 4 fichiers d'implémentation à planifier |
| 0.3 | 2026-11-20 | Vague 4 close — 14 produits |
| 0.4 | 2026-11-20 | Vague 5 close — 15 produits |

### 2.3 [reference/terminology.md §12](reference/terminology.md)

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 1) |
| 0.2 | 2026-11-20 | Intégration A5 (rôle documentaire auxiliaire) et C19 (`readiness_review` / `sprint_audit`) |
| 0.3 | 2026-11-20 | A2 (v2.0 normative) et C26 (reçu ORCHESTRATOR) intégrés |

### 2.4 [implementations/opencode/agent_permissions.md §10](implementations/opencode/agent_permissions.md)

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Constat initial — 22 règles, 0 test exécuté |
| 0.2 | 2026-11-20 | Inspection ORCHESTRATOR (18 règles) et AUDITOR (13 règles) ; asymétrie comparée ; T1–T4 déclarés `NON EXÉCUTÉ` avec justification |
| 0.3 | 2026-11-20 | C29 : protection de `main` maintenue `unknown` ; T5 préparé, non exécuté |
| 0.4 | 2026-11-20 | Harmonisation documentaire de T4 approuvée par le VALIDATOR : branche protégée autre que `main`, dépôt de test ; T5 maintenu pour `main` ; contrôle AUDITOR/`src/**` conservé hors T1–T5 ; aucun test exécuté |

---

## 3. Détail de la maintenance M1

| Action | Contenu |
|---|---|
| **I1** | `README.md` : `Agent` remplacé par `Rôle auxiliaire` ; statut tranché ; hors de la boucle d'exécution applicative |
| **I2** | `README.md` : mention d'un statut ouvert supprimée ; DOCUMENTATION BUILDER indiqué comme rôle documentaire auxiliaire |
| **I3** | `reference/document_map.md` : A5 passé à `Tranché`, C19 retiré des points ouverts, `(A5)` retiré du prompt maintenu `PLANIFIÉ` en vague 6 |
| **I4** | `reference/document_map.md` : en-tête fixé à `Version 0.4` |
| **I5** | Création du présent fichier : centralisation et référencement des quatre historiques autorisés |
| **A2** | v2.0 devient la structure normative ; le pilote v1.0 est un écart historique |
| **C13** | Emplacement doctrinal `docs/governance/readiness/` ; rapport historique du pilote conservé |
| **C26** | Reçu ORCHESTRATOR dans `docs/governance/receipts/` |
| **C27** | Aucune durée numérique par défaut ; expiration selon le mandat et le profil |
| **C28** | `reference/state.schema.json` créé pour la Norme AKORIS v2.0 |
| **C29** | Protection de `main` maintenue `unknown` ; T5 préparé, non exécuté |

---

### 3.1 Maintenance M2 — vague 6

| Fichier | Correction effectuée |
|---|---|
| `README.md` | Compteur 27/34 ; vague 6 close ; prompts liés et marqués réalisés ; manuel v7 toujours absent ; historique 0.6 |
| `reference/document_map.md` | Compteur 27/34 ; 11 fiches v6 passées `EXISTANT` avec liens locaux ; note datée sans nouvelle version d'en-tête |
| `protocol/transition_policy.md` | §11 : mention « non tranché » alignée sur C26 — `docs/governance/receipts/` |
| `protocol/audit_policy.md` | T1 à T5 dans les renvois ; modèle AUDITOR indiqué créé en vague 6 ; statuts `NON EXÉCUTÉ` inchangés |
| `00_cartographie.md` | Note datée distinguant la photographie historique de l'état actuel (4 prompts, 7 modèles) ; D5 et D6 non tranchés |
| `changelog.md` | Entrée M2, ce détail et historique 0.2 |

---

### 3.2 Clôture V7 — trois livrables, compteur 34/34

| Fichier | Contenu |
|---|---|
| `reference/traceability_map.md` | Créé — chaîne exigence → tâche/action → test/contrôle → preuve → décision ; deux niveaux de traçabilité distingués ; champs restant à arbitrer |
| `reference/versioning_policy.md` | Créé — cinq catégories A7, emplacement et historique des versions, rôle du journal, divergences `00_cartographie.md` §7 et F2 §16, points `À ARBITRER` |
| `protocol/getting_started.md` | Créé en dernier — parcours complet orienté références, décisions du VALIDATOR, exemples marqués, statuts préservés |
| `README.md` | Compteur 34/34 ; vague 7 close ; trois livrables liés ; avertissement de non-validation maintenu à la clôture |
| `reference/document_map.md` | Trois fiches passées `EXISTANT` et liées ; arborescence `[x]` ; compteur 34/34 ; note de clôture datée |
| `changelog.md` | Entrée V7, ce détail, mise à jour des copies centralisées, note datée sur §4, historique 0.3 |

Corrections apportées pendant la rédaction, avant clôture : caractères parasites supprimés ; renvoi erroné `GC-22` remplacé par `[governance_core.md](protocol/governance_core.md) §0` ; renvois `DM` §11.1 retirés au profit de `README` §11, `SM` §8 et `T` §11. Aucune règle, catégorie, numérotation ni seuil n'a été ajouté.

Contrôles de clôture exécutés : 188 liens Markdown relatifs vérifiés sur les six fichiers touchés, 0 cassé ; 39 identifiants `GC-xx`/`INV-xx` cités, tous présents dans les sources ; renvois de sections vérifiés ; inventaire comparé au manifeste avant V7 : 36 → 39 fichiers, trois créations, aucune suppression, aucune autre modification avant clôture.

Aucun test T1 à T5 n'a été exécuté ; permissions et protection de `main` restent `unknown` ; C25 reste ouvert ; les trois livrables V7 sont désormais validés par le VALIDATOR, le reste du corpus conservant son statut propre.

**Corrections de revue (2026-11-21).** Le nombre de liens annoncé ci-dessus a été aligné sur le recomptage : 173 → **188**. En outre, `reference/versioning_policy.md` §2 et §5 précisent que `state.json` ne comporte **aucun champ de version du profil** : la version est portée par le document `profile_*.md`, et la relation entre un état et une version donnée de ce document est marquée `À ARBITRER`. Aucune autre règle ni aucun champ de schéma n'a été ajouté.

### 3.3 Validation partielle V7 — 2026-11-21

| Portée | Fichiers | Limites |
|---|---|---|
| Trois livrables V7 validés par le VALIDATOR | `protocol/getting_started.md`, `reference/traceability_map.md`, `reference/versioning_policy.md` | Validation documentaire uniquement : ni validation générale du corpus, ni autorisation d'exécution, ni certification de permission, ni modification de `state.json`, du schéma ou de règle normative |

Les réserves, divergences, points `À ARBITRER` et statuts d'exécution restent inchangés. Aucun identifiant de décision n'a été créé.

---

## 4. Ce que ce journal ne dit pas

- Il ne certifie **aucune permission technique**.
- Il ne déclare **aucun test T1 à T5 comme exécuté** ; tous restent `NON EXÉCUTÉ`.
- Il ne modifie pas les sources historiques : `AKORIS_consolide.md`, `AKORIS_architecture_documentaire.md`, `akoris_documentation_builder.md`.
- Il ne lance pas la vague 7 : aucun manuel, registre de projet ou fichier de la vague 7 n'est créé. La vague 6 a produit quatre prompts et sept modèles ; leur état est suivi dans `reference/document_map.md`.

> **Note datée (2026-11-21).** L'énoncé ci-dessus décrit l'état au 2026-11-20, à la clôture de la vague 6 ; il n'est pas réécrit. Depuis, la vague 7 a été lancée puis close : trois documents sont créés (§3.2) et le compteur est à 34/34. Aucun registre de projet, état réel ni preuve d'exécution n'a été créé pour autant.

> **Note datée (2026-11-21 — arbitrage A13).** Les trois sources historiques citées ci-dessus ont été déplacées vers `_sources/` sans modification de leur contenu ; leurs empreintes SHA-256 avant et après déplacement sont identiques. Le paragraphe historique ci-dessus n'est pas réécrit ; la localisation courante figure dans `reference/document_map.md` §5.

---

## 5. Historique du journal

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Création en maintenance (I5) — centralisation des quatre historiques autorisés et de la maintenance M1 |
| 0.2 | 2026-11-20 | Maintenance M2 — cohérence vague 6 : 27/34, statuts des livrables v6, alignement C26, T1 à T5 ; aucune permission certifiée |
| 0.3 | 2026-11-21 | Clôture V7 — trois livrables rédigés, compteur 34/34, liens et renvois vérifiés ; aucune permission certifiée, aucun test exécuté |

> **Note de journal (2026-11-21).** L'enregistrement de la validation partielle n'a ni incrémenté les versions d'en-tête ni créé d'identifiant de décision : la fréquence d'incrément et le format d'ID ne sont pas définis dans les sources consultées.
