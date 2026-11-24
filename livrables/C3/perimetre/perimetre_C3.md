# C3 — C3.1 : Périmètre et conditions de sécurité

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.1 — Définir périmètre et conditions de sécurité  
**Transition** : TR-2026-0004 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C3-expérimentation-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)  
**Contrainte** : Aucune expérience en dehors de `/app` sans autorisation explicite

---

## 1. Vérification état Git (prérequis C3.1)

| Vérification | Résultat | Preuve |
|---|---|---|
| Branche courante | `dev_C3` | `git branch` |
| Alignement avec `main` | `dev_C3` = `main` (commit `2172ea5` + C3 reçu) | `git log --oneline` |
| Intégration C0 + C1 + C2 dans `main` | 16 commits présents sur `main` | `git log --oneline main` |
| Reçu de transition C3 déposé | `livrables/C3/transition/recu_transition_C3.md` | Commit `2172ea5` |
| `current_agent` = BUILDER | `state.json` ligne 31 | `directly_verified` |
| Transition TR-2026-0004 autorisée | `state.json` ligne 35-50 | `directly_verified` |

---

## 2. Objectif de C3.1

Définir le périmètre expérimental et les conditions de sécurité pour l'expérimentation du method AKORIS dans `/app`. Cela inclut :

- Les limites du périmètre expérimental (ce qui est inclus, ce qui est exclu)
- Les conditions de sécurité (règles GC-33, GC-34, etc.)
- Les scénarios autorisés et non autorisés
- Les variables d'environnement et conditions d'exécution

---

## 3. Périmètre de l'expérimentation C3

### 3.1 Périmètre inclus

| Élément | Description | Localisation |
|---|---|---|
| Scénarios de démonstration | Scénarios qui montrent le method AKORIS en action | `/app` |
| Scénarios de validation nominale | Scénarios qui valident le fonctionnement normal | `/app` |
| Scénarios de résistance | Scénarios qui testent les limites, les refus, les autorisations expirées | `/app` |
| Scénarios de récupération/reprise | Scénarios de retour à l'état normal après échec | `/app` |
| Scénarios de migration | Scénarios de migration de données ou structures (si nécessaire) | `/app` |
| Observance des écarts | Consignation des écarts attendus/observés | `/app` |
| Distinction défaut de méthode, configuration, implémentation, environnement | Analyse post-chaque-scénario | `/app` |

### 3.2 Périmètre exclu

| Élément | Justification | Base normative |
|---|---|---|
| Expériences en dehors de `/app` | Hors périmètre C3 sans autorisation explicite | Mandat C3 §1 |
| Scénarios non autorisés par le mandat C3 | Hors périmètre C3 | Mandat C3 §1 |
| Modification du method AKORIS sans décision HVG3 | Nécessite une décision distincte | Mandat C3 §1, GC-14 |
| Accès à des données sensibles sans anonymisation | Protection des secrets | GC-33 |
| Scénarios violant GC-33 (secrets) | Protection des secrets | GC-33 |
| Scénarios violant GC-34 (permissions) | Recherche de secrets avant commit/fusion | GC-34 |

---

## 4. Conditions de sécurité

### 4.1 Règles GC-33 (secrets)

| Règle | Contenu | Application C3 |
|---|---|---|
| GC-33 | Aucun secret n'apparaît dans un rapport, un commit, un document ou un journal | Aucun secret dans les scénarios C3, les rapports d'écarts ou le rapport C3 |
| GC-34 | Les secrets sont recherchés avant commit et avant fusion | Vérification avant chaque commit C3 |

### 4.2 Règles GC-34 (permissions)

| Règle | Contenu | Application C3 |
|---|---|---|
| GC-34 | Recherche de secrets avant commit et avant fusion | Même que GC-33 |
| GC-35 | Une anomalie touchant la sécurité, les données ou un secret relève au minimum de S0 | Toute anomalie de sécurité dans C3 est classifiée S0 minimum |

### 4.3 Conditions d'exécution

