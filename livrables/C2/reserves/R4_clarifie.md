# C2 — Réserve R4 : État de référence vs state.json/state.md

**Chantier** : C2 — Vérification technique  
**Tâche** : C2-04 — Traiter réserve R4 (priorité moyenne)  
**Transition** : TR-2026-0003 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C2-verification-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C2` (alignée sur `main`, intègre C0 + C1)  
**Référence** : Réserve R4 de C0 (état.json `last_decision.reserves`)

---

## 1. Objet de la réserve R4

| Élément | Valeur |
|---|---|
| Réserve | R4 : État de référence vs state.json/state.md — distinction état de référence C0 (markdown) vs états opérationnels |
| Gravité | S3 |
| Consigne C0 | État de référence markdown autonome dans `livrables/` |
| Contexte C0 | `référence_c0.md` produit dans `livrables/C0/reference/` ; `state.json` et `state.md` sont des états opérationnels |

---

## 2. Clarification de la distinction

| Objet | `référence_c0.md` (état de référence C0) | `state.json` | `state.md` |
|---|---|---|---|
| **Nature** | Document Markdown autonome | État opérationnel machine | Vue lisible générée |
| **Localisation** | `livrables/C0/reference/référence_c0.md` | Racine du dépôt | (à générer, absent actuellement) |
| **Contenu** | Inventaire, métadonnées, classifications, statuts, décisions, divergences, lacunes, sources historiques | État courant du projet (projet, sprint, transition, décision, réserves, changements) | Vue lisible de `state.json` |
| **Figé** | Oui — figé à la date de fin C0 | Non — état courant, modifiable par ORCHESTRATOR | Non — vue générée, pas éditée manuellement |
| **Propriétaire** | BUILDER (livrable C0) | ORCHESTRATOR (seul rédacteur normal, GC-12) | Généré automatiquement |
| **Modifiable par BUILDER** | Non (figé) | Non (GC-13) | Non (GC-13, INV-08) |

---

## 3. Règles de séparation

> **Règle R4-1** : L'état de référence C0 (`référence_c0.md`) est un document documentaire figé, distinct de `state.json` et `state.md`. Il ne doit pas être confondu avec l'état opérationnel.

> **Règle R4-2** : `state.json` est la source de vérité de l'état opérationnel courant (A2). `state.md` en est une vue générée, jamais une source concurrente (GC-13, INV-08).

> **Règle R4-3** : Le BUILDER ne modifie ni `state.json`, ni `state.md` (GC-13). Le BUILDER produit uniquement des livrables dans `livrables/C2/`.

---

## 4. Preuves et traçabilité

| Élément | Référence | Statut |
|---|---|---|
| Réserve R4 définie | `state.json` `last_decision.reserves` | `directly_verified` |
| État de référence C0 | `livrables/C0/reference/référence_c0.md` | `directly_verified` |
| `state.json` | Racine du dépôt | `directly_verified` (lu, non modifié) |
| `state.md` | Absent du dépôt | `directly_verified` (constat d'absence) |
| GC-13 | `protocol/governance_core.md` GC-13 | `directly_verified` |

---

## 5. Conclusion

La réserve R4 est **clarifiée** : la distinction entre l'état de référence C0 (markdown autonome, figé dans `livrables/C0/reference/`) et les états opérationnels (`state.json`/`state.md`) est maintenue et documentée.

**Statut R4** : ✅ Clarifiée — distinction état de référence vs états opérationnels confirmée.

---
*Fin de R4. Réserve clarifiée. Prêt pour R5.*