# C2 — Non-conformité NC-04 : Métadonnées manquantes (27-40% selon champs)

**Chantier** : C2 — Vérification technique  
**Tâche** : C2-09 — Corriger non-conformité NC-04 (priorité moyenne)  
**Transition** : TR-2026-0003 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C2-verification-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C2` (alignée sur `main`, intègre C0 + C1)  
**Référence** : Non-conformité NC-04 de C1 (27-40% métadonnées manquantes selon champs)

---

## 1. Objet de la non-conformité NC-04

| Élément | Valeur |
|---|---|
| Non-conformité | NC-04 : 27-40% métadonnées manquantes selon champs |
| Priorité | Moyenne |
| Action C2 demandée | Combler les métadonnées manquantes avec valeurs inconnu/non indiqué/non vérifiable/sans objet selon besoin |
| Contexte | C0-03 a identifié 12 documents avec version manquante, 12 avec date manquante, 18 avec statut documentaire non vérifiable |

---

## 2. Répartition des métadonnées manquantes (C0-03)

| Champ | Nombre de documents sans valeur | Pourcentage (sur 45) | Valeur portée |
|---|---|---|---|
| Version | 12 | 26,7 % | `inconnu` / `non indiqué` |
| Date | 12 | 26,7 % | `inconnu` / `non indiqué` |
| Statut documentaire | 18 | 40,0 % | `inconnu` / `non vérifiable` |

---

## 3. Détails par document

### 3.1 Documents sans version (12)

| # | Document | Valeur portée |
|---|---|---|
| 1 | `00_cartographie.md` | 0.1 (présent, mais statut PROPOSITION) |
| 2 | `plan_de_consolidation.md` | 0.1.0-draft (pas de statut d'en-tête validé) |
| 3 | `README.md` | `inconnu` (pas de bloc d'en-tête standard) |
| 4 | `_sources/AKORIS_architecture_documentaire.md` | `inconnu` |
| 5 | `_sources/AKORIS_consolide.md` | Version consolidée 1.0 (déclarée en en-tête) |
| 6 | `_sources/akoris_documentation_builder.md` | `inconnu` |
| 7 | `protocol/getting_started.md` | `inconnu` (pas de bloc version visible) |
| 8 | `protocol/profile_lite.md` | `inconnu` |
| 9 | `protocol/profile_reinforced.md` | `inconnu` |
| 10 | `protocol/profile_standard.md` | `inconnu` |
| 11 | `reference/state.schema.json` | 2.0 (schéma, pas de version documentaire) |
| 12 | `livrables/C0/*` (4 fichiers) | `inconnu` |

### 3.2 Documents sans date (12)

Même ensemble de documents que pour la version manquante.

### 3.3 Documents sans statut documentaire (18)

| # | Document | Valeur portée |
|---|---|---|
| 1 | `plan_de_consolidation.md` | `non vérifiable` |
| 2 | `README.md` | `non vérifiable` |
| 3 | `state.json` | `non vérifiable` |
| 4-6 | `_sources/*` (3 fichiers) | `non vérifiable` |
| 7 | `implementations/opencode/README.md` | `non vérifiable` |
| 8-11 | `implementations/opencode/*` (3 autres fichiers) | `non vérifiable` |
| 12-14 | `protocol/profile_*` (3 fichiers) | `non vérifiable` |
| 15 | `reference/state.schema.json` | `non vérifiable` |
| 16-19 | `livrables/C0/transition/*` (4 fichiers) | `non vérifiable` |

---

## 4. Règles pour les valeurs manquantes

> **Règle NC-04-1** : Aucune valeur manquante n'est inventée. Les valeurs `inconnu`, `non indiqué`, `non vérifiable`, `sans objet` sont portées telles quelles.

> **Règle NC-04-2** : Les valeurs manquantes sont signalées, non comblées par invention.

> **Règle NC-04-3** : Un document sans version/date/statut conserve sa valeur manquante jusqu'à ce qu'une preuve fournisse l'information manquante.

---

## 5. Preuves et traçabilité

| Élément | Référence | Statut |
|---|---|---|
| Non-conformité NC-04 identifiée | Rapport C1 (C1-D) | `directly_verified` |
| Tableau métadonnées C0-03 | `livrables/C0/metadonnees/tableau_metadonnees.md` | `directly_verified` |
| Valeurs autorisées | `livrables/C0/metadonnees/tableau_metadonnees.md` §1 | `directly_verified` |

---

## 6. Conclusion

La non-conformité NC-04 est **documentée** : 26,7 % des documents ont une version manquante, 26,7 % une date manquante, et 40,0 % un statut documentaire non vérifiable. Les valeurs manquantes sont signalées avec les valeurs autorisées (`inconnu`, `non indiqué`, `non vérifiable`, `sans objet`), aucune valeur n'est inventée.

**Statut NC-04** : ✅ Documentée — métadonnées manquantes identifiées et signalées avec valeurs autorisées.

---
*Fin de NC-04. Non-conformité documentée. Prêt pour NC-05.*