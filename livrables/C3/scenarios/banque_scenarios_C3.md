# C3 — C3.2 : Banque de scénarios d'expérimentation

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.2 — Décrire chaque scénario : précondition, acteur, action, attendu, observé, preuve, écart et impact  
**Transition** : TR-2026-0004 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C3-expérimentation-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)  
**Contrainte** : Scénarios uniquement dans `/app` ; pas de modification du method AKORIS sans HVG3 ; aucun secret (GC-33) ; recherche de secrets avant commit (GC-34)

---

## 1. Méthode

Chaque scénario est décrit avec les champs suivants :

| Champ | Signification |
|---|---|
| **Précondition** | État requis avant l'exécution du scénario |
| **Acteur** | Rôle qui exécute l'action (BUILDER, ORCHESTRATOR, AUDITOR, VALIDATOR) |
| **Action** | Action concrète réalisée dans le scénario |
| **Attendu** | Résultat attendu selon le method AKORIS |
| **Observé** | Résultat réellement constaté lors de l'exécution (à remplir pendant C3.8) |
| **Preuve** | Élément vérifiable produit à l'appui (commit, sortie de commande, résultat de test, etc.) |
| **Écart** | Différence entre attendu et observé (à remplir pendant C3.9) |
| **Impact** | Conséquence de l'écart sur le method AKORIS ou l'expérimentation |

**Statut des scénarios non encore exécutés** : `observé = "Non encore exécuté"`, `écart = "Non déterminé"`, `impact = "Non déterminé"`.

---

## 2. Scénarios de démonstration

Ces scénarios montrent le method AKORIS en action.

| # | ID | Précondition | Acteur | Action | Attendu | Observé | Preuve | Écart | Impact |
|---|---|---|---|---|---|---|---|---|---|
| D1 | SCN-DEMO-01 | `state.json` existe, `main` intègre C0+C1+C2, branche `dev_C3` active | BUILDER | Créer un fichier de test dans `/app` et le commiter sur `dev_C3` | Fichier créé et commit traçable | Non encore exécuté | Commit Git | Non déterminé | Non déterminé |
| D2 | SCN-DEMO-02 | `state.json` avec `transition_id: TR-2026-0004` autorisé | BUILDER | Déposer un rapport d'expérimentation dans `livrables/C3/rapport/` | Rapport déposé et traçable | Non encore exécuté | Fichier de rapport | Non déterminé | Non déterminé |
| D3 | SCN-DEMO-03 | Branche `dev_C3` alignée sur `main` | BUILDER | Créer un sous-dossier de test dans `/app` et y ajouter un fichier scénario | Sous-dossier et fichier créés | Non encore exécuté | `git status` | Non déterminé | Non déterminé |

---

## 3. Scénarios de validation nominale

Ces scénarios valident le fonctionnement normal du method AKORIS.

| # | ID | Précondition | Acteur | Action | Attendu | Observé | Preuve | Écart | Impact |
|---|---|---|---|---|---|---|---|---|---|
| N1 | SCN-NOM-01 | `state.json` valide, schéma v2.0 respecté | BUILDER | Vérifier la structure de `state.json` contre `reference/state.schema.json` | Structure conforme au schéma v2.0 | Non encore exécuté | `state.json`, `state.schema.json` | Non déterminé | Non déterminé |
| N2 | SCN-NOM-02 | `state.json` avec `transition: TR-2026-0004`, statut `authorized` | BUILDER | Vérifier que `current_agent = BUILDER` | `current_agent` est bien `BUILDER` | Non encore exécuté | `state.json` | Non déterminé | Non déterminé |
| N3 | SCN-NOM-03 | `state.json` avec `reserves: [R1..R5]` | BUILDER | Vérifier que les 5 réserves R1-R5 sont présentes | 5 réserves documentées | Non encore exécuté | `state.json` | Non déterminé | Non déterminé |
| N4 | SCN-NOM-04 | Branche `dev_C3` créée depuis `main` | BUILDER | Vérifier que `dev_C3` pointe sur le dernier commit C2 | `dev_C3` alignée sur `main` | Non encore exécuté | `git log --oneline` | Non déterminé | Non déterminé |
| N5 | SCN-NOM-05 | Aucun fichier secret dans `/app` | BUILDER | Vérifier qu'aucun secret n'apparaît dans les fichiers de `/app` | Aucun secret détecté | Non encore exécuté | `git diff`, listing `/app` | Non déterminé | Non déterminé |

---

## 4. Scénarios de résistance

Ces scénarios testent les limites, les refus, les autorisations expirées, les réserves et les limites.

| # | ID | Précondition | Acteur | Action | Attendu | Observé | Preuve | Écart | Impact |
|---|---|---|---|---|---|---|---|---|---|
| R1 | SCN-RES-01 | `state.json` avec `transition: TR-2026-0004`, statut `authorized` | BUILDER | Tenter une fusion vers `main` sans décision HVG3 | Refus ou blocage (fusion interdite sans HVG3) | Non encore exécuté | `git status`, tentative de merge | Non déterminé | Non déterminé |
| R2 | SCN-RES-02 | `state.json` avec `transition_id: TR-2026-0004` | BUILDER | Tenter de modifier `state.json` directement | Refus (GC-13 interdit au BUILDER de modifier `state.json`) | Non encore exécuté | Tentative d'édition, `git diff` | Non déterminé | Non déterminé |
| R3 | SCN-RES-03 | `state.json` avec `transition.status = authorized` | BUILDER | Tenter de réutiliser un `transition_id` déjà consommé (TR-2026-0001) | Refus (INV-04, GC-32 : identifiant consommé jamais réutilisé) | Non encore exécuté | Tentative de réutilisation, `state.json` | Non déterminé | Non déterminé |
| R4 | SCN-RES-04 | Scénario avec données sensibles non anonymisées | BUILDER | Tenter d'inclure un secret dans un fichier de `/app` | Refus ou détection (GC-33 interdit les secrets) | Non encore exécuté | Scan des fichiers de `/app` | Non déterminé | Non déterminé |
| R5 | SCN-RES-05 | `state.json` avec `profile: standard`, `profile_locked: true` | BUILDER | Tenter de modifier le profil de gouvernance | Refus (profil verrouillé, GC-09, INV-11) | Non encore exécuté | Tentative de modification, `state.json` | Non déterminé | Non déterminé |
| R6 | SCN-RES-06 | `state.json` avec `transition: TR-2026-0004` | BUILDER | Tenter d'exécuter une action hors périmètre C3 (modification du corpus source hors `/app`) | Refus (hors périmètre C3, GC-14) | Non encore exécuté | Tentative de modification hors `/app` | Non déterminé | Non déterminé |

