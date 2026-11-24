# C2 — Non-conformité NC-02 : Taux d'approbation des documents (3/45 = 6,7%)

**Chantier** : C2 — Vérification technique  
**Tâche** : C2-07 — Corriger non-conformité NC-02 (priorité faible)  
**Transition** : TR-2026-0003 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C2-verification-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C2` (alignée sur `main`, intègre C0 + C1)  
**Référence** : Non-conformité NC-02 de C1 (seulement 3/45 documents "Approuvés")

---

## 1. Objet de la non-conformité NC-02

| Élément | Valeur |
|---|---|
| Non-conformité | NC-02 : Seulement 3/45 documents "Approuvés" (6,7%) |
| Priorité | Faible |
| Action C2 demandée | Définir des critères formels de "document approuvé" et mettre à jour la classification |
| Contexte | Seul les 3 livrables V7 (getting_started.md, traceability_map.md, versioning_policy.md) sont approuvés par le VALIDATOR |

---

## 2. Répartition actuelle des statuts documentaires (C0-09)

| Statut | Nombre | Pourcentage |
|---|---|---|
| Approuvé | 3 | 6,7 % |
| Proposé | 24 | 53,3 % |
| Non vérifié | 18 | 40,0 % |
| **Total** | **45** | **100 %** |

Les 3 documents approuvés sont :
1. `protocol/getting_started.md` (VALIDÉ PAR LE VALIDATOR — 2026-11-21)
2. `reference/traceability_map.md` (VALIDÉ PAR LE VALIDATOR — 2026-11-21)
3. `reference/versioning_policy.md` (VALIDÉ PAR LE VALIDATOR — 2026-11-21)

---

## 3. Critères formels de "document approuvé"

### 3.1 Définition

> **Règle NC-02-1** : Un document est "Approuvé" si et seulement s'il a fait l'objet d'une décision explicite du VALIDATOR, tracée, portant sur l'approbation du document lui-même (et non seulement sur une décision C0, C1 ou C2).

### 3.2 Critères d'évaluation

| Critère | Description | Preuve requise |
|---|---|---|
| Décision VALIDATOR | Le VALIDATOR a pris une décision explicite sur le document | Identifiant de décision, date, auteur, motif |
| Décision tracée | La décision est consignée dans `state.json` (`last_decision` ou `change_control.change_history`) | Référence dans `state.json` |
| Décision sur le document | La décision porte spécifiquement sur l'approbation du document (pas seulement sur un chantier ou un périmètre) | Libellé de la décision mentionne le document |

### 3.3 Application aux 45 documents

| Document | Statut actuel | Critères satisfaits ? | Écart |
|---|---|---|---|
| `getting_started.md` | Approuvé | ✅ Décision HVG1 (ou V7 validation) sur le document | — |
| `traceability_map.md` | Approuvé | ✅ Décision de validation V7 sur le document | — |
| `versioning_policy.md` | Approuvé | ✅ Décision de validation V7 sur le document | — |
| Autres 42 documents | Proposé / Non vérifié | ❌ Aucune décision VALIDATOR sur le document | Décision VALIDATOR manquante |

---

## 4. Recommandations pour mettre à jour la classification

### 4.1 Pour augmenter le taux d'approbation

| Action | Acteur | Priorité | Justification |
|---|---|---|---|
| Décision VALIDATOR sur les documents normatifs clés (governance_core.md, decision_policy.md, etc.) | VALIDATOR | Moyenne | Ces documents sont le socle du cadre |
| Décision VALIDATOR sur les profils (profile_standard, profile_lite, profile_reinforced) | VALIDATOR | Moyenne | Les profils sont utilisés dans state.json |
| Décision VALIDATOR sur les politiques spécialisées (audit_policy, permission_policy, etc.) | VALIDATOR | Moyenne | Ce sont des sources uniques de leurs domaines |

### 4.2 Pour les documents "Non vérifié"

| Document | Raison du statut | Action possible |
|---|---|---|
| `state.json` | Pas de champ statut, pas de validation documentaire | Décision VALIDATOR sur l'adoption du schéma v2.0 |
| `state.schema.json` | Pas de champ statut (fichier JSON) | Décision VALIDATOR sur l'adoption du schéma |
| `changelog.md` | Journal de maintenance, non normatif | Aucun (document non normatif par nature) |
| `plan_de_consolidation.md` | Pas de bloc d'en-tête standard | Décision VALIDATOR sur l'adoption du plan |
| `_sources/*` | Sources historiques, pas de bloc d'en-tête | Aucun (sources, pas de règles) |
| `prompts/*` | "LIVRABLE VAGUE 6 — à valider par le VALIDATOR" | Décision VALIDATOR sur chaque prompt |
| `templates/*` | "LIVRABLE VAGUE 6 — à valider par le VALIDATOR" | Décision VALIDATOR sur chaque template |

---

## 4. Preuves et traçabilité

| Élément | Référence | Statut |
|---|---|---|
| Non-conformité NC-02 identifiée | Rapport C1 (C1-D) | `directly_verified` |
| Statuts documentaires C0-09 | `livrables/C0/stats_doc/tableau_statu.md` | `directly_verified` |
| 3 documents approuvés (V7) | `README.md` §10, en-têtes des 3 fichiers | `directly_verified` |
| Règle d'approbation | `decision_policy.md` §3, §11 | `directly_verified` |

---

## 5. Conclusion

La non-conformité NC-02 est **documentée** : seuls 3/45 documents (6,7 %) sont approuvés. Les critères formels de "document approuvé" sont définis : décision VALIDATOR explicite, tracée, portant sur le document lui-même. La mise à jour de la classification nécessite des décisions VALIDATOR sur les documents non encore approuvés.

**Statut NC-02** : ✅ Documentée — critères formels définis, mise à jour en attente de décisions VALIDATOR.

---
*Fin de NC-02. Non-conformité documentée. Prêt pour NC-03.*