# C0-08 — Examen des sources historiques

**Tâche** : C0-08 — Examiner sources historiques et relations avec corpus  
**Date d'exécution** : 2026-11-24  
**Contrainte** : Pas d'attribution d'autorité normative par défaut aux sources historiques

---

## 1. Méthode

Les sources historiques sont les documents qui ont alimenté la rédaction du cadre AKORIS, antérieurs au corpus produit. Elles sont examinées pour comprendre leur origine, leur relation avec le corpus actuel, leur contexte et leur périodicité. Aucune autorité normative n'est attribuée par défaut.

---

## 2. Liste des sources historiques

| # | Fichier | Rôle déclaré | Niveau d'autorité (déclaré) | Origine historique | Contexte | Périodicité |
|---|---|---|---|---|---|---|
| S1 | `_sources/AKORIS_consolide.md` | Référence doctrinale du cadre (v1.0) | Niveau 2 — prime sur tout sauf décision humaine | Document consolidé v1.0, antérieur au corpus produit | Doctrinal : principes, rôles, profils, états, décisions, preuves, changements, audit, permissions, checkpoints | Version 1.0, date inconnue (pas de bloc de version dans le document) |
| S2 | `_sources/AKORIS_architecture_documentaire.md` | Plan d'architecture et d'organisation | Niveau 3 | Plan d'architecture antérieur au corpus produit | Architectural : arborescence, rôle de chaque fichier, mandats, contexte par agent | Date inconnue (pas de bloc de version) |
| S3 | `_sources/akoris_documentation_builder.md` | Mandat et méthode du rédacteur documentaire | Niveau 4 | Mandat de rédaction antérieur au corpus produit | Méthodologique : méthode de production, interdictions, format de rapport | Date inconnue (pas de bloc de version) |
| S4 | `C:\demo_web - Copie\*` (projet pilote) | Manuel v1, contrats, état, rapports, ADR | Niveau 5 — matériau, non doctrinal | Projet pilote antérieur, version antérieure du cadre | Matériel d'implémentation : getting_started.md v1 (mono-profil), agents.md, contexte.md, current_sprint.md, state.json/state.md v1.0, templates, .opencode/agents/, opencode.json, docs/, sprints/, rapports | Version v1.0 du pilote, date inconnue |
| S5 | `C:\demo_web` (variante allégée) | `state.json`, `rapports/`, `transitions/` | Niveau 5 — matériau, non doctrinal | Variante allégée du pilote | État et rapports du pilote | Date inconnue |

---

## 3. Relations avec le corpus actuel

| Source | Relation avec le corpus | Utilisation dans le corpus actuel | Autorité normative attribuée ? |
|---|---|---|---|
| S1 `AKORIS_consolide.md` | Source principale de doctrine | Cité par `governance_core.md`, `decision_policy.md`, `state_model.md`, `transition_policy.md`, `permission_policy.md`, `audit_policy.md`, `recovery_policy.md`, `00_cartographie.md`, `document_map.md` §5 | **Non** — niveau 2, prime sur tout sauf décision humaine validée ; pas d'autorité normative par défaut |
| S2 `AKORIS_architecture_documentaire.md` | Source d'architecture | Cité par `governance_core.md`, `document_map.md` §5, `decision_policy.md`, `state_model.md` | **Non** — niveau 3 |
| S3 `akoris_documentation_builder.md` | Source de méthode | Cité par `governance_core.md`, `document_map.md` §5 | **Non** — niveau 4 |
| S4 Pilote `demo_web - Copie` | Matériau d'implémentation | Référencé dans `00_cartographie.md` §2.2, `document_map.md` §5 (niveau 5), `audit_policy.md` §4.1 (source GS1), `terminology.md` (source GS1 pour `instance d'agent`) | **Non** — niveau 5, matériau, pas doctrine |
| S5 Pilote `demo_web` (allégé) | Matériel d'implémentation allégé | Référencé dans `00_cartographie.md` §2.2 | **Non** — niveau 5 |

---

## 4. Hiérarchie d'autorité des sources (déclarée dans le corpus)

| Niveau | Source | Usage |
|---|---|---|
| 1 | Décision humaine validée (VALIDATOR) | Prime sur tout |
| 2 | `AKORIS_consolide.md` (v1.0) | Doctrine du cadre |
| 3 | `AKORIS_architecture_documentaire.md` | Plan d'architecture |
| 4 | `akoris_documentation_builder.md` + conventions de projet | Méthode de production |
| 5 | `getting_started.md` du pilote | **À ARBITRER** (A6) — matériau, pas doctrine |
| 6 | Propositions du DOCUMENTATION BUILDER | Jamais présentées comme validées |

> **Déclaration C0-08** : Aucune autorité normative n'est attribuée par défaut aux sources historiques. Leur niveau d'autorité (2 à 5) est celui déclaré dans le corpus, et il reste subordonné à toute décision humaine validée (niveau 1).

---

## 5. Contexte et périodicité

| Source | Contexte de création | Périodicité | Mise à jour connue |
|---|---|---|---|
| S1 | Rédaction initiale de la doctrine AKORIS v1.0 | Version unique v1.0 | Aucune mise à jour documentée dans le fichier |
| S2 | Planification de l'architecture documentaire AKORIS | Version unique | Aucune mise à jour documentée dans le fichier |
| S3 | Méthode de rédaction documentaire AKORIS | Version unique | Aucune mise à jour documentée dans le fichier |
| S4 | Implémentation pilote `demo_web` (version v1 du cadre) | Version v1.0 du pilote | Aucun historique de version dans les fichiers pilotes référencés |
| S5 | Variante allégée du pilote | Version unique | Aucune mise à jour documentée |

---

## 6. Observations

- Les trois sources S1-S3 ont été déplacées de la racine vers `_sources/` par l'arbitrage A13 (2026-11-21), sans modification de leur contenu ; leurs empreintes SHA-256 avant et après déplacement sont identiques (`changelog.md` §4 note datée A13).
- `00_cartographie.md` §3 observe que F3 (S1) est le document le plus ancien du dossier et pourtant le plus autoritaire (niveau 2) : la récence ne vaut pas autorité.
- Le pilote (S4) implémente une version antérieure du cadre : sans profils, 3 valeurs de décision, `state.json` v1.0, 5 états de transition. Il est déclaré non conforme à la Norme AKORIS v2.0 (`state_model.md` §6.1).
- Aucune des sources historiques ne porte de bloc de version/date/statut standard (sauf S1 qui déclare « Version consolidée : 1.0 » en en-tête). Les dates et versions de F2 et F1 sont `INCONNU` (`versioning_policy.md` §5).

---
*Fin de l'examen des sources historiques. Aucune autorité normative attribuée par défaut. Total : 5 sources identifiées (S1 à S5).*