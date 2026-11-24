# C0-07 — Liste des lacunes

**Tâche** : C0-07 — Identifier lacunes, questions et dépendances  
**Sous-tâche** : Lacunes (sujets non couverts par le corpus)  
**Date d'exécution** : 2026-11-24  
**Contrainte** : Aucune réponse fournisse — repérage uniquement

---

## 1. Méthode

Une lacune est un sujet, un document, un registre ou un mécanisme qui devrait exister selon le cadre AKORIS mais qui est absent du corpus. Aucune réponse n'est apportée ; les lacunes sont uniquement répertoriées.

---

## 2. Liste des lacunes

| # | Sujet de la lacune | Document ou zone concerné | Nature de l'absence | Contexte |
|---|---|---|---|---|
| L1 | Registre des décisions (`decision_log.md`) | `reference/decision_log.md` — **fichier planifié, non créé** | Document annoncé mais absent | `decision_policy.md` §11 : « fichier planifié, non créé » ; `traceability_map.md` §3.5 : registre à arbitrer |
| L2 | Schéma de validation de `state.json` reproduit avec un validateur nommé | `reference/state.schema.json` — schéma existe mais validation non exécutée | Preuve de validation manquante | `state_model.md` §10 : « validation JSON Schema n'a pas été reproduite avec un validateur nommé (NON VÉRIFIÉE) » |
| L3 | Procédure de migration pilote v1.0 → Norme v2.0 | Aucun document de migration | Procédure absente | `versioning_policy.md` §5 : « Procédure de migration... À ARBITRER — décision humaine requise (A16 différé) » |
| L4 | Matrice complète des permissions (rôles × ressources × niveau) | `permission_policy.md` §3 — matrice proposée, non exhaustive | Matrice incomplète | `permission_policy.md` §3 : statut RECOMMANDATION ; sources ne fournissent pas la matrice complète |
| L5 | Table de transition des états de projet (état × événement → état cible × acteur) | `state_model.md` §2.2 — table proposée, statut RECOMMANDATION | Table non validée | `state_model.md` §2.2 : « Statut : RECOMMANDATION... doit être validée » |
| L6 | Table de transition des états de sprint (état × événement → état cible × acteur) | `state_model.md` §3.2 — table proposée, statut RECOMMANDATION | Table non validée | `state_model.md` §3.2 : « Même réserve que §2.2 » |
| L7 | Seuils quantitatifs de gravité d'anomalie (S0-S3) | Aucune échelle définie | Seuil manquant | `decision_policy.md` §12 : « Aucun seuil quantitatif de gravité — INCONNU — la qualification reste humaine » |
| L8 | Règle de quorum ou de délégation de décision | Aucun document | Mécanisme absent | `decision_policy.md` §12 : « Aucune règle de quorum ou de délégation — INCONNU » |
| L9 | Décision en cas d'absence prolongée du VALIDATOR | Aucun document | Procédure absente | `decision_policy.md` §12 : « Décision en cas d'absence prolongée du VALIDATOR — INCONNU » |
| L10 | Échelle de risque chiffrée (C25) | Aucun document | Échelle absente | `audit_policy.md` §15.2 : C25 — « aucune n'existe » ; `README.md` §11 |
| L11 | Tests T1 à T5 exécutés | Aucun test exécuté | Preuves d'exécution absentes | `agent_permissions.md` §6 : T1 à T5 NON EXÉCUTÉ ; `audit_policy.md` §12.1 |
| L12 | Preuve technique de protection de `main` | Aucun test concluant | Protection non certifiée | `agent_permissions.md` §7 : C29 — protection de `main` maintenue `unknown` |
| L13 | Registre des changements (`docs/governance/changes/`) | Dossier non créé dans le périmètre documentaire | Registre absent | `change_control.md` §10 : emplacement `docs/governance/changes/` ; `CC` §12 : « non créé dans le pilote » |
| L14 | Registre des incidents (`docs/governance/incidents/`) | Dossier non créé | Registre absent | `recovery_policy.md` §14 : « `docs/governance/incidents/` non créé dans le pilote » |
| L15 | Dossier de revues de préparation (`docs/governance/readiness/`) | Dossier non créé dans ce dépôt | Dossier absent | `audit_policy.md` §2 : emplacement doctrinal `docs/governance/readiness/` (C13) |
| L16 | Dossier des reçus ORCHESTRATOR (`docs/governance/receipts/`) | Dossier non créé dans ce dépôt | Dossier absent | `transition_policy.md` §5.2 (C26) : emplacement du reçu ORCHESTRATOR |
| L17 | Identifiants d'exigence et de tâche | Aucun format normatif | Format manquant | `traceability_map.md` §7 : « Aucun format normatif dans les sources pour les identifiants d'exigence ou de tâche » |
| L18 | Durée de conservation des preuves et reçus | Aucune durée définie | Règle absente | `transition_policy.md` §10 : « Durée de conservation non définie (INCONNU) » |
| L19 | RTO / RPO (objectifs de reprise) | Aucune définition | Indicateurs absents | `recovery_policy.md` §14 : « Aucun RTO / RPO défini — INCONNU » |
| L20 | Modèle de rapport de dette (`debt_report_template.md`) | Absent de la cible des 7 modèles | Modèle manquant | `00_cartographie.md` §6.2 : `templates/debt_report_template.md` existe dans le pilote, absent de la cible |
| L21 | Document de sélection de profil (`profile_selection.md`) | Absent de la cible | Document manquant | `00_cartographie.md` §8.3 : `protocol/profile_selection.md` utile mais non créé |
| L22 | Correspondance manuel v1 → architecture cible (`pilot_mapping.md`) | Absent | Document manquant | `00_cartographie.md` §6.2 : `reference/pilot_mapping.md` recommandé |
| L23 | Fichiers avec version et date manquantes (F2, F1) | `_sources/AKORIS_architecture_documentaire.md`, `_sources/akoris_documentation_builder.md` | Métadonnées absentes | `versioning_policy.md` §5 : « Dates et versions sur F2 et F1 — INCONNU — constat historique, non corrigé » |
| L24 | `.gitignore` | Aucun fichier à la racine | Politique d'inclusion/exclusion absente | Constat C0-02 : absence de `.gitconfirmé` ; réserve R5 |
| L25 | Preuve de refus technique (tests T1-T5) | Aucun rapport de refus | Preuve absente | `agent_permissions.md` §5.4 : « Aucun rapport du pilote ne contient de trace montrant qu'une édition a été refusée » |

---
*Fin de la liste des lacunes. Aucune réponse fournie. Total : 25 lacunes (L1 à L25).*