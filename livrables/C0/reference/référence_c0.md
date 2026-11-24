# AKORIS — État de référence C0 (figé)

**Chantier** : C0 — Inventaire et état de référence du corpus AKORIS  
**Mandat** : C0-revise-v1  
**Transition** : TR-2026-0001  
**Décision VALIDATOR** : GO_WITH_RESERVES (HVG0), 2026-11-24  
**Date de gel de l'état de référence** : 2026-11-24  
**Branche d'exécution** : `dev_C0` (depuis `main` vérifié, commit `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea`)  
**Contrainte** : Lecture seule du corpus source — aucun document source modifié  
**Distinction** : Ce document est un état de référence autonome (Markdown). Il est distinct de `state.json` (source de vérité opérationnelle) et de `state.md` (vue générée).

---

## 1. Objet

Cet état de référence fige, à la date d'achèvement de C0, l'inventaire complet du corpus AKORIS, ses métadonnées, classifications, statuts, décisions, divergences, lacunes et dépendances. Il sert de base à la décision HVG0 distincte (transition C0 → C1 ou clôture C0).

---

## 2. Synthèse de l'inventaire

| Indicateur | Valeur |
|---|---|
| Dépôt | `C:\Methode_AKORIS` |
| Commit initial vérifié | `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea` |
| Branche de travail | `dev_C0` (depuis `main`) |
| Branche `main` | Vérifiée, propre, au commit initial |
| Fichiers trackés (commit initial) | 39 |
| Fichiers untracked | 6 (`plan_de_consolidation.md`, `state.json`, `livrables/C0/*`) |
| Total fichiers documentaires | 45 |
| Répertoires documentaires | 8 (`_sources`, `implementations/opencode`, `livrables/C0`, `prompts`, `protocol`, `reference`, `templates`, racine) |
| Modification de source | Aucune (lecture seule respectée) |

---

## 3. Référence aux livrables C0

| Domaine | Fichier livrable | Tâche C0 |
|---|---|---|
| État Git | `livrables/C0/inventaire/etat_git.md` | C0-01 |
| Arborescence fichiers | `livrables/C0/inventaire/arborescence_fichiers.md` | C0-02 |
| Métadonnées | `livrables/C0/metadonnees/tableau_metadonnees.md` | C0-03 |
| Classification | `livrables/C0/classification/tableau_classification.md` | C0-04 |
| Décisions | `livrables/C0/decisions/registre_decision.md` | C0-05 |
| Doublons | `livrables/C0/registres/registre_doublons.md` | C0-06 |
| Contradictions | `livrables/C0/registres/registre_contradictions.md` | C0-06 |
| Divergences terminologiques | `livrables/C0/registres/registre_divergences.md` | C0-06 |
| Lacunes | `livrables/C0/lacunes/liste_lacunes.md` | C0-07 |
| Questions ouvertes | `livrables/C0/lacunes/questions_questions.md` | C0-07 |
| Dépendances | `livrables/C0/lacunes/dependances_carte.md` | C0-07 |
| Sources historiques | `livrables/C0/sources_historique/sources_historique.md` | C0-08 |
| Statuts documentaires | `livrables/C0/stats_doc/tableau_statu.md` | C0-09 |
| État de référence | `livrables/C0/reference/référence_c0.md` | C0-10 (présent document) |
| Rapport C0 | `livrables/C0/rapport/rapport_C0.md` | C0-11 |
| Proposition périmètre C1 | `livrables/C0/perimetre-C1/proposition_perimetre_C1.md` | C0-12 |
| Réception de transition | `livrables/C0/transition/reception_transition.md` | C0 (réception) |

---

## 4. Métadonnées — résumé

45 documents inventoriés. Répartition des métadonnées manquantes :

| Champ | Nombre de documents sans valeur | Valeur portée |
|---|---|---|
| Version | 12 | `inconnu` / `non indiqué` |
| Date | 12 | `inconnu` / `non indiqué` |
| Statut documentaire | 18 | `inconnu` / `non vérifiable` |

Aucune valeur manquante n'est inventée.

---

## 5. Classification par nature — résumé

| Catégorie principale | Nombre | Pourcentage |
|---|---|---|
| Normatifs | 13 | 28,9 % |
| Opérationnels | 21 | 46,7 % |
| Explicatifs | 8 | 17,8 % |
| Historiques / sources | 3 | 6,7 % |
| **Total** | **45** | **100 %** |

4 documents portent une catégorie secondaire justifiée.

---

