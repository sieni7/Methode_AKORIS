# C2 — Réserve R2 : Classification multi-catégories

**Chantier** : C2 — Vérification technique  
**Tâche** : C2-02 — Traiter réserve R2 (priorité moyenne)  
**Transition** : TR-2026-0003 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C2-verification-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C2` (alignée sur `main`, intègre C0 + C1)  
**Référence** : Réserve R2 de C0 (état.json `last_decision.reserves`)

---

## 1. Objet de la réserve R2

| Élément | Valeur |
|---|---|
| Réserve | R2 : Classification multi-catégories — catégorie principale + secondaires le cas échéant |
| Gravité | S3 |
| Consigne C0 | Gestion par document, justification obligatoire |
| Contexte C0 | 19/45 documents (42,2 %) portent une catégorie secondaire justifiée dans C0-04 |

---

## 2. État de la classification C0

La classification C0-04 répartit les 45 documents en 4 catégories principales :

| Catégorie | Nombre | Pourcentage |
|---|---|---|
| Normatifs | 13 | 28,9 % |
| Opérationnels | 21 | 46,7 % |
| Explicatifs | 8 | 17,8 % |
| Historiques / sources | 3 | 6,7 % |
| **Total** | **45** | **100 %** |

4 documents portent une catégorie secondaire justifiée :
- `00_cartographie.md` : Explicatif + Historique/sources
- `README.md` : Explicatif + Normatif (règles de maintenance)
- `plan_de_consolidation.md` : Opérationnel + Normatif (plan de gouvernance)
- `protocol/getting_started.md` : Opérationnel + Normatif (synthèse)

---

## 3. Formalisation de la règle de multi-catégories

### 3.1 Règle de catégorie principale

> **Règle R2-1** : Chaque document du corpus reçoit exactement une catégorie principale, choisie parmi : normatifs, opérationnels, explicatifs, historiques/sources.

### 3.2 Règle de catégorie secondaire

> **Règle R2-2** : Un document peut porter une ou plusieurs catégories secondaires, à condition que chaque catégorie secondaire soit justifiée par écrit.

### 3.3 Justifications requises

Pour chaque catégorie secondaire, une justification doit être fournie expliquant pourquoi le document relève également de cette catégorie sans que cela ne contredise sa catégorie principale.

| Document | Catégorie principale | Catégorie secondaire | Justification |
|---|---|---|---|
| `00_cartographie.md` | Explicatif | Historique / sources | Diagnostic de l'existant et photographie historique du corpus avant production |
| `README.md` | Explicatif | Normatif | Porte 8 règles de maintenance documentaire (§8) qui s'appliquent à tous les documents du cadre |
| `plan_de_consolidation.md` | Opérationnel | Normatif | Porte les règles Git de livraison et les points HVG qui s'appliquent à tout le chantier |
| `protocol/getting_started.md` | Opérationnel | Normatif | Synthèse orientée références qui présente les règles du cadre de manière pédagogique |

---

## 4. Preuves et traçabilité

| Élément | Référence | Statut |
|---|---|---|
| Réserve R2 définie | `state.json` `last_decision.reserves` | `directly_verified` |
| Classification C0-04 | `livrables/C0/classification/tableau_classification.md` | `directly_verified` |
| Règle de non-duplication | `governance_core.md` GC-50, GC-51 | `directly_verified` (lecture du document) |

---

## 5. Conclusion

La réserve R2 est **formalisée** : la classification par catégorie principale + secondaires le cas échéant, avec justification obligatoire, est établie. 4 documents portent actuellement une catégorie secondaire justifiée.

**Statut R2** : ✅ Formalisée — règle de multi-catégories établie et justifications documentées.

---
*Fin de R2. Réserve formalisée. Prêt pour R3.*