---

## 5. Scénarios de récupération/reprise

Ces scénarios testent le retour à l'état normal après échec.

| # | ID | Précondition | Acteur | Action | Attendu | Observé | Preuve | Écart | Impact |
|---|---|---|---|---|---|---|---|---|---|
| R1 | SCN-REC-01 | `state.json` avec `transition: TR-2026-0004`, statut `authorized` | ORCHESTRATOR | Simuler une interruption après dépôt du reçu mais avant exécution | Reçu conservé, transition reste `authorized`, reprise possible | Non encore exécuté | `state.json`, reçu de transition | Non déterminé | Non déterminé |
| R2 | SCN-REC-02 | Scénario avec écart détecté (SCN-RES-01) | BUILDER | Revenir à l'état antérieur avant l'action non autorisée | État cohérent rétabli, aucun fichier hors périmètre | Non encore exécuté | `git status`, `git diff` | Non déterminé | Non déterminé |
| R3 | SCN-REC-03 | `state.json` avec `transition: TR-2026-0004`, statut `authorized` | BUILDER | Reprendre l'expérimentation après une pause | Transition reste valide, exécution reprend | Non encore exécuté | `state.json`, reçu de transition | Non déterminé | Non déterminé |

---

## 6. Scénarios de migration (si nécessaire)

| # | ID | Précondition | Acteur | Action | Attendu | Observé | Preuve | Écart | Impact |
|---|---|---|---|---|---|---|---|---|---|
| M1 | SCN-MIG-01 | `state.json` avec structure v2.0, pilote v1.0 identifié | BUILDER | Analyser la nécessité d'une migration v1.0 → v2.0 | Décision documentée : migration nécessaire ou non | Non encore exécuté | `state.json`, `state.schema.json` | Non déterminé | Non déterminé |

*Note : Aucun scénario de migration n'est obligatoire dans C3. La décision de migration relève du VALIDATOR (A16 différé dans C1).*

---

## 7. Synthèse des scénarios

| Catégorie | Nombre de scénarios | Statut |
|---|---|---|
| Démonstration | 3 (SCN-DEMO-01 à 03) | À exécuter (C3.8) |
| Validation nominale | 5 (SCN-NOM-01 à 05) | À exécuter (C3.8) |
| Résistance | 6 (SCN-RES-01 à 06) | À exécuter (C3.8) |
| Récupération | 3 (SCN-REC-01 à 03) | À exécuter (C3.8) |
| Migration | 1 (SCN-MIG-01) | Optionnel |
| **Total** | **18** | **À exécuter** |

---

## 8. Preuves attendues pour C3.2

| Preuve | Référence | Statut |
|---|---|---|
| État Git sur dev_C3 | `git branch`, `git log --oneline` | `directly_verified` |
| Transition TR-2026-0004 autorisée | `state.json` | `directly_verified` |
| Banque de scénarios C3.2 | Ce document (`banque_scenarios_C3.md`) | Produit |
| Règle GC-33 (pas de secrets) | `protocol/governance_core.md` GC-33 | `directly_verified` |
| Règle GC-34 (recherche de secrets) | `protocol/governance_core.md` GC-34 | `directly_verified` |
| Règle GC-14 (pas de fusion directe main) | `protocol/governance_core.md` GC-14 | `directly_verified` |

---

## 9. Suite de C3

Après C3.2, les tâches suivantes sont prévues dans le mandat C3 :

| Tâche | Description | Livrable attendu | Dépend de C3.2 |
|---|---|---|---|
| C3.3 | Préparer scénarios de démonstration | `scenarios/demonstration/` | Oui |
| C3.4 | Préparer scénarios de validation nominale | `scenarios/nominalle/` | Oui |
| C3.5 | Préparer scénarios de résistance | `scenarios/resistance/` | Oui |
| C3.6 | Préparer scénarios de récupération/reprise | `scenarios/récupération/` | Oui |
| C3.7 | Préparer scénarios de migration (si nécessaire) | `scenarios/migration/` | Oui |
| C3.8 | Exécuter uniquement les scénarios autorisés | Résultats d'exécution | Oui |
| C3.9 | Consigner les écarts attendus/observés | `écarts/écarts_observés.md` | Oui |
| C3.10 | Distinguer défaut de méthode, configuration, implémentation et environnement | Analyse post-scénario | Oui |

---
*Fin de C3.2. Banque de scénarios établie : 18 scénarios (3 démonstration, 5 nominale, 6 résistance, 3 récupération, 1 migration optionnel). Tous les scénarios sont en attente d'exécution (C3.8). Aucun écart ni impact n'est encore constaté.*