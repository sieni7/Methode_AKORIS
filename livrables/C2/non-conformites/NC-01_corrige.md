# C2 — Non-conformité NC-01 : Traçabilité des décisions A15, A10, A14, A09

**Chantier** : C2 — Vérification technique  
**Tâche** : C2-06 — Corriger non-conformité NC-01 (priorité moyenne)  
**Transition** : TR-2026-0003 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C2-verification-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C2` (alignée sur `main`, intègre C0 + C1)  
**Référence** : Non-conformité NC-01 de C1 (4/26 décisions validées avec traçabilité moindre)

---

## 1. Objet de la non-conformité NC-01

| Élément | Valeur |
|---|---|
| Non-conformité | NC-01 : 4/26 décisions "validées" (A15, A10, A14, A09) traçabilité moindre |
| Priorité | Moyenne |
| Action C2 demandée | Renforcer la traçabilité des décisions (lier chaque décision à sa preuve en state.json) |
| Contexte | 4 décisions VALIDATOR (A15, A10, A14, A09) ont une traçabilité moindre dans le registre C0 |

---

## 2. Analyse des 4 décisions concernées

| ID | Décision | Date | Auteur | Preuve dans C0 | Écart de traçabilité |
|---|---|---|---|---|---|
| D-VAL-A15 | Règles AKORIS prospectives : SemVer indépendant pour protocole et schéma ; révision simple pour les documents ; incrémentation événementielle | 2026-11-21 | VALIDATOR | `versioning_policy.md` §5 | Lien vers `state.json` absent |
| D-VAL-A10 | Aucun champ de version du profil ajouté à `state.json`, au modèle d'état ni au schéma | 2026-11-21 | VALIDATOR | `versioning_policy.md` §2 | Lien vers `state.json` absent |
| D-VAL-A14 | A7 demeure la taxonomie de référence à cinq catégories ; aucune unification des listes de CART et F2 requise | 2026-11-21 | VALIDATOR | `versioning_policy.md` §4 | Lien vers `state.json` absent |
| D-VAL-A09 | Rôles des sources dans versioning_policy.md : CART et F2 marqués NON DÉTERMINÉ | 2026-11-21 | VALIDATOR | `versioning_policy.md` §2 | Lien vers `state.json` absent |

---

## 3. Renforcement de la traçabilité

### 3.1 Lien avec state.json

`state.json` contient un champ `last_decision` qui référence la dernière décision du VALIDATOR. Cependant, il ne contient qu'une seule décision (`D-001-HVG0`). Les décisions A15, A10, A14, A09 ne sont pas référencées dans `state.json`.

### 3.2 Proposition de renforcement

> **Règle NC-01-1** : Chaque décision VALIDATOR doit être liée à sa preuve dans `state.json` via le champ `last_decision` ou via un registre des décisions (`decision_log.md` — fichier planifié, non créé, lacune L1 de C0).

> **Règle NC-01-2** : Le champ `change_control.change_history` dans `state.json` doit enregistrer chaque changement lié à une décision VALIDATOR, avec l'identifiant de la décision comme référence.

### 3.3 Actions concrètes pour C2

| Action | Description | Statut |
|---|---|---|
| NC-01-1 | Lier les décisions A15, A10, A14, A09 à leurs preuves dans `versioning_policy.md` | ✅ Documenté (ce fichier) |
| NC-01-2 | Consigner dans `change_control.change_history` de `state.json` le lien entre chaque décision et sa preuve | ⏳ À faire par ORCHESTRATOR (modification de state.json) |
| NC-01-3 | Créer `reference/decision_log.md` (fichier planifié, lacune L1 de C0) pour centraliser toutes les décisions | ⏳ À faire (décision VALIDATOR requise) |

---

## 4. Preuves et traçabilité

| Élément | Référence | Statut |
|---|---|---|
| Non-conformité NC-01 identifiée | Rapport C1 (C1-D) | `directly_verified` |
| Décisions A15, A10, A14, A09 | `versioning_policy.md` §2, §4, §5 | `directly_verified` |
| state.json last_decision | `state.json` lignes 52-66 | `directly_verified` (D-001-HVG0 seulement) |
| state.json change_control | `state.json` lignes 76-103 | `directly_verified` (CC-2026-0001 à 0004) |

---

## 5. Conclusion

La non-conformité NC-01 est **documentée** : les 4 décisions A15, A10, A14, A09 ont une traçabilité moindre car elles ne sont pas liées à `state.json`. Le renforcement de la traçabilité est proposé via l'enregistrement dans `change_control.change_history` et la création d'un registre des décisions (`decision_log.md`).

**Statut NC-01** : ✅ Documentée — renforcement de la traçabilité proposé, exécution par ORCHESTRATOR en attente.

---
*Fin de NC-01. Non-conformité documentée. Prêt pour NC-02.*