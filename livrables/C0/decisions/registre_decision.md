# C0-05 — Registre des décisions validées et preuves

**Tâche** : C0-05 — Identifier décisions validées et preuves  
**Date d'exécution** : 2026-11-24  
**Contrainte** : Pas de décision déduite comme validée ; uniquement éléments accessibles  
**5 types distingués** : décision formellement validée / proposition / recommandation / décision non confirmée / historique statut inconnu

---

## 1. Décisions formellement validées (VALIDATOR, tracé)

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
| D-001-HVG0 | `GO_WITH_RESERVES` pour le démarrage de C0 ; 5 réserves R1–R5 documentées et conservées. | 2026-11-24 | VALIDATOR | `state.json` (`last_decision`, `decision_id: D-001-HVG0`) ; `reception_transition.md` §1 ; `recu_transition_C0.md` §3 | Validé (HVG0) |

---

## 2. Propositions (non validées comme décisions)

| ID | Décision proposée | Auteur / origine | Preuve / référence | État |
|---|---|---|---|---|
| D-PROP-001 | Ordre interne de rédaction vague 1 : `terminology` → `governance_core` → `document_map` → `README` (inversion de l'ordre de la consigne). | DOCUMENTATION BUILDER | `00_cartographie.md` §9 (Vague 1) | Proposition (recommandation, pas décision) |
| D-PROP-002 | Table de transitions des états de projet (F3 §2.2 proposée). | DOCUMENTATION BUILDER / F2 | `state_model.md` §2.2 (statut RECOMMANDATION) | Proposition (non validée) |
| D-PROP-003 | Table de transitions des états de sprint (F3 §3.2 proposée). | DOCUMENTATION BUILDER / F2 | `state_model.md` §3.2 (statut RECOMMANDATION) | Proposition (non validée) |
| D-PROP-004 | Matrice des permissions complète (rôles × ressources × niveau). | DOCUMENTATION BUILDER | `permission_policy.md` §3 (statut RECOMMANDATION) | Proposition (non validée) |
| D-PROP-005 | Reprise dans le même rôle après interruption (continuation sous même `transition_id`). | DOCUMENTATION BUILDER | `recovery_policy.md` §5.2 (statut RECOMMANDATION) | Proposition (non validée) |

---

## 3. Recommandations (non décisions)

| ID | Recommandation | Auteur / origine | Preuve / référence | État |
|---|---|---|---|---|
| D-REC-A1 | 5 valeurs + underscore pour les valeurs de décision (cohérent avec HOLD et CANCELLED). | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A1) | Recommandation du BUILDER (arbitrée par A1 tranchée) |
| D-REC-A2 | v2.0 + reçu conservé (C8) pour l'arbitrage état/reçu. | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A2) | Recommandation du BUILDER (arbitrée par A2 tranchée) |
| D-REC-A3 | Profils activés ; pilote déclaré « non conforme, antérieur ». | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A3) | Recommandation du BUILDER (arbitrée par A3 tranchée) |
| D-REC-A4 | `documentation/` autonome ; README projet distinct. | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A4) | Recommandation du BUILDER (arbitrée par A4 tranchée) |
| D-REC-A5 | 4 rôles, le 4e étant documentaire et hors boucle d'exécution. | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A5) | Recommandation du BUILDER (arbitrée par A5 tranchée) |
| D-REC-A6 | `getting_started.md` v1 : matériau de rédaction, pas source d'autorité. | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A6) | Recommandation du BUILDER (arbitrée par A6 tranchée) |
| D-REC-A7 | 4 axes distincts de versionnement, voir C15. | BUILDER (00_cartographie) | `00_cartographie.md` §7.2 (A7) | Recommandation du BUILDER (arbitrée par A7 tranchée) |

---

## 4. Décisions non confirmées

| ID | Décision non confirmée | Origine | Preuve / référence | État |
|---|---|---|---|---|
| D-NC-D-001 | Plan global : cadre de travail proposé ; adoption et GO C0 restent à confirmer explicitement par le VALIDATOR. | `plan_de_consolidation.md` §6 (D-001) | `plan_de_consolidation.md` ligne 183 | Non confirmée (GO C0 à confirmer explicitement) |
| D-NC-C25 | Échelle de risque chiffrée — aucune n'existe. | `audit_policy.md` §15.2 | `audit_policy.md` §15.2 (C25) | Non confirmé (INCONNU) |
| D-NC-C29-bis | Protection technique effective de `main` — non certifiée. | `agent_permissions.md` §7 | `agent_permissions.md` §7 (C29) | Non confirmé (`unknown`) |

---

## 5. Décisions historiques (statut inconnu / non vérifiable)

| ID | Décision historique | Origine | Preuve / référence | Statut |
|---|---|---|---|---|
| D-HIST-F3-10 | 10 « décisions structurantes retenues » énumérées dans F3 §19 sans identifiant ni registre. | `AKORIS_consolide.md` §19 | `00_cartographie.md` §5.3 (C18) | Statut inconnu (contradiction avec le principe 6 de F3 — traçabilité) |
| D-HIST-Pilote | Décisions du projet pilote `demo_web` (contrats, permissions, transitions, reçu). | `C:\demo_web - Copie\agents.md` | `00_cartographie.md` §2.2 ; `document_map.md` §5 | Statut inconnu (niveau 5, non doctrinal) |

---

## 6. Preuves associées aux décisions

| Preuve | Type | Référence | Décisions concernées |
|---|---|---|---|
| Commit initial `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea` | Commit Git | `git log` | D-001 (plan de consolidation) |
| `state.json` (`last_decision`) | État opérationnel | `state.json` lignes 52-67 | D-001-HVG0 (GO_WITH_RESERVES) |
| `reception_transition.md` | Reçu de transition | `livrables/C0/transition/reception_transition.md` | D-001-HVG0 |
| `recu_transition_C0.md` | Reçu de transition | `livrables/C0/transition/recu_transition_C0.md` | D-001-HVG0 |
| `plan_de_consolidation.md` §6 | Journal des décisions | `plan_de_consolidation.md` ligne 183 | D-001 |
| `00_cartographie.md` §7 | Décisions tranchées et ouvertes | `00_cartographie.md` lignes 223-237 | D-VAL-A1 à A8 |
| `changelog.md` | Historique centralisé | `changelog.md` §1, §2 | Toutes les décisions A1-A8, C13-C31 |
| `reference/state.schema.json` | Schéma technique | `reference/state.schema.json` | D-VAL-A2, D-VAL-C28 |
| `reference/versioning_policy.md` §5 | Politique de versionnement | `reference/versioning_policy.md` lignes 116-136 | D-VAL-A15, D-VAL-A10, D-VAL-A14, D-VAL-A09 |

---
*Fin de C0-05. Registre figé à la date d'exécution : 2026-11-24. Nombre de décisions formellement validées : 26 (dont D-001-HVG0). Propositions : 5. Recommandations : 7. Non confirmées : 3. Historiques statut inconnu : 2.*