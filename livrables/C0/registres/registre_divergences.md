# C0-06 — Registre des divergences terminologiques

**Tâche** : C0-06 — Identifier doublons, contradictions, divergences  
**Sous-tâche** : Divergences terminologiques (même concept nommé différemment, ou même nom utilisé pour des concepts différents)  
**Date d'exécution** : 2026-11-24  
**Contrainte** : Signalement uniquement — aucune correction de document source

---

## 1. Méthode

Une divergence terminologique est un même concept nommé différemment dans plusieurs documents, ou un même terme employé avec des sens différents. Les divergences ci-dessous sont issues de l'examen du corpus, notamment `terminology.md` §8 (confusions à éviter), `versioning_policy.md` §4 (trois listes de catégories), et les contradictions C1/C2 de la cartographie.

---

## 2. Registre des divergences terminologiques

| ID | Concept | Terme A | Terme B | Documents impliqués | Nature de la divergence |
|---|---|---|---|---|---|
| T1 | Valeur de décision « go avec réserves » | `GO WITH RESERVES` (espaces) | `GO_WITH_RESERVES` (underscore) | `getting_started.md` (pilote) vs `AKORIS_consolide.md` §8.1, `decision_policy.md` §3 | Orthographe divergente ; A1 tranche en faveur de l'underscore |
| T2 | Nombre de valeurs de décision | 3 valeurs (pilote v1) | 5 valeurs (cadre v2) | `getting_started.md` 5.5 + pilote vs `decision_policy.md` §3 | Divergence de cardinalité ; A1 tranche 5 valeurs |
| T3 | Champ d'identification de transition | `token` (pilote v1) | `transition_id` (cadre v2) | `AKORIS_consolide.md` §7 (v1.0) vs `state_model.md` §6.4, `transition_policy.md` §2 | C22 : `token` déprécié, `transition_id` normatif |
| T4 | Activité « audit » | Audit de **préparation** (`readiness_review`) | Audit de **sprint** (`sprint_audit`) | `AKORIS_consolide.md` §11 (Bloc 08 vs §11) | Même mot, deux activités distinctes ; C19 tranche |
| T5 | Chemin du fichier d'entrée documentation | `README.md` (projet, installation) | `README.md` (documentation, point d'entrée) | `AKORIS_architecture_documentaire.md` §6.1 vs `akoris_documentation_builder.md` §6 | C6 : collision de nom de fichier ; A4 tranche |
| T6 | Nombre d'états de transition | 5 états (pilote) | 9 états (cadre v2) | `getting_started.md` 06.8 vs `AKORIS_consolide.md` §6.3 | C7 : `draft`, `consumed`, `expired`, `rejected` ajoutés par F3 |
| T7 | Structure de `state.json` | v1.0 plat | v2.0 imbriqué | `AKORIS_consolide.md` §7 vs `state_model.md` §6.1 | C3 : schémas incompatibles ; A2 tranche v2.0 |
| T8 | Chemins racine du socle | `governance/` | `protocol/` | `AKORIS_consolide.md` (governance/, 4 fichiers) vs `AKORIS_architecture_documentaire.md` (protocol/, 11 fichiers) | C5 : trois chemins concurrents (y compris `documentation/protocol/` de F1) |
| T9 | Liste des rôles | 3 agents + VALIDATOR | 4 rôles (ajout DOCUMENTATION BUILDER) | `AKORIS_consolide.md`, `getting_started.md` vs `akoris_documentation_builder.md` | C11 : A5 tranche 4 rôles, 4e documentaire hors boucle |
| T10 | Catégories de versions | Protocole, schéma, document, mandat (4 axes) | Protocole, profil, schéma, mandat, document (5 catégories) | `00_cartographie.md` §7 (ancienne mention « 4 axes ») vs `state_model.md` §8, `terminology.md` §11, `versioning_policy.md` §1 | Divergence de taxonomie ; A14/A15 tranchent A7 comme référence (5 catégories) |
| T11 | Éléments à versionner | Protocole, profils, prompts, modèles de rapports, schéma de `state.json`, décisions techniques, mandats, documents métier validés (8 éléments) | Protocole, profil, schéma, mandat, document (5 catégories) | `AKORIS_architecture_documentaire.md` §16 vs `versioning_policy.md` §1 | Divergence de portée ; A14 précise que F2 §16 est un inventaire historique, pas une catégorie A7 |
| T12 | Version du profil | Champ de version du profil dans `state.json` | Aucun champ de version du profil (version portée par l'en-tête du document `profile_*.md`) | `state.json` vs `versioning_policy.md` §2 (décision A10) | Divergence résolue par A10 : aucun champ ajouté |
| T13 | Reçu de transition | Pas de mécanisme de reçu (F3) | Reçu de transition obligatoire (`getting_started` 06.9, `agents.md` §7) | `AKORIS_consolide.md` §6.4 vs `getting_started.md` 06.9 | C8 : révisé, le reçu devient composant central (`transition_policy.md`) |
| T14 | Niveau des permissions | Principalement procédurales (environnement partagé) | Preuve technique partielle (frontmatter OpenCode) | `AKORIS_consolide.md` §12 vs `.opencode/agents/*.md` | C10 : révisé, `permission_policy.md` doit porter procédure de vérification |
| T15 | Emplacement des revues de préparation | `docs/governance/readiness/` (doctrinal) | `docs/governance/initialization_readiness_report.md` (pilote, historique) | `AKORIS_architecture_documentaire.md` §8.9 vs pilote | C13 : C13 appliqué, emplacement doctrinal tranché, rapport pilote conservé |

---

## 3. Confusions terminologiques à éviter (terminology §8)

Ces confusions sont documentées dans `terminology.md` §8 comme des distinctions à ne pas brouiller. Elles ne sont pas des divergences entre documents, mais des points de vigilance terminologique :

| # | À ne pas confondre | Avec | Pourquoi |
|---|---|---|---|
| CF-1 | Rapport | Preuve | Un rapport raconte ; une preuve démontre |
| CF-2 | Recommandation | Décision | Seul le VALIDATOR décide |
| CF-3 | Autorisation | Consommation | Autoriser n'est pas agir ; consommer n'est pas exécuter |
| CF-4 | Achèvement | Acceptation | Un résultat produit n'est pas un résultat accepté |
| CF-5 | Réserve | Anomalie | Une anomalie est un défaut ; une réserve est une condition acceptée |
| CF-6 | Profil | Implémentation | Le profil règle le niveau de contrôle ; l'implémentation fournit des moyens |
| CF-7 | Revue de préparation | Audit de sprint | Deux contrôles distincts, avant/après exécution (C19) |
| CF-8 | Changement | Correction | Une correction reste dans le périmètre ; un changement le modifie |
| CF-9 | Jeton | Preuve cryptographique | Un identifiant de transition est traçable, pas infalsifiable |
| CF-10 | Permission déclarée | Permission appliquée | Déclarer n'est pas imposer |
| CF-11 | `state.json` | `state.md` | L'un est la source, l'autre une vue générée |
| CF-12 | `NOT_CHECKED` | `PASS` | L'absence de contrôle n'est pas un succès |
| CF-13 | `declared_only` | Vérifié | Une déclaration n'est pas une vérification |
| CF-14 | Document de référence | Document produit | Une source alimente la documentation ; elle n'en fait pas partie |

---
*Fin du registre des divergences terminologiques. Signalement uniquement — aucune correction apportée. Total : 15 divergences terminologiques (T1 à T15) + 14 confusions terminologiques (CF-1 à CF-14).*