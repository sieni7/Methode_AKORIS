# C0-01 — État Git du dépôt AKORIS

**Tâche** : C0-01 — Vérifier dépôt, branche, commit initial et état Git  
**Date d'exécution** : 2026-11-24  
**Branche de travail** : `dev_C0` (créée depuis `main` vérifié)  
**Contrainte** : Lecture seule — aucun document source modifié

---

## 1. Dépôt et branche

| Élément | Valeur constatée | Preuve |
|---|---|---|
| Dépôt racine | `C:\Methode_AKORIS` | `git status`, `git rev-parse` |
| Branche courante | `dev_C0` | `git branch -a` |
| Branche `main` | Présente, pointe sur le commit initial | `git rev-parse main` |
| Branche `remotes/origin/main` | Présente, pointe sur le commit initial | `git branch -a` |
| Commit HEAD (`dev_C0`) | `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea` | `git rev-parse HEAD` |
| Commit `main` | `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea` | `git rev-parse main` |
| Commit initial attendu | `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea` | Mandat C0-revise-v1 |

**Constat** : `dev_C0`, `main` et `remotes/origin/main` pointent tous sur le même commit initial `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea` (`docs(init): import existing AKORIS corpus`). Le commit initial exigé par le mandat est présent et vérifié.

---

## 2. Historique des commits

```
f3b2eb7 docs(init): import existing AKORIS corpus
```

Un seul commit existe dans l'historique : le commit initial d'import du corpus AKORIS. Aucun autre commit n'a été effectué sur aucune branche.

---

## 3. État du working tree (`git status`)

```
On branch dev_C0
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	livrables/
	plan_de_consolidation.md
	state.json

nothing added to commit but untracked files present
```

**Interprétation** :
- Aucune modification de fichier suivi (tracked) n'est présente.
- Trois éléments sont non suivis (untracked) :
  1. `livrables/` — répertoire de livrables C0 (créé dans le cadre du présent mandat, contenu nouveau, aucune source modifiée)
  2. `plan_de_consolidation.md` — fichier racine, non suivi, daté 2026-11-24
  3. `state.json` — fichier racine, non suivi, daté 2026-11-24

**Constat** : Le working tree ne contient aucune modification de document source par rapport au commit initial. Les fichiers sources trackés (39 fichiers dans le commit `f3b2eb7`) sont inchangés.

---

## 4. Fichiers trackés dans le commit initial

39 fichiers sont trackés dans le commit `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea`, répartis comme suit :

| Répertoire | Nombre de fichiers |
|---|---|
| Racine | 3 (`00_cartographie.md`, `README.md`, `changelog.md`) |
| `_sources/` | 3 |
| `implementations/opencode/` | 5 |
| `prompts/` | 4 |
| `protocol/` | 12 |
| `reference/` | 5 |
| `templates/` | 7 |
| **Total** | **39** |

---

## 5. Conclusion C0-01

- Le dépôt existe et est accessible.
- La branche `main` est vérifiée et pointe sur le commit initial `f3b2eb73a738be726cbc5b1a72ceafbe9d1712ea`.
- La branche `dev_C0` est créée depuis `main` et pointe sur le même commit.
- Aucun document source n'a été modifié (lecture seule respectée).
- L'état Git est documenté ; ce fichier (`etat_git.md`) constitue la preuve C0-01.

---
*Fin de C0-01. État figé à la date d'exécution : 2026-11-24.*