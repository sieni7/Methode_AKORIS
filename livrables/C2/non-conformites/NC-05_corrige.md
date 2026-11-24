# C2 — Non-conformité NC-05 : Contradictions C5/C6 statut "À ARBITRER"

**Chantier** : C2 — Vérification technique  
**Tâche** : C2-10 — Corriger non-conformité NC-05 (priorité faible)  
**Transition** : TR-2026-0003 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C2-verification-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C2` (alignée sur `main`, intègre C0 + C1)  
**Référence** : Non-conformité NC-05 de C1 (contradictions C5/C6 statut "À ARBITRER" non mises à jour post-A4)

---

## 1. Objet de la non-conformité NC-05

| Élément | Valeur |
|---|---|
| Non-conformité | NC-05 : Contradictions C5/C6 statut "À ARBITRER" non mises à jour post-A4 |
| Priorité | Faible |
| Action C2 demandée | Mettre à jour le statut des contradictions C5/C6 en "À ARBITRER" ou "Résolu" avec justification |
| Contexte | C5 et C6 étaient marquées "À ARBITRER" dans C0 ; l'arbitrage A4 a tranché certains aspects |

---

## 2. Analyse des contradictions C5 et C6

### 2.1 Contradiction C5 : Trois chemins racine pour le socle

| Élément | Détail |
|---|---|
| Contradiction | Trois chemins racine pour le socle : `governance/` (F3, 4 fichiers) · `protocol/` racine projet (F2, 11 fichiers) · `documentation/protocol/` (F1) |
| Documents en conflit | F3 (`AKORIS_consolide.md`), F2 (`AKORIS_architecture_documentaire.md`), F1 (`akoris_documentation_builder.md`) |
| Blocage | `document_map.md` |
| Statut C0 | À ARBITRER (A4) |

### 2.2 Contradiction C6 : Collision `README.md`

| Élément | Détail |
|---|---|
| Contradiction | F2 §6.1 = README projet (installation) ; F1 §6 = README documentation |
| Documents en conflit | F2 (`AKORIS_architecture_documentaire.md`), F1 (`akoris_documentation_builder.md`) |
| Statut C0 | À ARBITRER (A4) |

---

## 3. État de l'arbitrage A4

L'arbitrage A4 a été tranché par le VALIDATOR :

| Aspect | Décision A4 | Source |
|---|---|---|
| Chemin racine canonique | `documentation/` autonome | `00_cartographie.md` §7.2, `README.md` §11 |
| README de documentation | `documentation/README.md` distinct du README projet | `00_cartographie.md` §7.2, `README.md` §11 |
| Terminologie | `documentation/README.md` tranché (A4) | `terminology.md` §11 |

---

## 4. Mise à jour du statut des contradictions C5 et C6

### 4.1 C5 : Trois chemins racine pour le socle

**Statut mis à jour : `À ARBITRER` (partiellement résolu par A4)**

Justification : L'arbitrage A4 a tranché le chemin racine canonique (`documentation/` autonome) et le nom du README de documentation. Cependant, la contradiction C5 concerne spécifiquement trois chemins concurrents (`governance/`, `protocol/`, `documentation/protocol/`). A4 tranche `documentation/` comme chemin autonome, mais ne résout pas explicitement la coexistence des trois chemins dans les sources historiques F1, F2, F3. Le statut reste donc `À ARBITRER` pour la coexistence historique, avec la précision que le chemin canonique actuel est `documentation/`.

### 4.2 C6 : Collision `README.md`

**Statut mis à jour : `Résolu` (par A4)**

Justification : L'arbitrage A4 a tranché que `documentation/README.md` est le README de documentation et que le README projet est distinct. La collision entre F2 §6.1 (README projet) et F1 §6 (README documentation) est résolue par cette séparation explicite.

---

## 5. Tableau de mise à jour

| ID | Contradiction | Statut C0 | Statut C2 (mis à jour) | Justification |
|---|---|---|---|---|
| C5 | Trois chemins racine pour le socle | À ARBITRER (A4) | À ARBITRER | A4 tranche le chemin canonique (`documentation/`) mais ne résout pas explicitement la coexistence des trois chemins dans F1/F2/F3 |
| C6 | Collision `README.md` | À ARBITRER (A4) | Résolu | A4 tranche : `documentation/README.md` pour la documentation, README projet distinct |

---

## 6. Preuves et traçabilité

| Élément | Référence | Statut |
|---|---|---|
| Non-conformité NC-05 identifiée | Rapport C1 (registres C0) | `directly_verified` |
| Contradiction C5 | `00_cartographie.md` §5 (C5) | `directly_verified` |
| Contradiction C6 | `00_cartographie.md` §5 (C6) | `directly_verified` |
| Arbitrage A4 | `00_cartographie.md` §7.2, `terminology.md` §11 | `directly_verified` |
| Registre contradictions C0 | `livrables/C0/registres/registre_contradictions.md` | `directly_verified` |

---

## 7. Conclusion

La non-conformité NC-05 est **documentée** : C6 est maintenant résolue par l'arbitrage A4, tandis que C5 reste à arbitrer pour la coexistence des trois chemins historiques, avec le chemin canonique `documentation/` établi par A4.

**Statut NC-05** : ✅ Documentée — C6 résolue, C5 reste à arbitrer avec justification.

---
*Fin de NC-05. Non-conformité documentée. Toutes les non-conformités NC-01 à NC-05 sont maintenant traitées.*