# C1-D — Registre des décisions (consolidation C0 + nouvelles C1)

**Chantier** : C1 — Consolidation normative et documentaire  
**Tâche** : C1-D — Registres décisions : consolider les décisions C0, enregistrer nouvelles décisions, lier preuves  
**Transition** : TR-2026-0002 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C1-consolide-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C1` (alignée sur `main`, intègre les 10 commits C0)  
**Contrainte** : Pas de décision déduite comme validée ; uniquement éléments accessibles  
**5 types distingués** : décision formellement validée / proposition / recommandation / décision non confirmée / historique statut inconnu

---

## 1. Vérification état Git (prérequis C1-D)

| Vérification | Résultat | Preuve |
|---|---|---|
| Branche courante | `dev_C1` | `git branch` |
| Alignement avec `main` | `dev_C1` = `main` (commit `fbfc5d1`) | `git log --oneline` |
| Intégration C0 dans `main` | 10 commits C0 présents sur `main` | `git log --oneline main` |
| C1-A, C1-B, C1-C terminés | Commits `7da7ebc`, `cc6ebc5`, `fbfc5d1` | `git log --oneline -3` |
| Reçu de transition C1 déposé | `livrables/C1/transition/recu_transition_C1.md` | Commit `7da7ebc` |

---

## 2. Objectif de C1-D

Ce registre consolide :

1. **Toutes les décisions identifiées en C0** (registre C0-05), avec leurs preuves
2. **La décision C1 nouvelle** : D-001-HVG0-B (`GO_WITH_RESERVES` pour la transition C0 → C1)
3. Le lien de chaque décision à sa preuve (commit, document, jeton, état)
4. La distinction des 5 types de décisions

---

## 3. Décisions formellement validées (VALIDATOR, tracé)

Ces décisions ont été prises par le VALIDATOR, avec auteur, date et preuve tracés.

| ID | Décision | Date | Auteur | Preuve / référence | État |
|---|---|---|---|---|---|
| D-VAL-A1 | Cinq valeurs de décision normatives (`GO`, `GO_WITH_RESERVES`, `NO_GO`, `HOLD`, `CANCELLED`), orthographe à underscore. Formes `GO WITH RESERVES` / `NO GO` du pilote v1 abandonnées. | 2026-11-20 | VALIDATOR | `00_cartographie.md` §7.1 (A8) ; `decision_policy.md` §3 ; `terminology.md` §4, §11 ; `README.md` §11 | Tranché |
| D-VAL-A2 | `state.json` sérialisation v2.0 (structure imbriquée) est la structure normative AKORIS ; le pilote v1.0 est un écart historique. | 2026-11-20 | VALIDATOR | `state_model.md` §0, §6.1 ; `reference/state.schema.json` ; `terminology.md` §11 | Tranché |
| D-VAL-A3 | Couche profils activée ; le pilote déclaré « non conforme, antérieur ». | 2026-11-20 | VALIDATOR | `00_cartographie.md` §7.2 ; `changelog.md` V1 | Tranché |
| D-VAL-A4 | Chemin racine canonique : `documentation/` autonome ; README projet distinct. | 2026-11-20 | VALIDATOR | `00_cartographie.md` §7.2 ; `README.md` §11 | Tranché |
| D-VAL-A5 | 4 rôles (3 agents + VALIDATOR + DOCUMENTATION BUILDER rôle documentaire auxiliaire hors boucle d'exécution). | 2026-11-20 | VALIDATOR | `00_cartographie.md` §7.2 ; `README.md` §5 ; `terminology.md` §2, §11 | Tranché |
| D-VAL-A6 | Statut de `getting_started.md` v1 : matériau de rédaction, pas source d'autorité. | 2026-11-20 | VALIDATOR | `00_cartographie.md` §7.2 ; `audit_policy.md` §4.1 ; `terminology.md` §12 source GS1 | Tranché |
| D-VAL-A7 | 5 catégories de versions distinctes (protocole, profil, schéma, mandat, document). | 2026-11-20 | VALIDATOR | `00_cartographie.md` §7.2 ; `state_model.md` §8 ; `versioning_policy.md` §1 ; `terminology.md` §11 | Tranché |
| D-VAL-A8 | Socle AKORIS agnostique de l'outil + OpenCode comme implémentation de référence documentée séparément. | 2026-11-20 | VALIDATOR | `00_cartographie.md` §7.1 ; `README.md` §10, §33 | Tranché |
| D-VAL-C13 | Emplacement doctrinal de la `readiness_review` : `docs/governance/readiness/` ; rapport historique du pilote conservé. | 2026-11-20 | VALIDATOR | `audit_policy.md` §2, §6.3 ; `document_map.md` §6 ; `terminology.md` §11 | Tranché |
| D-VAL-C19 | `readiness_review` et `sprint_audit` sont deux contrôles distincts et non substituables. | 2026-11-20 | VALIDATOR | `audit_policy.md` §2 ; `terminology.md` §4, §11 ; `traceability_map.md` §3.7 | Tranché |
| D-VAL-C22 | `transition_id` remplace `token` (déprécié) dans `state.json` et la politique des transitions. | 2026-11-20 | VALIDATOR | `state_model.md` §6.4 (C22 dépréciation) ; `transition_policy.md` §2 (C22 nommage) ; `terminology.md` §9 | Tranché |
| D-VAL-C24 | Le mécanisme de reçu est un composant central du dispositif, pas une hypothèse. | 2026-11-20 | VALIDATOR | `00_cartographie.md` §5.4 (révision C8) ; `transition_policy.md` §0 | Tranché |
| D-VAL-C26 | Reçu d'ORCHESTRATOR déposé dans `docs/governance/receipts/` par le destinataire lui-même. | 2026-11-20 | VALIDATOR | `transition_policy.md` §5.2, §5.7 ; `audit_policy.md` §13 ; `document_map.md` §6 | Tranché |
| D-VAL-C27 | Aucune durée numérique par défaut pour l'expiration des transitions ; durée selon mandat et profil. | 2026-11-20 | VALIDATOR | `transition_policy.md` §7 ; `terminology.md` §11 | Tranché |
| D-VAL-C28 | `reference/state.schema.json` créé comme Schéma AKORIS v2.0. | 2026-11-20 | VALIDATOR | `state_model.md` §6.1, §6.3 (C28) ; `reference/state.schema.json` | Tranché |
| D-VAL-C29 | Protection de `main` maintenue `unknown` ; T5 préparé, non exécuté. | 2026-11-20 | VALIDATOR | `agent_permissions.md` §7 ; `audit_policy.md` §11 ; `terminology.md` §11 | Tranché |
| D-VAL-C30 | Une transition `consumed` n'est pas réutilisable et ne revient pas à `authorized`. | 2026-11-20 | VALIDATOR | `audit_policy.md` §7 (règle C30) ; `state_model.md` §4.2 | Tranché |
| D-VAL-C31 | Un `HOLD` laisse le changement en `awaiting_decision` avec `decision = HOLD`. | 2026-11-20 | VALIDATOR | `audit_policy.md` §13 ; `recovery_policy.md` §13 | Tranché |
| D-VAL-C34 | L'exigence de rollback est déterminée par le risque réel, pas par le seul profil. | 2026-11-20 | VALIDATOR | `recovery_policy.md` §10.2 ; `terminology.md` §11 | Tranché |
| D-VAL-A15 | Règles AKORIS prospectives : SemVer indépendant pour protocole et schéma ; révision simple pour les documents ; incrémentation événementielle. | 2026-11-21 | VALIDATOR | `versioning_policy.md` §5 (A15 approuvée) | Décidé (prospectif) |
| D-VAL-A10 | Aucun champ de version du profil ajouté à `state.json`, au modèle d'état ni au schéma. | 2026-11-21 | VALIDATOR | `versioning_policy.md` §2 (décision A10) | Décidé |
| D-VAL-A14 | A7 demeure la taxonomie de référence à cinq catégories ; aucune unification des listes de `CART` et `F2` requise. | 2026-11-21 | VALIDATOR | `versioning_policy.md` §4 (A14 précisé) | Décidé |
| D-VAL-A09 | Rôles des sources dans `versioning_policy.md` : `CART` et `F2` marqués `NON DÉTERMINÉ` (pas de dépendance normative). | 2026-11-21 | VALIDATOR | `versioning_policy.md` §2 (A09 précisé) | Décidé |
| D-001-HVG0 | `GO_WITH_RESERVES` pour le démarrage de C0 ; 5 réserves R1–R5 documentées et conservées. | 2026-11-24 | VALIDATOR | `state.json` (`last_decision`, `decision_id: D-001-HVG0`) ; `livrables/C0/transition/reception_transition.md` §1 ; `livrables/C0/transition/recu_transition_C0.md` §3 | Validé (HVG0) |
| D-001-HVG0-B | `GO_WITH_RESERVES` pour la transition C0 → C1 ; 5 réserves R1–R5 maintenues ; 10 actions prioritaires identifiées. | 2026-11-24 | VALIDATOR | `state.json` (`last_decision`, `decision_id: D-001-HVG0-B`, `transition.decision_id`) ; `livrables/C1/transition/recu_transition_C1.md` §3 | Validé (HVG0-B) |

**Nombre de décisions formellement validées : 28** (26 de C0 + D-001-HVG0 + D-001-HVG0-B)

---

## 4. Propositions (non validées comme décisions)

Ces propositions ont été émises par le DOCUMENTATION BUILDER ou d'autres acteurs, mais n'ont pas été validées par le VALIDATOR comme décisions formelles.

| ID | Décision proposée | Auteur / origine | Preuve / référence | État |
|---|---|---|---|---|
| D-PROP-001 | Ordre interne de rédaction vague 1 : `terminology` → `governance_core` → `document_map` → `README` (inversion de l'ordre de la consigne). | DOCUMENTATION BUILDER | `00_cartographie.md` §9 (Vague 1) | Proposition (recommandation, pas décision) |
| D-PROP-002 | Table de transitions des états de projet (F3 §2.2 proposée). | DOCUMENTATION BUILDER / F2 | `state_model.md` §2.2 (statut RECOMMANDATION) | Proposition (non validée) |
| D-PROP-003 | Table de transitions des états de sprint (F3 §3.2 proposée). | DOCUMENTATION BUILDER / F2 | `state_model.md` §3.2 (statut RECOMMANDATION) | Proposition (non validée) |
| D-PROP-004 | Matrice des permissions complète (rôles × ressources × niveau). | DOCUMENTATION BUILDER | `permission_policy.md` §3 (statut RECOMMANDATION) | Proposition (non validée) |
| D-PROP-005 | Reprise dans le même rôle après interruption (continuation sous même `transition_id`). | DOCUMENTATION BUILDER | `recovery_policy.md` §5.2 (statut RECOMMANDATION) | Proposition (non validée) |

**Nombre de propositions : 5** (toutes de C0, aucune nouvelle proposition C1 à ce stade)

---

## 5. Recommandations (non décisions)

Ces recommandations ont été émises par le BUILDER ou d'autres acteurs, mais ne sont pas des décisions VALIDATOR.

| ID | Recommandation | Auteur / origine | Preuve / référence | État |
|---|---|---|---|---|
| D-REC-A1 | 5 valeurs + underscore pour les valeurs de décision (cohérent avec HOLD et CANCELLED). | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A1) | Recommandation du BUILDER (arbitrée par A1 tranchée) |
| D-REC-A2 | v2.0 + reçu conservé (C8) pour l'arbitrage état/reçu. | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A2) | Recommandation du BUILDER (arbitrée par A2 tranchée) |
| D-REC-A3 | Profils activés ; pilote déclaré « non conforme, antérieur ». | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A3) | Recommandation du BUILDER (arbitrée par A3 tranchée) |
| D-REC-A4 | `documentation/` autonome ; README projet distinct. | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A4) | Recommandation du BUILDER (arbitrée par A4 tranchée) |
| D-REC-A5 | 4 rôles, le 4e étant documentaire et hors boucle d'exécution. | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A5) | Recommandation du BUILDER (arbitrée par A5 tranchée) |
| D-REC-A6 | `getting_started.md` v1 : matériau de rédaction, pas source d'autorité. | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A6) | Recommandation du BUILDER (arbitrée par A6 tranchée) |
| D-REC-A7 | 4 axes distincts de versionnement, voir C15. | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A7) | Recommandation du BUILDER (arbitrée par A7 tranchée) |

**Nombre de recommandations : 7** (toutes de C0, aucune nouvelle recommandation C1 à ce stade)

---

## 6. Décisions non confirmées

Ces décisions ont été identifiées mais ne sont pas confirmées par le VALIDATOR.

| ID | Décision non confirmée | Origine | Preuve / référence | État |
|---|---|---|---|---|
| D-NC-D-001 | Plan global : cadre de travail proposé ; adoption et GO C0 restent à confirmer explicitement par le VALIDATOR. | `plan_de_consolidation.md` §6 (D-001) | `plan_de_consolidation.md` ligne 183 | Non confirmée (GO C0 à confirmer explicitement) |
| D-NC-C25 | Échelle de risque chiffrée — aucune n'existe. | `audit_policy.md` §15.2 | `audit_policy.md` §15.2 (C25) | Non confirmé (INCONNU) |
| D-NC-C29-bis | Protection technique effective de `main` — non certifiée. | `agent_permissions.md` §7 | `agent_permissions.md` §7 (C29) | Non confirmé (`unknown`) |

**Nombre de décisions non confirmées : 3** (toutes de C0, aucune nouvelle non-confirmation C1 à ce stade)

---

## 7. Décisions historiques (statut inconnu / non vérifiable)

| ID | Décision historique | Origine | Preuve / référence | Statut |
|---|---|---|---|---|
| D-HIST-F3-10 | 10 « décisions structurantes retenues » énumérées dans F3 §19 sans identifiant ni registre. | `AKORIS_consolide.md` §19 | `00_cartographie.md` §5.3 (C18) | Statut inconnu (contradiction avec le principe 6 de F3 — traçabilité) |
| D-HIST-Pilote | Décisions du projet pilote `demo_web` (contrats, permissions, transitions, reçu). | `C:\demo_web - Copie\agents.md` | `00_cartographie.md` §2.2 ; `document_map.md` §5 | Statut inconnu (niveau 5, non doctrinal) |

**Nombre de décisions historiques statut inconnu : 2** (toutes de C0, aucune nouvelle décision historique C1 à ce stade)

---

## 8. Répartition globale des décisions

| Type | Nombre C0 | Nombre C1 (nouveau) | Total |
|---|---|---|---|
| Décision formellement validée | 26 | 2 (D-001-HVG0, D-001-HVG0-B) | 28 |
| Proposition | 5 | 0 | 5 |
| Recommandation | 7 | 0 | 7 |
| Décision non confirmée | 3 | 0 | 3 |
| Décision historique (statut inconnu) | 2 | 0 | 2 |
| **Total** | **43** | **2** | **45** |

---

## 9. Preuves associées aux décisions

| Preuve | Type | Référence | Décisions concernées |
|---|---|---|---|
| Commit initial `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea` | Commit Git | `git log` | D-001 (plan de consolidation) |
| `state.json` (`last_decision`) | État opérationnel | `state.json` lignes 52-66 | D-001-HVG0, D-001-HVG0-B |
| `state.json` (`transition.decision_id`) | État opérationnel | `state.json` ligne 46 | D-001-HVG0-B |
| `reception_transition.md` (C0) | Reçu de transition | `livrables/C0/transition/reception_transition.md` §1 | D-001-HVG0 |
| `recu_transition_C0.md` (C0) | Reçu de transition | `livrables/C0/transition/recu_transition_C0.md` §3 | D-001-HVG0 |
| `recu_transition_C1.md` (C1) | Reçu de transition | `livrables/C1/transition/recu_transition_C1.md` §3 | D-001-HVG0-B |
| `plan_de_consolidation.md` §6 | Journal des décisions | `plan_de_consolidation.md` ligne 183 | D-001 |
| `00_cartographie.md` §7 | Décisions tranchées et ouvertes | `00_cartographie.md` lignes 223-237 | D-VAL-A1 à A8 |
| `changelog.md` | Historique centralisé | `changelog.md` §1, §2 | Toutes les décisions A1-A8, C13-C31 |
| `reference/state.schema.json` | Schéma technique | `reference/state.schema.json` | D-VAL-A2, D-VAL-C28 |
| `reference/versioning_policy.md` §5 | Politique de versionnement | `reference/versioning_policy.md` lignes 116-136 | D-VAL-A15, D-VAL-A10, D-VAL-A14, D-VAL-A09 |
| `decision_policy.md` §3 | Politique de décision | `decision_policy.md` §3 | D-VAL-A1, toutes les décisions VALIDATOR |
| `permission_policy.md` §7 | Politique de permission | `permission_policy.md` §7 | D-VAL-C29 |
| `agent_permissions.md` | Constat OpenCode | `implementations/opencode/agent_permissions.md` | D-NC-C29-bis |

---

## 9. Décisions émergentes attendues dans la suite de C1

Les décisions suivantes sont attendues dans la suite de C1 mais ne sont pas encore prises (à ne pas confondre avec des décisions déjà validées) :

| ID prévisionnel | Décision attendue | Contexte | Acteur décisionnel |
|---|---|---|---|
| D-C1-HVG1 | Décision finale sur C1 (GO / NO_GO / GO_WITH_RESERVES / HOLD / CANCELLED) | Après exécution C1 et audit | VALIDATOR (HVG1) |
| D-C1-M1 | Validation du schéma `state.schema.json` (action M1) | Validation JSON Schema contre `state.json` | À déterminer (test technique) |
| D-C1-M3 | Protection de `main` certifiée ou non (action M3, test T5) | Test de fusion/push non autorisé vers `main` | À déterminer (test technique) |

Ces décisions ne figurent pas dans le registre ci-dessus car elles ne sont pas encore prises.

---
*Fin de C1-D. Registre consolidé : 45 décisions (28 validées, 5 propositions, 7 recommandations, 3 non confirmées, 2 historiques). D-001-HVG0-B ajouté comme décision C1 nouvelle. Aucune décision déduite comme validée ; uniquement éléments accessibles.*