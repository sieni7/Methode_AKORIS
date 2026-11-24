# Politique de versionnement AKORIS

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-21 |
| Statut | **VALIDÉ PAR LE VALIDATOR — 2026-11-21** |
| Portée | Catégories de versions arrêtées, emplacement de chaque version, traçabilité des évolutions |
| Autorité | Normatif — politique de versionnement |
| Vague | 7 |

**Sources citées :** `SM` = [state_model.md](../protocol/state_model.md) §6.1, §6.4, §8 · `T` = [terminology.md](terminology.md) §11 · `DM` = [document_map.md](document_map.md) §8 · `GC` = [governance_core.md](../protocol/governance_core.md) · `CC` = [change_control.md](../protocol/change_control.md) §6, §8 · `TP` = [transition_policy.md](../protocol/transition_policy.md) §7 · `CART` = [00_cartographie.md](../00_cartographie.md) §7, décision A7 · `F2` = [AKORIS_architecture_documentaire.md](../_sources/AKORIS_architecture_documentaire.md) §16 · `CHL` = [changelog.md](../changelog.md) · décisions VALIDATOR **A2**, **A7**, **C25**, **C27**, **C28**.

---

## 0. Objet et frontière

Cette politique **formalise des décisions déjà prises** et indique où chaque version est portée et où son historique est tracé.

Elle ne crée **aucune** règle de numérotation, aucun schéma SemVer, aucune règle major/minor/patch et aucune procédure de migration. Ces points ne sont pas définis par les sources consultées : ils sont explicitement `À ARBITRER` en §5 et appellent une décision humaine.

> **Note d'actualisation (2026-11-21 — arbitrage A15).** L'énoncé ci-dessus décrivait la portée initiale du livrable V7 et est conservé comme trace historique. Depuis, l'arbitrage A15 a ajouté prospectivement une décision de numérotation (SemVer indépendant pour le protocole et le schéma ; révision simple pour les documents) en §5. Les règles AKORIS de `major` / `minor` / `patch` sont désormais approuvées (A15) ; seule la procédure de migration du pilote n'est toujours pas définie (A16 différé). Aucune application rétroactive aux numéros existants n'est opérée.

Elle ne modifie ni le modèle d'état, ni le schéma technique, ni les sources historiques. Une divergence entre sources est signalée en §4, sans harmonisation silencieuse.

---

## 1. Les cinq catégories retenues (A7)

La décision **A7** est tranchée : cinq versions distinctes coexistent et ne se confondent jamais. Elle est reprise dans `SM` §8, `T` §11 et [README.md](../README.md) §11.

| Catégorie | Objet | Portée par | Source |
|---|---|---|---|
| **Protocole** | Règles du cadre | `protocol.version` | `SM` §8, `SM` §6.4 |
| **Profil** | Niveau d'exigence | Document de profil (`profile_*.md`) | `SM` §8 |
| **Schéma** | Structure de `state.json` | `schema_version` | `SM` §8, décision **C28** |
| **Mandat** | Périmètre autorisé | `current_sprint.md`, `mandate_version` | `SM` §8, `TP` §2 |
| **Document** | Révision d'un fichier | En-tête de chaque document | `SM` §8 |

> **Séparation (SM §6.4).** `schema_version` est distinct de `protocol.version`. Une évolution du protocole n'est pas une évolution du projet, et une évolution du schéma n'est pas une évolution du protocole (`SM` §8, `F2` §16).

---

## 2. Où chaque version est portée et tracée

