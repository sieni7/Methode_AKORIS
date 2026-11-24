# C2 — Réserve R1 : Frontière C0-07 / C0-09

**Chantier** : C2 — Vérification technique  
**Tâche** : C2-01 — Traiter réserve R1 (priorité moyenne)  
**Transition** : TR-2026-0003 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C2-verification-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C2` (alignée sur `main`, intègre C0 + C1)  
**Référence** : Réserve R1 de C0 (état.json `last_decision.reserves`)

---

## 1. Objet de la réserve R1

| Élément | Valeur |
|---|---|
| Réserve | R1 : Frontière C0-07 / C0-09 — distinction lacunes/questions/dépendances vs statuts documentaires |
| Gravité | S2 |
| Consigne C0 | Maintenir sans chevauchement pendant l'exécution |
| Problème | Risque de chevauchement conceptuel entre les tâches C0-07 (lacunes/questions/dépendances) et C0-09 (statuts documentaires) |

---

## 2. Analyse de la frontière

### 2.1 C0-07 — Lacunes, questions et dépendances

C0-07 identifie trois types d'objets :

| Objet | Définition | Exemple |
|---|---|---|
| Lacune | Sujet non couvert par le corpus | Registre des décisions (`decision_log.md`) absent |
| Question ouverte | Interrogation sur le sens ou l'application d'une règle | Échelle de risque chiffrée (C25) |
| Dépendance | Lien de reliance entre deux documents ou avec une entité externe | `state.json` dépend de `state.schema.json` |

**Caractéristique** : Aucun des trois n'est une caractéristique d'un document particulier. Ce sont des sujets, des interrogations ou des liens qui traversent le corpus.

### 2.2 C0-09 — Statuts documentaires

C0-09 attribue un statut à chaque document du corpus :

| Statut | Définition | Exemple |
|---|---|---|
| Approuvé | Document validé par le VALIDATOR | `getting_started.md` (V7) |
| Proposé | Document en attente de validation | `governance_core.md` |
| Non vérifié | Statut non établi à partir des sources | `state.json` |

**Caractéristique** : Chaque document du corpus reçoit exactement un statut. C'est une propriété du document, pas un sujet transversal.

---

## 3. Clarification de la frontière

| Dimension | C0-07 (Lacunes/Questions/Dépendances) | C0-09 (Statuts documentaires) |
|---|---|---|
| **Objet** | Sujets, interrogations, liens transversaux | Caractéristique de chaque document |
| **Unité d'analyse** | Sujet ou question (peut concerner plusieurs documents) | Document individuel (un seul statut par document) |
| **Statut attribué** | Aucun statut documentaire | Approuvé / Proposé / Obsolète / Retiré / Non vérifié |
| **Chevalau possible** | Un document peut être à la fois une lacune et avoir un statut | Un document avec statut "non vérifié" peut aussi être identifié comme lacune |

### 3.3 Règle de séparation

Pour éviter tout chevauchement :

> **Règle R1-1** : Un document du corpus reçoit exactement un statut documentaire (C0-09). Ce statut est indépendant de tout sujet, question ou dépendance dans lequel le document pourrait être impliqué (C0-07).

> **Règle R1-2** : Une lacune, une question ou une dépendance (C0-07) peut concerner un document quel que soit son statut documentaire (C0-09). Par exemple, un document "Approuvé" peut toujours faire l'objet d'une question ouverte.

> **Règle R1-3** : Le statut "non vérifié" (C0-09) ne signifie pas que le document est une lacune (C0-07). "Non vérifié" signifie que le statut documentaire n'a pas pu être établi ; "lacune" signifie qu'un sujet n'est pas couvert par le corpus.

---

## 4. Preuves et traçabilité

| Élément | Référence | Statut |
|---|---|---|
| Réserve R1 définie | `state.json` `last_decision.reserves` | `directly_verified` |
| C0-07 — Lacunes/questions/dépendances | `livrables/C0/lacunes/liste_lacunes.md`, `questions_questions.md`, `dependances_carte.md` | `directly_verified` |
| C0-09 — Statuts documentaires | `livrables/C0/stats_doc/tableau_statu.md` | `directly_verified` |
| Séparation des tâches C0 | `livrables/C0/mandat_builder.md` §2 | `directly_verified` |

---

## 5. Conclusion

La réserve R1 est **clarifiée** : la frontière entre C0-07 et C0-09 est maintenue sans chevauchement. Les deux tâches traitent des objets distincts (sujets/questions/dépendances vs statuts documentaires) et peuvent coexister sans contradiction.

**Statut R1** : ✅ Clarifiée — pas de chevauchement conceptuel résiduel.

---
*Fin de R1. Réserve clarifiée et documentée. Prêt pour R2.*