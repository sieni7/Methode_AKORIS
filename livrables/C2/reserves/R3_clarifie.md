# C2 — Réserve R3 : Autorité sources historiques

**Chantier** : C2 — Vérification technique  
**Tâche** : C2-03 — Traiter réserve R3 (priorité moyenne)  
**Transition** : TR-2026-0003 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C2-verification-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C2` (alignée sur `main`, intègre C0 + C1)  
**Référence** : Réserve R3 de C0 (état.json `last_decision.reserves`)

---

## 1. Objet de la réserve R3

| Élément | Valeur |
|---|---|
| Réserve | R3 : Attribution autorité sources historiques (C0-08) — vigilance contre attribution implicite d'autorité normative |
| Gravité | S2 |
| Consigne C0 | Ne pas attribuer d'autorité normative par défaut |
| Contexte C0 | 5 sources historiques identifiées (S1 à S5), niveaux d'autorité déclarés de 2 à 5 |

---

## 2. Hiérarchie d'autorité des sources (déclarée dans le corpus)

| Niveau | Source | Rôle | Autorité normative par défaut ? |
|---|---|---|---|
| 1 | Décision humaine validée (VALIDATOR) | Prime sur tout | Oui (absolue) |
| 2 | `AKORIS_consolide.md` (F3) | Doctrine du cadre (v1.0) | Non — subordonné au niveau 1 |
| 3 | `AKORIS_architecture_documentaire.md` (F2) | Plan d'architecture | Non — subordonné au niveau 1 |
| 4 | `akoris_documentation_builder.md` (F1) | Méthode de rédaction | Non — subordonné au niveau 1 |
| 5 | Projet pilote `demo_web` | Matériau, non doctrinal | Non — matériau, pas doctrine |

---

## 3. Clarification : aucune autorité normative par défaut

### 3.1 Principe

> **Règle R3-1** : Aucune autorité normative n'est attribuée par défaut aux sources historiques. Leur niveau d'autorité (2 à 5) est déclaratif et reste subordonné à toute décision humaine validée (niveau 1).

### 3.2 Conséquences pour le corpus

| Source | Niveau déclaré | Peut-elle faire autorité sur un document produit ? | Condition pour faire autorité |
|---|---|---|---|
| `AKORIS_consolide.md` (F3) | Niveau 2 | Non | Seulement par décision explicite du VALIDATOR |
| `AKORIS_architecture_documentaire.md` (F2) | Niveau 3 | Non | Seulement par décision explicite du VALIDATOR |
| `akoris_documentation_builder.md` (F1) | Niveau 4 | Non | Seulement par décision explicite du VALIDATOR |
| Projet pilote `demo_web` | Niveau 5 | Non | Jamais (matériau, non doctrinal, A6) |

### 3.3 Distinction source vs règle

> **Règle R3-2** : Une source historique peut alimenter la rédaction (contexte, origine, forme) mais ne peut pas devenir une règle normative sans décision explicite du VALIDATOR.

> **Règle R3-3** : Le niveau "pilote" (niveau 5) désigne explicitement un matériau non doctrinal qui ne doit jamais être promu en règle du protocole.

---

## 4. Preuves et traçabilité

| Élément | Référence | Statut |
|---|---|---|
| Réserve R3 définie | `state.json` `last_decision.reserves` | `directly_verified` |
| Sources historiques C0-08 | `livrables/C0/sources_historique/sources_historique.md` | `directly_verified` |
| Hiérarchie d'autorité | `00_cartographie.md` §3, `document_map.md` §5 | `directly_verified` |
| Décision A6 (statut du pilote) | `00_cartographie.md` §7.2, `audit_policy.md` §4.1 | `directly_verified` |

---

## 5. Conclusion

La réserve R3 est **clarifiée** : aucune autorité normative n'est attribuée par défaut aux sources historiques. Le niveau "pilote" (niveau 5) reste classé comme matériau non doctrinal.

**Statut R3** : ✅ Clarifiée — pas d'attribution d'autorité normative par défaut aux sources historiques.

---
*Fin de R3. Réserve clarifiée. Prêt pour R4.*