| Catégorie | Portée par | Historique / trace de l'évolution | Autorité de l'évolution |
|---|---|---|---|
| **Protocole** | `protocol.version` dans la structure v2.0 de `state.json` ; en-tête `Version` des documents de `protocol/` | Section `Historique` de chaque document ; `CHL` (journal du cadre) | Décision du VALIDATOR ; [governance_core.md](../protocol/governance_core.md) §0 (stabilité du socle) |
| **Profil** | En-tête `Version` du document `profile_*.md` (`SM` §8) | Section `Historique` du profil ; `CHL` ; procédure de changement de profil (`CC` §8) | VALIDATOR, avant CP1, puis verrouillé (`GC-09`, `INV-11`) |
| **Schéma** | `schema_version` dans `state.json` ; schéma technique [state.schema.json](state.schema.json) — **Schéma AKORIS v2.0** | `SM` §6.1 et §11 ; `CHL` (décisions **A2**, **C28**) | Décision **A2** ; toute évolution versionnée selon A7 et tracée dans `CHL` |
| **Mandat** | `current_sprint.md` ; `mandate_version` dans la transition et l'état | `state.json` (`change_control`, `transition_history`) ; `CC` §10 | VALIDATOR ; changement ⇒ nouvelle version, nouvelle transition, nouveau `GO` (`CC` §6) |
| **Document** | En-tête `Version` de chaque fichier | Section `Historique` interne du fichier ; `CHL` centralise et référence les historiques autorisés | Rédacteur du document ; validation par le VALIDATOR pour les documents du corpus |

> **Précision A15 (2026-11-21).** La mention de l'en-tête `Version` des documents de `protocol/` dans la ligne « Protocole » est conservée comme trace de la catégorie A7. Depuis A15, la version du protocole est portée par `protocol.version` dans `state.json` et relève de SemVer ; l'en-tête d'un document est une **révision documentaire simple**. Aucune identité ni aucun numéro commun n'est supposé entre les deux, et aucune signification SemVer n'est attribuée rétroactivement aux en-têtes existants.

> **Mandat (INV-10).** Un changement de version de mandat invalide l'autorisation en cours. Poursuivre avec un mandat périmé est une violation **P1** (`CC` §6).

> **Schéma (A2/C28).** La structure imbriquée v2.0 est la structure normative ; la structure plate v1.0 du pilote est un écart historique. La migration du pilote n'est **pas** réalisée par la documentation (`SM` §6.1). Voir §5 pour l'absence de procédure de migration.

> **Profil — précision (2026-11-21).** `state.json` n'enregistre **aucun champ de version du profil** : `governance` contient `profile` (profil actif), `profile_locked` (verrouillage), `selected_by` et `selected_at` (`SM` §6.4 ; `state.schema.json`, `additionalProperties: false`). Ces champs identifient le profil actif, **non sa version**. La version du profil appliqué est portée par l'en-tête du document `profile_*.md` (`SM` §8) ; la relation exacte entre un état et une version donnée de ce document n'est pas modélisée dans le schéma : `À ARBITRER` (§5).

> **Profil — décision A10 (2026-11-21).** Aucun champ de version du profil n'est ajouté à `state.json`, au modèle d'état ni au schéma. L'état identifie le profil actif et son verrouillage (`profile`, `profile_locked`) ; il ne fige pas la version du document `profile_*.md`. Cette version reste portée par l'en-tête du document de profil. La relation exacte entre un état et une version donnée de ce document demeure `À ARBITRER` (§5).

> **Sources et rôles — arbitrage A09 précisé (2026-11-21).** La validation ciblée de la présente politique (trois livrables V7) ne valide ni ses sources ni le reste du corpus. Le statut propre de chaque document est conservé tel qu'à son en-tête ; il n'est ni promu ni rétrogradé. Le rôle ci-dessous décrit l'usage documentaire vérifiable dans cette politique. Un rôle `NON DÉTERMINÉ` signale l'absence de preuve de dépendance ; aucune liste de dépendances normatives n'est fabriquée.

