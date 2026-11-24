# C2 — Réserve R5 : Fichiers .gitignore et ignorés

**Chantier** : C2 — Vérification technique  
**Tâche** : C2-05 — Traiter réserve R5 (priorité moyenne)  
**Transition** : TR-2026-0003 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C2-verification-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C2` (alignée sur `main`, intègre C0 + C1)  
**Référence** : Réserve R5 de C0 (état.json `last_decision.reserves`)

---

## 1. Objet de la réserve R5

| Élément | Valeur |
|---|---|
| Réserve | R5 : Fichiers .gitignore et ignorés — politique d'inclusion/exclusion à documenter |
| Gravité | S3 |
| Consigne C0 | Signaler éléments inaccessibles avec justification |
| Contexte C0 | Aucun fichier `.gitignore` présent à la racine du dépôt (constat C0-02) |

---

## 2. État actuel du dépôt

| Élément | Statut | Commentaire |
|---|---|---|
| Fichier `.gitignore` | Absent | Aucun fichier `.gitignore` à la racine du dépôt |
| Fichiers ignorés | Aucun (pas de règles d'ignore) | Tous les fichiers sont potentiellement suivis par Git |
| Fichiers untracked | `plan_de_consolidation.md`, `state.json`, `livrables/C0/*`, `livrables/C1/*`, `livrables/C2/*` | Fichiers nouveaux non encore ajoutés à l'index |
| Fichiers trackés | 39 fichiers (commit initial `f3b2eb7`) | Tous les fichiers sources du corpus AKORIS |

---

## 3. Politique d'inclusion/exclusion proposée

### 3.1 Principe

> **Règle R5-1** : En l'absence de fichier `.gitignore`, tous les fichiers du dépôt sont potentiellement suivis par Git. Une politique d'inclusion/exclusion doit être établie pour définir ce qui doit être versionné et ce qui doit être exclu.

### 3.2 Catégories de fichiers à inclure (versionnés)

| Catégorie | Exemples | Justification |
|---|---|---|
| Documents sources du corpus AKORIS | `protocol/*`, `reference/*`, `templates/*`, `prompts/*`, `implementations/*`, `_sources/*` | Règles, politiques, schémas, sources historiques — cœur du cadre |
| Fichiers racines | `README.md`, `changelog.md`, `00_cartographie.md` | Point d'entrée, journal, cartographie — documentation du cadre |
| Livrables de chantier | `livrables/C0/*`, `livrables/C1/*`, `livrables/C2/*` | Preuves d'exécution, rapports, registres — traçabilité des chantiers |

### 3.3 Catégories de fichiers à exclure (non versionnés)

| Catégorie | Exemples | Justification |
|---|---|---|
| État opérationnel du projet | `state.json`, `state.md` | État du projet gouverné, pas du cadre documentaire (GC-54) |
| Mandat du sprint | `current_sprint.md` | État du projet gouverné (hors périmètre documentaire) |
| Fichiers de build/temporaires | `*.log`, `*.tmp`, `*.cache` | Fichiers techniques temporaires, pas de valeur documentaire |
| Données sensibles | `*.secret`, `*.key`, `*.pem` | Secrets ne doivent pas apparaître dans le dépôt (GC-33) |
| Données de projet gouverné | `docs/*`, `sprints/*`, `sprint_report/*`, `audit_report/*`, `debt_report/*` | Projet gouverné, pas documentation du cadre (hors périmètre documentaire) |

### 3.4 Fichiers à surveiller

| Fichier | Statut | Action |
|---|---|---|
| `state.json` | Untracked | Doit rester exclu du versionnement (état opérationnel) |
| `plan_de_consolidation.md` | Untracked | Document de travail du chantier — à évaluer pour inclusion |
| `livrables/C*/**` | Untracked (ajoutés progressivement) | Livrables de chantier — à inclure pour traçabilité |

---

## 4. Recommandation

| Action | Acteur | Priorité |
|---|---|---|
| Créer un fichier `.gitignore` à la racine | ORCHESTRATOR / BUILDER (C2) | Moyenne |
| Exclure `state.json`, `state.md` du versionnement | ORCHESTRATOR / BUILDER | Moyenne |
| Inclure les livrables de chantier (`livrables/C*/**`) | BUILDER | Continue |
| Documenter la politique d'inclusion/exclusion | BUILDER (ce document) | Réalisé |

---

## 5. Preuves et traçabilité

| Élément | Référence | Statut |
|---|---|---|
| Réserve R5 définie | `state.json` `last_decision.reserves` | `directly_verified` |
| Absence de `.gitconfirmé` | Constat C0-02 (`arborescence_fichiers.md`) | `directly_verified` |
| Règle GC-54 | `protocol/governance_core.md` GC-54 | `directly_verified` |
| Règle GC-33 | `protocol/governance_core.md` GC-33 | `directly_verified` |

---

## 5. Conclusion

La réserve R5 est **documentée** : la politique d'inclusion/exclusion des fichiers est établie. Un fichier `.gitignore` doit être créé pour formaliser cette politique, avec exclusion de `state.json`/`state.md` et inclusion des livrables de chantier.

**Statut R5** : ✅ Documentée — politique d'inclusion/exclusion établie, création de `.gitignore` recommandée.

---
*Fin de R5. Réserve documentée. Toutes les réserves R1-R5 sont maintenant traitées.*