| Condition | Valeur | Justification |
|---|---|---|
| Environnement d'expérimentation | `/app` | Uniquement dans `/app`, pas en dehors |
| Données utilisées | Données fictives ou anonymisées | Pas de données réelles sensibles |
| Secrets | Aucun secret autorisé | Conformément à GC-33 |
| Modifications du corpus source | Aucune | Lecture seule du corpus AKORIS (sauf `/app`) |
| Fusion vers `main` | Interdite sans HVG3 | GC-14, mandat C3 |

---

## 5. Scénarios autorisés et non autorisés

### 5.1 Scénarios autorisés

| Type | Description | Livrable associé |
|---|---|---|
| Démonstration | Montrer le method AKORIS en action | `scenarios/demonstration/` |
| Validation nominale | Valider le fonctionnement normal | `scenarios/nominalle/` |
| Résistance | Tester les limites, les refus, les autorisations expirées | `scenarios/resistance/` |
| Récupération | Retour à l'état normal après échec | `scenarios/récupération/` |
| Migration | Migration de données ou structures (si nécessaire) | `scenarios/migration/` |

### 5.2 Scénarios non autorisés

| Type | Motif |
|---|---|
| Scénarios en dehors de `/app` | Hors périmètre C3 |
| Scénarios avec données sensibles réelles | Violation GC-33 |
| Scénarios modifiant le method AKORIS | Nécessite décision HVG3 |
| Scénarios modifiant `state.json` | Interdit à C3 (réservé à C1/C2) |
| Scénarios fusionnant vers `main` sans HVG3 | Interdit par GC-14 |

---

## 6. Variables d'environnement et conditions d'exécution

| Variable | Valeur | Commentaire |
|---|---|---|
| Répertoire d'expérimentation | `/app` | Uniquement ce répertoire |
| Données de test | Fictives ou anonymisées | Aucune donnée réelle |
| Niveau de risque maximal autorisé | S0 (aucune anomalie S0/S1 tolérée) | Conformément aux conditions d'arrêt C3 |
| Modification du corpus AKORIS | Interdite | Lecture seule du corpus source |

---

## 7. Preuves attendues pour C3.1

| Preuve | Référence | Statut |
|---|---|---|
| État Git sur dev_C3 | `git branch`, `git log --oneline` | `directly_verified` |
| Transition TR-2026-0004 autorisée | `state.json` | `directly_verified` |
| Périmètre C3 défini | Ce document (`perimetre_C3.md`) | Produit |
| Conditions de sécurité définies | §4 de ce document | Produit |
| Scénarios autorisés/non autorisés | §5 de ce document | Produit |

---

## 8. Suite de C3

Après C3.1, les tâches suivantes sont prévues dans le mandat C3 :

| Tâche | Description | Livrable attendu | Dépend de C3.1 |
|---|---|---|---|
| C3.2 | Décrire chaque scénario (précondition, acteur, action, attendu, observé, preuve, écart, impact) | Banque de scénarios | Oui |
| C3.3 | Préparer scénarios de démonstration | `scenarios/demonstration/` | Oui |
| C3.4 | Préparer scénarios de validation nominale | `scenarios/nominalle/` | Oui |
| C3.5 | Préparer scénarios de résistance | `scenarios/resistance/` | Oui |
| C3.6 | Préparer scénarios de récupération/reprise | `scenarios/récupération/` | Oui |
| C3.7 | Préparer scénarios de migration (si nécessaire) | `scenarios/migration/` | Oui |
| C3.8 | Exécuter uniquement les scénarios autorisés | Résultats d'exécution | Oui |
| C3.9 | Consigner les écarts attendus/observés | `écarts/écarts_observés.md` | Oui |
| C3.10 | Distinguer défaut de méthode, configuration, implémentation et environnement | Analyse post-scénario | Oui |

---
*Fin de C3.1. Périmètre et conditions de sécurité définis. Aucune expérience en dehors de `/app`. Aucun secret autorisé. Fusion vers `main` interdite sans HVG3.*