## 6. Décisions — résumé

| Type | Nombre | Exemple |
|---|---|---|
| Décision formellement validée (VALIDATOR) | 26 | D-VAL-A1 à A8, C13 à C34, D-001-HVG0 |
| Proposition (non validée) | 5 | D-PROP-001 à D-PROP-005 |
| Recommandation (non décision) | 7 | D-REC-A1 à A7 |
| Décision non confirmée | 3 | D-NC-D-001, C25, C29-bis |
| Décision historique (statut inconnu) | 2 | D-HIST-F3-10, D-HIST-Pilote |

Décision C0 en cours : `D-001-HVG0` = `GO_WITH_RESERVES` (VALIDATOR, 2026-11-24), 5 réserves R1-R5.

---

## 7. Registres — résumé

| Registre | Nombre de cas | Fichier |
|---|---|---|
| Doublons | 20 (D1 à D20) | `registre_doublons.md` |
| Contradictions | 25 (C1 à C25, dont C8 et C10 révisées) | `registre_contradictions.md` |
| Divergences terminologiques | 15 (T1 à T15) + 14 confusions (CF-1 à CF-14) | `registre_divergences.md` |

Signalement uniquement — aucune correction apportée.

---

## 8. Lacunes, questions, dépendances — résumé

| Domaine | Nombre | Fichier |
|---|---|---|
| Lacunes | 25 (L1 à L25) | `liste_lacunes.md` |
| Questions ouvertes | 24 (Q1 à Q24) | `questions_questions.md` |
| Dépendances | Documentées (document_map §9 + fiches + externalités) | `dependances_carte.md` |

Aucune réponse fournie, aucune dépendance résolue.

---

## 9. Sources historiques — résumé

| Source | Rôle | Niveau d'autorité déclaré | Autorité normative par défaut ? |
|---|---|---|---|
| `_sources/AKORIS_consolide.md` | Doctrine v1.0 | Niveau 2 | Non |
| `_sources/AKORIS_architecture_documentaire.md` | Plan d'architecture | Niveau 3 | Non |
| `_sources/akoris_documentation_builder.md` | Méthode de rédaction | Niveau 4 | Non |
| Pilote `demo_web - Copie` | Matériau v1 | Niveau 5 | Non |
| Pilote `demo_web` (allégé) | État et rapports v1 | Niveau 5 | Non |

Déclaration C0-08 : aucune autorité normative n'est attribuée par défaut aux sources historiques.

---

## 10. Statuts documentaires — résumé

| Statut | Nombre | Pourcentage |
|---|---|---|
| Approuvé | 3 | 6,7 % |
| Proposé | 24 | 53,3 % |
| Obsolète | 0 | 0 % |
| Retiré | 0 | 0 % |
| Non vérifié | 18 | 40,0 % |
| **Total** | **45** | **100 %** |

Les 3 documents approuvés sont les livrables V7 validés par le VALIDATOR le 2026-11-21 : `protocol/getting_started.md`, `reference/traceability_map.md`, `reference/versioning_policy.md`.

---

## 11. Réserves C0 (R1 à R5)

| Réserve | Intitulé | Gravité | Consigne C0 |
|---|---|---|---|
| R1 | Frontière C0-07 / C0-09 — distinction lacunes/questions/dépendances vs statuts documentaires | S2 | Maintenir sans chevauchement |
| R2 | Classification multi-catégories — catégorie principale + secondaires le cas échéant | S3 | Gestion par document, justification obligatoire |
| R3 | Attribution autorité sources historiques (C0-08) — vigilance contre attribution implicite | S2 | Ne pas attribuer d'autorité normative par défaut |
| R4 | État de référence vs state.json/state.md — distinction état de référence C0 (markdown) vs états opérationnels | S3 | État de référence markdown autonome dans `livrables/` |
| R5 | Fichiers .gitignore et ignorés — politique d'inclusion/exclusion à documenter | S3 | Signaler éléments inaccessibles avec justification |

---

## 12. État de référence figé

Cet état de référence est figé à la date du 2026-11-24. Il ne sera pas modifié ultérieurement. Toute évolution du corpus fera l'objet d'un nouvel état de référence dans le chantier C1 ou ultérieur.

**Preuves Git** :
- Commit initial : `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea`
- Branche : `dev_C0` (depuis `main` vérifié)
- Aucun fichier source modifié par rapport au commit initial

---
*Fin de l'état de référence C0. Gelé le 2026-11-24. Distinct de state.json et state.md.*