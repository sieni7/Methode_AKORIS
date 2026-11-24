# C0-07 — Questions ouvertes

**Tâche** : C0-07 — Identifier lacunes, questions et dépendances  
**Sous-tâche** : Questions ouvertes (sur le sens ou l'application de certaines règles)  
**Date d'exécution** : 2026-11-24  
**Contrainte** : Ne pas répondre aux questions — les repérer uniquement

---

## 1. Méthode

Une question ouverte est une interrogation sur le sens, l'application ou l'interprétation d'une règle, qui n'est pas tranchée dans le corpus. Aucune réponse n'est apportée.

---

## 2. Questions ouvertes issues de l'arbitrage A1-A7 (00_cartographie §7.2)

| # | Question | Contexte | Document source |
|---|---|---|---|
| Q1 | Valeurs de décision : 3 (v1) ou 5 (F3) ? Orthographe canonique ? | Bloque `decision_policy.md` et les modèles | `00_cartographie.md` §7.2 (A1) |
| Q2 | `state.json` cible : v1.0 plat ou v2.0 imbriqué ? Consommation par champ `consumed_at` ou par reçu ? | Bloque `state_model.md`, `transition_policy.md` | `00_cartographie.md` §7.2 (A2) |
| Q3 | Couche profils : activée, différée ou abandonnée ? | Bloque `profile_*.md`, `governance_core.md` | `00_cartographie.md` §7.2 (A3) |
| Q4 | Chemin racine canonique et nom du README de documentation | Bloque `document_map.md`, tous les liens | `00_cartographie.md` §7.2 (A4) |
| Q5 | Rôles : 3 agents + VALIDATOR, ou 4 avec DOCUMENTATION BUILDER ? | Bloque `governance_core.md`, `prompts/` | `00_cartographie.md` §7.2 (A5) |
| Q6 | Statut de `getting_started.md` v1 : source, matériau ou legacy ? | Bloque tout le contenu opérationnel | `00_cartographie.md` §7.2 (A6) |
| Q7 | Schéma de versionnement (protocole / schéma / doc / mandat) | Bloque `versioning_policy.md`, `changelog.md` | `00_cartographie.md` §7.2 (A7) |

---

## 3. Questions ouvertes issues des points ouverts du corpus

| # | Question | Contexte | Document source |
|---|---|---|---|
| Q8 | Quelle est l'échelle de risque chiffrée (C25) ? | Aucune échelle définie ; le choix de profil reste qualitatif | `audit_policy.md` §15.2 ; `document_map.md` §11 |
| Q9 | Quelle règle de quorum ou de délégation s'applique aux décisions ? | Aucune règle définie | `decision_policy.md` §12 |
| Q10 | Quelle décision prendre en cas d'absence prolongée du VALIDATOR ? | Le cadre suppose sa disponibilité | `decision_policy.md` §12 |
| Q11 | Quelle procédure de migration pilote v1.0 → Norme v2.0 ? | Aucune procédure décrite | `versioning_policy.md` §5 (A16 différé) |
| Q12 | Quelle est la durée de conservation des preuves et reçus ? | Non définie | `transition_policy.md` §10 |
| Q13 | Quels sont les RTO / RPO pour la reprise après incident ? | Aucun défini | `recovery_policy.md` §14 |
| Q14 | Quel est le format d'identifiant des exigences et des tâches ? | Aucun format normatif | `traceability_map.md` §7 |
| Q15 | Quel est le statut exact de `00_cartographie.md` (PROPOSITION vs TRAVAIL) ? | En-tête vs `document_map.md` §3 | `00_cartographie.md` en-tête ; `document_map.md` §3 |
| Q16 | Pourquoi l'en-tête de `document_map.md` reste fixé à `Version 0.4` malgré l'évolution du compteur ? | Décision explicite I4 | `changelog.md` §3.1 (I4) |
| Q17 | Quelle est la relation exacte entre un état `state.json` et une version donnée du document `profile_*.md` ? | Non modélisée dans le schéma | `versioning_policy.md` §2 (décision A10) |
| Q18 | Les tests T1 à T5 seront-ils exécutés, et avec quel résultat ? | Aucun test exécuté à ce jour | `agent_permissions.md` §6 ; `audit_policy.md` §12.1 |
| Q19 | La protection technique de `main` sera-t-elle vérifiée (T5) ? | Test préparé, non exécuté | `agent_permissions.md` §7 (C29) |

---

## 4. Questions ouvertes issues des arbitrages non tranchés

| # | Question | Contexte | Document source |
|---|---|---|---|
| Q20 | Divergence interne de `state_model.md` (§10 vs §6.1/§6.3 sur l'existence du schéma de validation) — quel texte prévaut ? | Divergence signalée, non tranchée | `traceability_map.md` §7 ; `state_model.md` §10 |
| Q21 | Unification des trois listes de catégories de versions (A7 : 5 ; CART : 4 axes ; F2 : 5 versions + 8 éléments) — une unification est-elle nécessaire ? | A14 précise qu'aucune unification n'est requise | `versioning_policy.md` §4 (A14) |
| Q22 | Le rôle de `00_cartographie.md` et de `AKORIS_architecture_documentaire.md` (F2) dans `versioning_policy.md` est-il normatif ou uniquement informatif ? | Marqués `NON DÉTERMINÉ` | `versioning_policy.md` §2 (A09) |

---

## 5. Questions issues des points « À ARBITRER » de `00_cartographie`

| # | Question | Référence | Document source |
|---|---|---|---|
| Q23 | Sort des trois sources F1/F2/F3 : conservation à la racine ou déplacement vers `documentation/_sources/` ? | §13 de la cartographie (étape 5) | `00_cartographie.md` §13 (déjà appliqué par A13) |
| Q24 | Maquette de consigne C20 : l'arborescence incomplète est-elle confirmée corrigée ? | §8.1 de la cartographie | `00_cartographie.md` §8.1 |

---
*Fin des questions ouvertes. Aucune réponse fournie. Total : 24 questions (Q1 à Q24).*