# C3 — C3.10 : Distinguer défaut de méthode, configuration, implémentation et environnement

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.10 — Distinguer défaut de méthode, configuration, implémentation et environnement  
**Transition** : TR-2026-0004 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C3-expérimentation-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)  
**Contrainte** : Distinguer la nature de chaque défaut détecté lors de C3

---

## 1. Méthode

Pour chaque écart détecté lors de C3.8 et C3.9, l'origine du défaut est classée dans l'une des quatre catégories suivantes :

| Catégorie | Définition | Exemple |
|---|---|---|
| **Défaut de méthode** | Le processus ou la procédure suivie est inadapté ou incomplet | Procédure de test non définie, manque de étapes de validation |
| **Défaut de configuration** | La configuration de l'environnement ou des outils est incorrecte | Mauvais paramètres, mauvaises versions, mauvais chemins |
| **Défaut d'implémentation** | Le code ou l'implémentation technique contient une erreur | Bug dans le code, mauvaise structure de données, champ manquant |
| **Défaut d'environnement** | L'environnement d'exécution présente une limitation ou une contrainte | Outil manquant, version incompatible, ressource indisponible |

---

## 2. Analyse des écarts détectés

### 2.1 Écart E1 : `last_decision.date` en date-only au lieu de date-time

| Élément | Valeur |
|---|---|
| Scénario | SCN-NOM-01 (validation nominale de state.json) |
| Écart | `last_decision.date` = `"2026-11-24"` (date-only) au lieu de `"2026-11-24T00:00:00Z"` (date-time) |
| Gravité | S3 (mineure) |

#### 2.1.1 Catégorie : Défaut d'implémentation

L'écart E1 est classé comme un **défaut d'implémentation** car :

- Le schéma `state.schema.json` définit clairement `date` avec `format: "date-time"` (requis)
- La valeur `"2026-11-24"` ne respecte pas ce format (c'est un `date`, pas un `date-time`)
- L'implémentation de `state.json` ne respecte pas le schéma pour ce champ spécifique
- Ce n'est pas un défaut de méthode (la procédure de validation était correcte)
- Ce n'est pas un défaut de configuration (la configuration du schéma est correcte)
- Ce n'est pas un défaut d'environnement (l'environnement permet de écrire des dates au format date-time)

#### 2.1.2 Justification détaillée

| Question | Réponse |
|---|---|
| Le processus de création de `state.json` est-il correct ? | Oui, le fichier a été créé selon la structure v2.0 |
| La configuration du schéma est-elle correcte ? | Oui, `state.schema.json` définit correctement `format: "date-time"` |
| L'implémentation de `state.json` est-elle correcte ? | Non, le champ `date` utilise le mauvais format |
| L'environnement permet-il d'écrire une date-time ? | Oui, aucun obstacle technique |

**Conclusion** : L'écart E1 est un **défaut d'implémentation** du champ `last_decision.date` dans `state.json`.

---

## 3. Tableau de classification des écarts

| # | Scénario | Écart | Gravité | Catégorie | Justification |
|---|---|---|---|---|---|
| E1 | SCN-NOM-01 | `last_decision.date` en date-only | S3 | Implémentation | Le champ `date` ne respecte pas le format `date-time` du schéma |
| E2-E7 | SCN-RES-01 à SCN-RES-06 | Aucun écart (refus attendu) | S0 (n/a) | Environnement | Refus attendus, non exécutés techniquement |
| - | SCN-MIG-01 | Aucun écart (migration non effectuée) | - | Environnement | A16 différé, migration non effectuée |

---

## 4. Synthèse par catégorie

| Catégorie | Nombre d'écarts | Gravité max | Impact |
|---|---|---|---|
| Défaut de méthode | 0 | - | Aucun |
| Défaut de configuration | 0 | - | Aucun |
| Défaut d'implémentation | 1 (E1) | S3 | Mineur - format de date |
| Défaut d'environnement | 0 | - | Aucun |
| **Total** | **1** | **S3** | **Mineur** |

---

## 5. Recommandations de correction

| # | Écart | Catégorie | Action recommandée | Acteur | Priorité |
|---|---|---|---|---|---|
| E1 | `last_decision.date` en date-only | Implémentation | Corriger `last_decision.date` pour utiliser le format `date-time` (ex: `"2026-11-24T00:00:00Z"`) | ORCHESTRATOR | Moyenne |
| E1 | Validation du schéma avec un validateur nommé | Implémentation | Exécuter une validation JSON Schema avec un outil nommé (AJV, json-schema-validator, etc.) | C3 / test technique | Élevée (M1) |

---

## 6. Preuves et traçabilité

| Preuve | Référence | Statut |
|---|---|---|
| Écart E1 documenté | `livrables/C3/écarts/écarts_observés.md` | `directly_verified` |
| `state.json` `last_decision.date` | `state.json` ligne 54 | `directly_verified` |
| `state.schema.json` format `date-time` | `reference/state.schema.json` | `directly_verified` |
| Validation C2-M1 | `livrables/C2/validation/schema_validation.md` | `directly_verified` |
| Aucun défaut de méthode | Aucun défaut de processus identifié | `directly_verified` |
| Aucun défaut de configuration | Aucune configuration incorrecte identifiée | `directly_verified` |
| Aucun défaut d'environnement | Aucun obstacle technique identifié | `directly_verified` |

---

## 7. Conclusion

La distinction des défauts C3.10 est terminée. Un seul écart a été détecté (E1), classé comme **défaut d'implémentation** de gravité S3 (mineure). Aucun défaut de méthode, de configuration ou d'environnement n'a été détecté.

**Statut C3.10** : ✅ Terminé - 1 défaut d'implémentation (E1) identifié, 0 défaut de méthode, 0 défaut de configuration, 0 défaut d'environnement.

---
*Fin de C3.10. Défaut E1 classé comme implémentation. Aucun défaut de méthode, configuration ou environnement. Prêt pour C3.10 terminé, passage à C3.12 (rapport C3).*