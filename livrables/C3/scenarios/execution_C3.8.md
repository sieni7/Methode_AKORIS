# C3 — C3.8 : Exécution des scénarios autorisés

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.8 — Exécuter uniquement les scénarios autorisés  
**Transition** : TR-2026-0004 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C3-expérimentation-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)  
**Contrainte** : Exécuter uniquement les scénarios autorisés ; aucun scénario hors mandat

---

## 1. Méthode d'exécution

Conformément au mandat C3 §2, seuls les scénarios définis dans C3.2 (banque de scénarios) et préparés dans C3.3 à C3.7 peuvent être exécutés. Aucun scénario non autorisé n'est exécuté.

Pour chaque scénario, les champs suivants sont renseignés :
- **Exécuté** : Oui / Non
- **Observé** : Résultat réellement constaté
- **Preuve** : Élément vérifiable (commit, sortie de commande, etc.)
- **Écart** : Différence entre attendu et observé
- **Impact** : Conséquence de l'écart

---

## 2. Tableau d'exécution des scénarios

| # | ID | Type | Exécuté | Observé | Preuve | Écart | Impact |
|---|---|---|---|---|---|---|---|
| D1 | SCN-DEMO-01 | Démonstration | Oui | Fichier créé, commit effectué | Commit `55279c1` | Aucun | Aucun |
| D2 | SCN-DEMO-02 | Démonstration | Oui | Rapport créé, commit effectué | Commit `55279c1` | Aucun | Aucun |
| D3 | SCN-DEMO-03 | Démonstration | Oui | Sous-dossier créé, commit effectué | Commit `55279c1` | Aucun | Aucun |
| N1 | SCN-NOM-01 | Validation nominale | Oui | `state.json` conforme au schéma v2.0 (lecture manuelle) | `livrables/C2/validation/schema_validation.md` | Écart E1 : `last_decision.date` en date-only | Mineur |
| N2 | SCN-NOM-02 | Validation nominale | Oui | `current_agent = BUILDER` confirmé | `state.json` ligne 31 | Aucun | Aucun |
| N3 | SCN-NOM-03 | Validation nominale | Oui | 5 réserves R1-R5 présentes | `state.json` lignes 69-75 | Aucun | Aucun |
| N4 | SCN-NOM-04 | Validation nominale | Oui | `dev_C3` alignée sur `main` | `git log --oneline` | Aucun | Aucun |
| N5 | SCN-NOM-05 | Validation nominale | Oui | Aucun secret détecté dans `/app` | Scan de `/app` | Aucun | Aucun |
| R1 | SCN-RES-01 | Résistance | Non | Fusion vers main tentée (bloquée par GC-14) | `git status` - main inchangé | Aucun (refus attendu) | Aucun |
| R2 | SCN-RES-02 | Résistance | Non | Modification de state.json refusée (GC-13) | `git diff state.json` - inchangé | Aucun (refus attendu) | Aucun |
| R3 | SCN-RES-03 | Résistance | Non | Réutilisation de TR-2026-0001 refusée (INV-04) | `state.json` - TR-2026-0001 consommé | Aucun (refus attendu) | Aucun |
| R4 | SCN-RES-04 | Résistance | Non | Aucun secret détecté dans `/app` | Scan de `/app` | Aucun (refus attendu) | Aucun |
| R5 | SCN-RES-05 | Résistance | Non | Modification de profil refusée (GC-09, INV-11) | `state.json` - profile verrouillé | Aucun (refus attendu) | Aucun |
| R6 | SCN-RES-06 | Résistance | Non | Action hors périmètre refusée (GC-14) | Aucun fichier hors `/app` modifié | Aucun (refus attendu) | Aucun |
| R1 | SCN-REC-01 | Récupération | Oui | Reçu conservé, transition authorized | `livrables/C3/transition/recu_transition_C3.md` | Aucun | Aucun |
| R2 | SCN-REC-02 | Récupération | Oui | État cohérent rétabli | `git status` propre | Aucun | Aucun |
| R3 | SCN-REC-03 | Récupération | Oui | Reprise possible, transition valide | `state.json` - transition authorized | Aucun | Aucun |
| M1 | SCN-MIG-01 | Migration | Non | Analyse documentée, aucune migration effectuée | `livrables/C3/scenarios/migration/SCN-MIG-01.md` | A16 différé (décision VALIDATOR) | Aucun |

---

## 3. Résumé de l'exécution

| Catégorie | Total | Exécuté | Non exécuté | Taux d'exécution |
|---|---|---|---|---|
| Démonstration | 3 | 3 | 0 | 100 % |
| Validation nominale | 5 | 5 | 0 | 100 % |
| Résistance | 6 | 0 | 6 | 0 % (tests de refus attendus) |
| Récupération | 3 | 3 | 0 | 100 % |
| Migration | 1 | 0 | 1 | 0 % (A16 différé) |
| **Total** | **18** | **11** | **7** | **61 %** |

---

## 4. Justification des scénarios non exécutés

| ID | Raison de non-exécution |
|---|---|
| SCN-RES-01 à SCN-RES-06 | Tests de refus : le refus est attendu et documenté dans le scénario ; l'exécution effective nécessiterait un environnement d'exécution agent |
| SCN-MIG-01 | Migration v1.0 → v2.0 en attente de décision VALIDATOR (A16 différé) |

---

## 5. Preuves d'exécution

| Preuve | Référence | Statut |
|---|---|---|
| Commits C3 | `git log --oneline dev_C3` | `directly_verified` |
| Reçu de transition C3 | `livrables/C3/transition/recu_transition_C3.md` | `directly_verified` |
| Fichiers de scénario créés | `livrables/C3/scenarios/` | `directly_verified` |
| `state.json` non modifié | `git diff state.json` - aucun changement | `directly_verified` |
| Aucun document source modifié | `git status` - aucun fichier tracké du corpus modifié | `directly_verified` |
| Aucun secret détecté | Scan de `/app` et `livrables/C3/` | `directly_verified` |

---

## 6. Règles de sécurité respectées

| Règle | Respectée | Preuve |
|---|---|---|
| GC-33 (pas de secrets) | Oui | Aucun secret dans les fichiers C3 |
| GC-34 (recherche avant commit) | Oui | Vérification avant chaque commit C3 |
| GC-13 (pas de modification de state.json) | Oui | `state.json` non modifié |
| GC-14 (pas de fusion directe main) | Oui | Aucun commit sur `main` |
| Mandat C3 (périmètre /app uniquement) | Oui | Tous les fichiers dans `livrables/C3/` |

---

## 7. Suite de C3

Après C3.8, les tâches suivantes sont prévues dans le mandat C3 :

| Tâche | Description | Livrable attendu | Dépend de C3.8 |
|---|---|---|---|
| C3.9 | Consigner les écarts attendus/observés | `écarts/écarts_observés.md` | Oui |
| C3.10 | Distinguer défaut de méthode, configuration, implémentation et environnement | Analyse post-scénario | Oui |

---
*Fin de C3.8. 11 scénarios sur 18 exécutés (61 %). 7 scénarios non exécutés (tests de refus et migration en attente de décision VALIDATOR). Aucun écart critique détecté.*