| Source | Statut d'en-tête courant | Rôle dans cette politique | Preuve documentaire précise |
|---|---|---|---|
| `SM` — `state_model.md` | `PROPOSITION — à valider par le VALIDATOR` | Dépendance normative | §1, colonne « Source » : `SM` §8 et §6.4 fondent les cinq catégories ; §4, ligne « A7 tranché — `SM` §8 ». |
| `T` — `terminology.md` | `PROPOSITION — à valider par le VALIDATOR` | Dépendance normative | §4, ligne « A7 tranché — `T` §11 » ; §6, règle « Signaler une divergence sans la corriger silencieusement — `T` §0 et §12 ». |
| `README.md` | Sans bloc d'en-tête standard | Dépendance normative | §4, ligne « A7 tranché — README §11 » ; §6, règle « Toute évolution tracée avec version et date — README §8, règle 8 ». |
| `GC` — `governance_core.md` | `PROPOSITION — à valider par le VALIDATOR` | Dépendance normative | §6 : renvois `GC-09`, `GC-31`, `GC-50`, `GC-51`, `GC-53` (autorité de l'évolution, divergence, unicité de l'information, exemples). |
| `CC` — `change_control.md` | `PROPOSITION — à valider par le VALIDATOR` | Dépendance normative | §6 : `CC` §6 (changement de mandat) et `CC` §8 (changement de profil). |
| `TP` — `transition_policy.md` | `PROPOSITION — à valider par le VALIDATOR` | Dépendance normative | §1, colonne « Source » de la catégorie Mandat : `TP` §2 ; §6 : `TP` §7 et `TP` §8. |
| `DM` — `document_map.md` | `PROPOSITION — à valider par le VALIDATOR` | Dépendance normative pour la règle d'unicité ; référence informative pour l'index | §6 : « Une information, une source unique — `DM` §8 ; `GC-50`, `GC-51` » ; rôle d'index rappelé dans la ligne « Sources citées » du présent document. |
| `profils` — `profile_*.md` | `PROPOSITION — à valider par le VALIDATOR` | Dépendance normative | §6 : « Aucun seuil de risque chiffré — README §11, décision C25 ; profils §1 ». |
| `CHL` — `changelog.md` | `Journal de maintenance — non normatif` | Référence informative, non normative | §3 : « Il est non normatif : les règles restent dans `protocol/` ». |
| `CART` — `00_cartographie.md` | `PROPOSITION — à valider par le VALIDATOR` | Référence informative historique ; rôle de source A7 : `NON DÉTERMINÉ` | §4 : mention « 4 axes » conservée comme formulation d'époque ; aucune règle de la présente politique ne dépend de `CART`. Pour établir un rôle normatif, il faudrait un acte du VALIDATOR assignant explicitement cette source. |
| `F2` — source déplacée sous `_sources/` par A13 | Aucun bloc `Version` / `Date` / `Statut` | Référence informative historique ; rôle de source A7 : `NON DÉTERMINÉ` | §4 : « `F2` §16 — liste historique » ; note A14 en §4 : inventaire historique, aucune catégorie créée. Aucune règle n'en dépend. Pour établir un rôle normatif, il faudrait un acte du VALIDATOR assignant explicitement cette source. |

> **Limite.** Les rôles marqués `NON DÉTERMINÉ` ne sont pas des dépendances normatives. Aucune règle de la présente politique ne repose sur `CART` ou `F2` : leur divergence est signalée en §4 sans être promue. La qualification ci-dessus ne modifie pas le statut propre des documents et ne démontre pas la validité technique de leur contenu. La validation de la politique ne valide ni ses sources ni le corpus entier.

---

## 3. Rôle de `changelog.md`

`CHL` est le **journal du cadre** : il consigne les évolutions de la documentation, avec version, date, nature et documents affectés.

- Il est **non normatif** : les règles restent dans `protocol/`.
- Il **centralise et référence** les historiques déjà existants (README §12, `DM` §12, `T` §12, `agent_permissions.md` §10) ; il ne modifie rétroactivement aucun d'entre eux.
- Il **ne remplace pas** l'historique interne d'un document : chaque fichier reste l'autorité de son propre historique.
- Il **ne contient pas l'état d'un projet** : l'état courant vit dans le `state.json` du projet gouverné (`README` §10, `GC-54`).
- Il **ne certifie aucune permission** et ne déclare aucun test T1 à T5 comme exécuté.

---

## 4. Divergences de source sur les catégories — signalées, non tranchées

Trois listes coexistent. Aucune n'est réécrite ici ; leur rapprochement relève d'une décision du VALIDATOR.

