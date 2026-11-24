# C1-A — Hiérarchie documentaire et prévalence des sources

**Chantier** : C1 — Consolidation normative et documentaire  
**Tâche** : C1-A — Hiérarchie documentaire  
**Transition** : TR-2026-0002 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C1-consolide-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C1` (alignée sur `main`, intègre les 10 commits C0)  
**Contrainte** : Modifications autorisées uniquement dans le périmètre C1 défini ; pas de fusion vers `main` sans HVG1

---

## 1. Vérification état Git (prérequis C1-A)

| Vérification | Résultat | Preuve |
|---|---|---|
| Branche courante | `dev_C1` | `git branch` |
| Alignement avec `main` | `dev_C1` = `main` (commit `ea42a48`) | `git log --oneline main -1` = `git log --oneline -1` |
| Intégration C0 dans `main` | 10 commits C0 présents sur `main` | `git log --oneline main` (commits 81345a0 à ea42a48) |
| Commit initial préservé | `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea` | Premier commit de l'historique |
| Reçu de transition C1 déposé | `livrables/C1/transition/recu_transition_C1.md` | Fichier créé, untracked |

---

## 2. Objectif de C1-A

Établir la **hiérarchie documentaire** du corpus AKORIS consolidé :

1. Classer les fichiers en catégories : normatives, opérationnelles, explicatives, historiques/sources
2. Définir la **prévalence des sources** (quelle source fait autorité en cas de divergence)
3. Distinguer les autorités sources sur certains documents (levée partielle de la réserve R3)
4. Consigner le résultat dans ce document

---

## 3. Hiérarchie des catégories

Chaque document du corpus appartient à exactement une catégorie principale. Cette hiérarchie reprend et formalise le travail de classification C0-04.

| Rang | Catégorie | Définition | Nombre de documents (C0) |
|---|---|---|---|
| 1 | **Normatifs** | Documents qui édictent des règles, obligations, politiques, socle, états, invariants applicables au cadre AKORIS | 13 |
| 2 | **Opérationnels** | Documents qui décrivent comment exécuter, démarrer, rapporter, auditer — guides, manuels, prompts, modèles, constat d'implémentation | 21 |
| 3 | **Explicatifs** | Documents qui présentent, introduisent, naviguent, expliquent le cadre sans édicter de règle (point d'entrée, vocabulaire, carte, journal) | 8 |
| 4 | **Historiques / sources** | Documents sources qui ont alimenté la rédaction, antérieurs au corpus produit, sans autorité normative par défaut | 3 |

> Les 45 documents du corpus sont classés dans `livrables/C0/classification/tableau_classification.md` (C0-04). Cette hiérarchie est reconduite telle quelle pour C1.

---

## 4. Prévalence des sources (table d'autorité)

La prévalence des sources détermine, en cas de divergence entre deux documents, lequel fait autorité. Cette table est nouvelle pour C1 (C0 se contentait de classer et de signaler les divergences sans trancher).

### 4.1 Table de prévalence

| Niveau | Source | Rôle | Prévalence | Commentaire |
|---|---|---|---|---|
| **1** | Décision humaine validée (VALIDATOR) | Prime sur tout le reste | Absolue | Toute décision VALIDATOR tracée prévaut sur tout document |
| **2** | `protocol/governance_core.md` | Socle commun obligatoire (54 règles GC) | Haute | Aucun profil, projet ou implémentation ne peut retirer ou affaiblir une règle du socle (GC-02) |
| **3** | `protocol/*_policy.md` (politiques spécialisées) | Source unique par domaine (décisions, changements, audit, permissions, reprises, transitions, état) | Haute | Chaque politique est la source unique de son domaine (`document_map.md` §8) |
| **4** | `reference/terminology.md` | Vocabulaire unique du cadre | Moyenne-élevée | Un terme défini ici ne doit pas être redéfini ailleurs (T §0) |
| **5** | `reference/document_map.md` | Index du corpus, sources uniques par information | Moyenne | Recense la source unique de chaque information (§8) |
| **6** | `reference/state.schema.json` | Schéma technique de `state.json` v2.0 | Moyenne | Schéma AKORIS v2.0 (décision C28) |
| **7** | `reference/versioning_policy.md` | Catégories de versions (A7) | Moyenne | Cinq catégories distinctes |
| **8** | `reference/traceability_map.md` | Chaîne exigence → tâche → test → preuve → décision | Moyenne | Cadre de lecture, pas de règle normative |
| **9** | `_sources/AKORIS_consolide.md` (F3) | Doctrine du cadre (v1.0) | Basse | Niveau 2 déclaré, source historique, pas d'autorité normative par défaut (réserve R3) |
| **10** | `_sources/AKORIS_architecture_documentaire.md` (F2) | Plan d'architecture | Basse | Niveau 3 déclaré, source historique |
| **11** | `_sources/akoris_documentation_builder.md` (F1) | Méthode de rédaction | Basse | Niveau 4 déclaré, source historique |
| **12** | Pilote `demo_web` (sources externes) | Matériau d'implémentation v1 | Très basse | Niveau 5 — matériau, non doctrinal (A6) |

### 4.2 Règle de prévalence en cas de divergence

En cas de divergence entre deux documents portant sur la même information :

1. Le document au **niveau le plus bas** (plus proche du niveau 1) fait autorité.
2. Si deux documents sont au même niveau, la divergence est signalée au VALIDATOR pour arbitrage (elle n'est pas corrigée silencieusement — GC-31).
3. Les sources historiques (niveaux 9 à 12) n'ont **jamais** autorité sur les documents produits du corpus (niveaux 1 à 8), sauf décision explicite du VALIDATOR.

---

## 5. Classification consolidée avec prévalence

Le tableau ci-dessous reprend les 45 documents du corpus avec leur catégorie principale et leur niveau de prévalence.

| # | Fichier | Catégorie principale | Niveau de prévalence | Source d'autorité en cas de divergence |
|---|---|---|---|---|
| 1 | `00_cartographie.md` | Explicatif | 8 | `document_map.md` (niveau 5) |
| 2 | `changelog.md` | Explicatif | 8 | `document_map.md` (niveau 5) |
| 3 | `plan_de_consolidation.md` | Opérationnel | 8 | `document_map.md` (niveau 5) |
| 4 | `README.md` | Explicatif | 5 | `document_map.md` (niveau 5) |
| 5 | `state.json` | Opérationnel | 6 (schéma) | `state.schema.json` (niveau 6) |
| 6 | `_sources/AKORIS_architecture_documentaire.md` | Historique / sources | 10 | N/A (source historique, pas d'autorité normative) |
| 7 | `_sources/AKORIS_consolide.md` | Historique / sources | 9 | N/A (source historique, pas d'autorité normative) |
| 8 | `_sources/akoris_documentation_builder.md` | Historique / sources | 11 | N/A (source historique, pas d'autorité normative) |
| 9 | `implementations/opencode/README.md` | Explicatif | 8 | `document_map.md` (niveau 5) |
| 10 | `implementations/opencode/agent_permissions.md` | Opérationnel | 8 | `permission_policy.md` (niveau 3) |
| 11 | `implementations/opencode/environment_requirements.md` | Explicatif | 8 | `permission_policy.md` (niveau 3) |
| 12 | `implementations/opencode/frontmatter_reference.md` | Explicatif | 8 | `permission_policy.md` (niveau 3) |
| 13 | `implementations/opencode/limitations.md` | Explicatif | 8 | `permission_policy.md` (niveau 3) |
| 14 | `prompts/akoris_auditor_bootstrap.md` | Opérationnel | 3 | `audit_policy.md` (niveau 3) |
| 15 | `prompts/akoris_builder_bootstrap.md` | Opérationnel | 3 | `governance_core.md` (niveau 2) |
| 16 | `prompts/akoris_documentation_builder.md` | Opérationnel | 3 | `document_map.md` (niveau 5) |
| 17 | `prompts/akoris_orchestrator_bootstrap.md` | Opérationnel | 3 | `governance_core.md` (niveau 2) |
| 18 | `protocol/audit_policy.md` | Normatif | 3 | `audit_policy.md` lui-même (source unique) |
| 19 | `protocol/change_control.md` | Normatif | 3 | `change_control.md` lui-même (source unique) |
| 20 | `protocol/decision_policy.md` | Normatif | 3 | `decision_policy.md` lui-même (source unique) |
| 21 | `protocol/getting_started.md` | Opérationnel | 3 | `getting_started.md` lui-même (source unique, V7 validé) |
| 22 | `protocol/governance_core.md` | Normatif | 2 | `governance_core.md` lui-même (socle) |
| 23 | `protocol/permission_policy.md` | Normatif | 3 | `permission_policy.md` lui-même (source unique) |
| 24 | `protocol/profile_lite.md` | Normatif | 3 | `governance_core.md` (niveau 2) |
| 25 | `protocol/profile_reinforced.md` | Normatif | 3 | `governance_core.md` (niveau 2) |
| 26 | `protocol/profile_standard.md` | Normatif | 3 | `governance_core.md` (niveau 2) |
| 27 | `protocol/recovery_policy.md` | Normatif | 3 | `recovery_policy.md` lui-même (source unique) |
| 28 | `protocol/state_model.md` | Normatif | 3 | `state_model.md` lui-même (source unique) |
| 29 | `protocol/transition_policy.md` | Normatif | 3 | `transition_policy.md` lui-même (source unique) |
| 30 | `reference/document_map.md` | Explicatif | 5 | `document_map.md` lui-même (source unique) |
| 31 | `reference/state.schema.json` | Normatif | 6 | `state.schema.json` lui-même (source unique) |
| 32 | `reference/terminology.md` | Explicatif | 4 | `terminology.md` lui-même (source unique) |
| 33 | `reference/traceability_map.md` | Explicatif | 8 | `document_map.md` (niveau 5) |
| 34 | `reference/versioning_policy.md` | Normatif | 7 | `versioning_policy.md` lui-même (source unique) |
| 35–41 | `templates/*` (7 fichiers) | Opérationnel | 8 | Politique correspondante (niveau 3) |
| 42–45 | `livrables/C0/transition/*` (4 fichiers) | Opérationnel | 8 | `transition_policy.md` (niveau 3) |

---

## 6. Autorités sources par domaine (sources uniques)

Conformément à `document_map.md` §8 (sources uniques par information) et à la prévalence établie ci-dessus :

| Information | Source unique | Niveau de prévalence |
|---|---|---|
| Vocabulaire | `reference/terminology.md` | 4 |
| Règles communes | `protocol/governance_core.md` | 2 |
| Niveau d'exigence par risque | `protocol/profile_*.md` | 3 |
| États et invariants | `protocol/state_model.md` | 3 |
| Transitions et reçus | `protocol/transition_policy.md` | 3 |
| Décisions, gravités, preuves, réserves | `protocol/decision_policy.md` | 3 |
| Changements et urgences | `protocol/change_control.md` | 3 |
| Audit | `protocol/audit_policy.md` | 3 |
| Règles de permission | `protocol/permission_policy.md` | 3 |
| Configuration réelle des permissions | `implementations/opencode/agent_permissions.md` | 8 (constat, pas de règle) |
| Limites de l'environnement | `implementations/opencode/limitations.md` | 8 (constat, pas de règle) |
| Reprises et incidents | `protocol/recovery_policy.md` | 3 |
| Schéma technique de `state.json` | `reference/state.schema.json` | 6 |
| Forme des livrables | `templates/*` | 8 |
| Carte du corpus | `reference/document_map.md` | 5 |
| Traçabilité | `reference/traceability_map.md` | 8 |
| Versions | `reference/versioning_policy.md` | 7 |
| État courant | `state.json` | 6 (via schéma) |
| Mandat courant | `current_sprint.md` | 8 (projet gouverné) |

---

## 7. Réserve R3 — Levée partielle (autorité sources historiques)

La réserve R3 de C0 stipulait : *« Ne pas attribuer d'autorité normative par défaut aux sources historiques. »*

Dans le cadre de C1-A, cette réserve est **partiellement levée** de la manière suivante :

- Les sources historiques (F1, F2, F3) conservent leur statut de **sources, pas de règles normatives** (niveaux 9 à 11 de prévalence).
- Elles ne peuvent **jamais** prévaloir sur un document produit du corpus (niveaux 1 à 8), sauf décision explicite du VALIDATOR.
- Leur rôle est limité à l'**origine historique** et au **contexte** d'une règle, jamais à sa définition normative.
- Le pilote `demo_web` (niveau 12) reste classé « matériau, non doctrinal » (A6).

La réserve R3 reste donc **ouverte** pour toute attribution d'autorité normative aux sources historiques qui serait demandée ultérieurement.

---

## 8. Preuves attendues pour C1-A

| Preuve | Référence | Statut |
|---|---|---|
| État Git sur dev_C1 | `git branch`, `git log --oneline main` | `directly_verified` |
| Hiérarchie documentaire | Ce document (`hiérarchie_doc.md`) | Produit |
| Table de prévalence des sources | §4.1 | Produit |
| Classification consolidée | §5 | Produit (reprend C0-04) |
| Note sur levée R3 | §7 | Produit |

---

## 9. Suite de C1

Après C1-A, les tâches suivantes sont prévues dans le mandat C1 :

| Tâche | Description | Livrable attendu |
|---|---|---|
| C1-B | Modèle d'état (`state.json`, `state.md`) | `livrables/C1/etat_model/` |
| C1-C | Permissions, rôles | `livrables/C1/permissions/` |
| C1-D | Registres décisions | `livrables/C1/registres/` |
| C1-E | Versionning SemVer | `livrables/C1/versioning/` |
| C1-F | Git/GitHub atomique | `livrables/C1/git/` |
| C1.1 | Traitement divergences C0 (propositions documentées) | `livrables/C1/registres/` |
| C1.3 | Distinction MUST/SHOULD/MAY/OUT OF SCOPE | Dans les documents du corpus |
| C1.4 | Modifications dans périmètre C1 uniquement | — |
| C1.5 | Vérification cohérence croisée | — |
| C1.6 | Préparation mandat AUDITOR C1 | `livrables/C1/rapport/` |
| C1.7 | Rapport C1 + réserves → VALIDATOR (HVG1) | `livrables/C1/rapport/rapport_C1.md` |

---
*Fin de C1-A. Hiérarchie documentaire et prévalence des sources établies. Réserve R3 partiellement levée (pas d'autorité normative par défaut aux sources historiques).*