| Source | Liste portée | Écart avec A7 |
|---|---|---|
| **A7 tranché** — `SM` §8, `T` §11, [README.md](../README.md) §11 | Protocole, profil, schéma, mandat, document — **5 catégories** | Référence retenue |
| `CART` §7, ligne A7 — ancienne mention « **4 axes** » | Protocole, schéma, document, mandat — **4 axes** ; renvoi à C15 | Omet le **profil** ; mention historique conservée telle quelle dans `00_cartographie.md` |
| `F2` §16 — liste historique | « Versions distinguées » : protocole, profil, mandat, **état**, **projet** — **5 versions** ; « éléments à versionner » : protocole, profils, prompts, modèles de rapports, schéma de `state.json`, décisions techniques, mandats, documents métier validés — **8 éléments** | Remplace **schéma** et **document** par **état** et **projet** ; ajoute prompts, modèles et décisions techniques à la liste des éléments à versionner |

> **Statut : `FAIT` pour l'existence des trois listes ; `À ARBITRER` pour leur unification.** Aucune source n'est harmonisée silencieusement. Le `README` §11, `SM` §8 et `T` §11 enregistrent A7 comme tranché ; `CART` et `F2` conservent leur formulation d'époque.

> **Note d'actualisation (2026-11-21 — arbitrage A14).** La mention « `À ARBITRER` pour leur unification » ci-dessus est conservée comme trace de l'état antérieur. L'arbitrage A14 précisé établit A7 comme taxonomie de référence : aucune unification des listes n'est nécessaire ; `CART` et `F2` restent des formulations historiques signalées, sans harmonisation.

> **Clarification — arbitrage A14 précisé (2026-11-21).** A7 demeure la taxonomie de référence à cinq catégories : protocole, profil, schéma, mandat, document. La liste de F2 §16 demeure un inventaire historique d'éléments susceptibles d'être versionnés ; elle ne crée aucune catégorie A7 supplémentaire et son contenu n'est pas modifié. Correspondances établies : « protocole AKORIS » → Protocole ; « profils » → Profil ; « schéma de `state.json` » → Schéma ; « mandats » → Mandat ; « prompts », « modèles de rapports » et « documents métier validés », lorsqu'ils sont des fichiers, → Document ; « décisions techniques » consignées sous forme de document ou de registre → Document comme artefact documentaire, sans transformer cette classification en statut d'approbation de la décision. Les expressions « version de l'état » et « version du projet » ne deviennent pas des catégories A7 : elles ne sont pas définies par la taxonomie A7 et n'ont pas de portée opérationnelle ici. Leur éventuelle affectation est `NON DÉTERMINÉE` ; aucun champ correspondant n'est ajouté au schéma ni à l'état, et aucune sémantique, aucun emplacement ni aucune règle d'incrémentation n'est inventé.

---

## 5. Ce qui n'est pas défini — `À ARBITRER`

> **Décision A15 approuvée (2026-11-21) — règles AKORIS prospectives.** Le protocole et le schéma portent des versions **SemVer indépendantes** ; les documents utilisent une **révision simple**, sans garantie SemVer. Aucune signification SemVer n'est attribuée rétroactivement aux numéros existants. L'incrémentation est **événementielle** : elle intervient lors de la publication d'un changement approuvé, non selon un calendrier. Le protocole et le schéma sont évalués indépendamment : un même changement peut entraîner des incréments différents. Le VALIDATOR approuve la classification et la version ; le Builder prépare la proposition, les preuves d'impact et les modifications, sans s'auto-attribuer l'approbation.

| Incrément | Règle AKORIS approuvée (prospective) |
|---|---|
| `major` | Changement incompatible : rend invalide une instance auparavant conforme ou rompt une règle normative / une compatibilité établie. |
| `minor` | Extension compatible qui préserve les instances et les exigences antérieures. |
| `patch` | Correction ou clarification sans changement des exigences normatives ni de l'ensemble des instances acceptées par le schéma. |

> **Documents.** La révision documentaire simple est incrémentée lors d'une révision approuvée selon les règles documentaires existantes (§6) ; elle ne suit pas les règles SemVer ci-dessus.

> **Limite.** Ces règles s'appliquent prospectivement. Elles ne réinterprètent pas les numéros déjà portés par le corpus et n'imposent aucun numéro commun entre protocole et schéma. Toute proposition d'incrément est soumise au VALIDATOR avec ses preuves d'impact.

| Objet | État des sources | Action attendue |
|---|---|---|
| Schéma de numérotation | Décision A15 : SemVer indépendant pour le protocole et le schéma ; révision simple, sans garantie SemVer, pour les documents | **DÉCIDÉ** — applicable prospectivement |
| Règles major / minor / patch | Règles AKORIS approuvées dans le tableau ci-dessus | **DÉCIDÉ** — applicable prospectivement |
| Procédure de migration, y compris pilote v1.0 → Norme v2.0 | `SM` §6.1 : la migration n'est pas automatiquement réalisée par la documentation ; aucune procédure décrite | `À ARBITRER` — décision humaine requise (A16 différé) |
| Correspondance entre version du protocole, version du schéma et version du document | Versions déclarées distinctes ; décision A15 : numéros indépendants, aucun alignement imposé | **DÉCIDÉ** — aucun numéro commun supposé |
| Champ de version du profil dans `state.json` | `governance` porte `profile`, `profile_locked`, `selected_by`, `selected_at` ; aucun champ de version (`SM` §6.4, `state.schema.json`, `additionalProperties: false`). La version est portée par le document `profile_*.md` (`SM` §8) | **DÉCIDÉ (A10)** — aucun champ ajouté ; la version reste portée par le document de profil |
| Fréquence et responsable de l'incrément de version | Décision A15 : incrémentation événementielle à la publication d'un changement approuvé ; VALIDATOR approuve la classification et la version, Builder prépare la proposition, les preuves d'impact et les modifications | **DÉCIDÉ** — applicable prospectivement |
| Unification des trois listes de catégories | Voir §4 : A7 est la taxonomie de référence ; `F2` §16 reste un inventaire historique (A14) | **DÉCIDÉ** — aucune unification requise ; aucun classement universel ajouté |
| Dates et versions sur `F2` et `F1` | `CART` §7 : « aucune date ni version » sur ces sources | `INCONNU` — constat historique, non corrigé |

Les rubriques marquées `À ARBITRER` ou `INCONNU` ne sont pas traitées comme des règles. Les rubriques `DÉCIDÉ` sont des décisions du VALIDATOR tracées conformément à `GC-21` ; une proposition de rédaction ne devient décision que par acte du VALIDATOR tracé (`GC-21`).

---

## 6. Règles établies à respecter — renvois

Ces règles existent déjà ; elles sont rappelées par renvoi, non recopiées ni modifiées.

| Sujet | Renvoi |
|---|---|
| Une information, une source unique | `DM` §8 ; `GC-50`, `GC-51` |
| Signaler une divergence sans la corriger silencieusement | `GC-31` ; [terminologie.md](terminology.md) §0 et §12 |
| Toute évolution tracée avec version et date | [README.md](../README.md) §8, règle 8 ; `CHL` §0 |
| Changement de mandat ⇒ nouvelle version et nouveau `GO` | `CC` §6 ; `TP` §8 ; `INV-10` |
| Changement de profil = changement majeur | `CC` §8 ; `GC-09` |
| Aucune durée numérique par défaut | `TP` §7, décision **C27** |
| Aucun seuil de risque chiffré | [README.md](../README.md) §11, décision **C25** ; profils §1 |
| Exemples signalés comme exemples | `GC-53` |

---

## 7. Renvois

| Sujet | Document |
|---|---|
| Catégories de versions | [state_model.md](../protocol/state_model.md) §8 |
| Schéma technique v2.0 | [state.schema.json](state.schema.json) |
| Sources uniques | [document_map.md](document_map.md) §8 |
| Journal du cadre | [changelog.md](../changelog.md) |
| Chaîne exigence → décision | [traceability_map.md](traceability_map.md) |
| Parcours de lecture | [getting_started.md](../protocol/getting_started.md) |

---

## 8. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-21 | Version initiale (vague 7) — cinq catégories A7, emplacement des versions, rôle du journal, divergences `CART`/`F2`, points à arbitrer |

> **Note de statut (2026-11-21).** Statut aligné sur **VALIDÉ PAR LE VALIDATOR — 2026-11-21** ; validation limitée aux trois livrables V7. Aucune règle, preuve d'exécution, permission ni donnée d'état n'a été modifiée.
