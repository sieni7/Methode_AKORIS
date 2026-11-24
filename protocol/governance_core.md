# AKORIS — Socle de gouvernance

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | Tous les profils (Lite, Standard, Reinforced), toutes les implémentations |
| Autorité | Socle commun obligatoire |
| Vague | 1 |

**Sources citées :** `F3` = `AKORIS_consolide.md` · `F2` = `AKORIS_architecture_documentaire.md` · `F1` = `akoris_documentation_builder.md` · `GS1` = `getting_started.md` du pilote (matériau non doctrinal) · `CART` = `00_cartographie.md`.

---

## 0. Nature de ce document

`governance_core.md` contient les règles qui s'appliquent **quel que soit le profil** et **quel que soit l'outil**.

- Il est **normatif** : les règles numérotées `GC-xx` sont obligatoires.
- Il est **volontairement court** : il énonce des règles, il ne décrit pas les procédures. Les procédures vivent dans les politiques spécialisées.
- Il est **stable** : il ne change qu'avec une décision du VALIDATOR et une entrée de changelog.

Un profil peut **ajouter** des exigences. Aucun profil, aucun projet, aucune implémentation ne peut **retirer** ou **affaiblir** une règle du socle.

---

## 1. Portée et applicabilité

| ID | Règle | Source |
|---|---|---|
| GC-01 | Le socle s'applique à tous les profils et à toutes les implémentations, sans exception. | F3 §4 |
| GC-02 | Un profil peut ajouter des exigences ; il ne peut ni en retirer ni en affaiblir. | F3 §4 |
| GC-03 | En cas de conflit entre le socle et un autre document, le socle prévaut et le conflit est signalé au VALIDATOR. | F3 §5.2 |

---

## 2. Autorité humaine

| ID | Règle | Source |
|---|---|---|
| GC-04 | Le VALIDATOR conserve toujours la décision finale. | F3 §2.15 |
| GC-05 | Une proposition d'IA n'est pas une décision validée. | F3 §2.1 |
| GC-06 | Un rapport positif n'est pas une autorisation de poursuivre. | F3 §2.2 |
| GC-07 | Une acceptation n'autorise ni le sprint suivant, ni la fusion, ni le déploiement, ni l'accès à de nouvelles données, ni une modification d'architecture. | F3 §15 |
| GC-08 | Une autorisation ne porte que sur le périmètre explicitement défini. | F3 §2.9 |
| GC-09 | Le choix du profil appartient au VALIDATOR. Il est enregistré et verrouillé ; sa modification suit la procédure de changement. | F3 §4, F2 §4.8 |

---

## 3. Séparation des rôles et moindre privilège

| ID | Règle | Source |
|---|---|---|
| GC-10 | Chaque rôle n'agit que dans le périmètre de son mandat. | F3 §3, F2 §10 |
| GC-11 | ORCHESTRATOR ne modifie pas le code applicatif pendant un sprint, sauf autorisation explicite prévue par le profil et le mandat. | F3 §3.1 |
| GC-12 | ORCHESTRATOR est le seul rédacteur normal de `state.json`. | F3 §3.1 |
| GC-13 | BUILDER ne modifie ni `state.json`, ni `state.md`, ni le rapport d'audit, ni une décision validée. | F3 §3.2 |
| GC-14 | BUILDER ne fusionne jamais directement vers `main` et n'étend pas silencieusement le périmètre. | F3 §3.2, §16 |
| GC-15 | AUDITOR ne corrige pas le code qu'il audite et ne modifie pas l'état central. | F3 §3.3 |
| GC-16 | Le moindre privilège s'applique à tous les rôles. La matrice contraignante est dans `permission_policy.md`. | F3 §12 |
| GC-17 | L'acteur qui produit un résultat ne peut pas en être l'unique juge. | F3 §4.1, §11 |

---

## 4. Statuts épistémiques

| ID | Règle | Source |
|---|---|---|
| GC-18 | Tout énoncé important porte un statut explicite : `FAIT`, `HYPOTHÈSE`, `RECOMMANDATION`, `À ARBITRER`, `INCONNU`. | F1 §4 |
| GC-19 | Une hypothèse n'est jamais présentée comme un fait. | F3 §2.4 |
| GC-20 | Une information inconnue ne devient jamais une règle officielle. | F1 §4 |
| GC-21 | Une recommandation ne devient une décision que par acte du VALIDATOR, tracé. | F1 §4 |

---

## 5. Preuves

| ID | Règle | Source |
|---|---|---|
| GC-22 | Une affirmation d'agent n'est pas une preuve. | F3 §9 |
| GC-23 | Toute vérification importante est accompagnée d'une preuve classée selon les statuts de preuve. | F3 §2.7, §9 |
| GC-24 | Une preuve `declared_only` ne suffit pas à valider un critère critique. | F3 §9 |
| GC-25 | `NOT_CHECKED` ne vaut jamais `PASS`. | F3 §9 |
| GC-26 | Un contrôle non réalisé est déclaré non réalisé, jamais omis. | F3 §9 |
| GC-27 | Les preuves sont conservées et rattachées au sprint, à la décision et à la transition concernés. | F3 §9, §7 |
| GC-28 | Une preuve ne contient ni secret ni donnée sensible non autorisée. | F3 §2.12 |

---

## 6. Traçabilité

| ID | Règle | Source |
|---|---|---|
| GC-29 | Toute décision structurante est traçable : identifiant, date, auteur, motif, preuve. | F3 §2.6 |
| GC-30 | Toute modification du mandat est signalée et versionnée. | F3 §2.10, §10.5 |
| GC-31 | Toute divergence entre documents est signalée. Elle n'est jamais corrigée silencieusement. | F3 §5.2, F1 §10 |
| GC-32 | Un identifiant consommé, expiré ou annulé n'est jamais réutilisé. | F3 §6.3 |

---

## 7. Sécurité, permissions et honnêteté des garanties

| ID | Règle | Source |
|---|---|---|
| GC-33 | Aucun secret n'apparaît dans un rapport, un commit, un document ou un journal. | F3 §2.12 |
| GC-34 | Les secrets sont recherchés avant commit et avant fusion. | F3 §16 |
| GC-35 | Une anomalie touchant la sécurité, les données ou un secret relève au minimum de S0. | F3 §8.2 |
| GC-36 | Les permissions déclarées sont distinguées des permissions réellement imposées. `unknown` n'est jamais présenté comme une garantie. | F3 §2.13, §12 |
| GC-37 | L'indépendance d'audit est procédurale par défaut. Elle n'est dite technique que si l'environnement l'impose réellement et si c'est prouvé. | F3 §3.3 |
| GC-38 | Les limites de l'environnement sont déclarées dans la documentation de l'implémentation. | F1 §13, F2 §12 |
| GC-39 | Aucun contrôle n'est déclaré réussi sans preuve. | F3 §9, F2 §12 |
| GC-40 | Aucun contrôle procédural n'est présenté comme technique. | F1 §14 |

> **Portée de GC-36.** L'existence d'une configuration de permissions dans un fichier ne prouve pas son application. La classification `technical_enforced` exige une vérification effective et une trace. Voir `permission_policy.md` (vague 3) et `implementations/opencode/agent_permissions.md` (vague 3).

---

## 8. Anomalies et violations

| ID | Règle | Source |
|---|---|---|
| GC-41 | Toute anomalie est signalée. Aucune n'est supprimée pour améliorer un rapport. | F3 §2.8, F2 §12 |
| GC-42 | Une anomalie est qualifiée avant toute décision. La qualification est définie dans `decision_policy.md`. | F3 §8.2 |
| GC-43 | Une violation de permission est arrêtée, conservée, identifiée, évaluée, auditée, rattachée à une décision, puis corrigée ou acceptée explicitement. | F3 §13 |
| GC-44 | Une violation peut invalider un résultat même si le code fonctionne. | F3 §13 |

---

## 9. Transitions

| ID | Règle | Source |
|---|---|---|
| GC-45 | Aucune action opérationnelle n'est engagée sans transition identifiée et autorisée. | F3 §6, §14 |
| GC-46 | Une transition terminée, consommée, expirée ou annulée n'est jamais réactivée. Une nouvelle action exige un nouvel identifiant. | F3 §6.3 |
| GC-47 | La consommation d'une autorisation est prouvée par un reçu de transition. | `transition_policy.md` §5 ; décision VALIDATOR **A2** |
| GC-48 | Un identifiant de transition n'est pas une preuve cryptographique. | F3 §2.3 |
| GC-49 | Aucune transition opérationnelle n'est déclenchée avant validation du checkpoint concerné. | F3 §14 |

---

## 10. Documentation

| ID | Règle | Source |
|---|---|---|
| GC-50 | Chaque information possède une source principale unique, recensée dans `reference/document_map.md`. | F3 §5.2, F2 §9 |
| GC-51 | Les autres documents résument et référencent ; ils ne recopient pas la source. | F1 §10 |
| GC-52 | Un modèle ne contient aucune décision propre à un projet. | F2 §8.3 |
| GC-53 | Un exemple est signalé comme exemple et n'est jamais une valeur à réutiliser automatiquement. | F1 §9 |
| GC-54 | Les règles du cadre ne sont jamais mélangées à l'état d'un projet particulier. | F1 §9 |

---

## 11. Ce que ce document ne contient pas

Ce document renvoie explicitement, pour éviter la duplication :

| Sujet | Document responsable |
|---|---|
| Définition des termes | `reference/terminology.md` |
| Niveau d'exigence par profil | `protocol/profile_lite.md`, `profile_standard.md`, `profile_reinforced.md` |
| États, invariants et schéma de `state.json` | `protocol/state_model.md` |
| Transitions, reçus, consommation, expiration | `protocol/transition_policy.md` |
| Valeurs de décision, gravités, critères, réserves | `protocol/decision_policy.md` |
| Changements, impact, urgence | `protocol/change_control.md` |
| Méthode d'audit, rapport, désaccords | `protocol/audit_policy.md` |
| Matrice des permissions et vérification | `protocol/permission_policy.md` |
| Blocage, reprise, rollback, incident | `protocol/recovery_policy.md` |
| Configuration OpenCode | `implementations/opencode/` |
| Carte des documents et de leurs dépendances | `reference/document_map.md` |
| Cycle de vie du cadre | `protocol/getting_started.md` |

---

## 12. Conformité minimale

Un projet est **conforme au socle** si, et seulement si, les dix points suivants sont établis et prouvés :

1. Le profil est choisi, enregistré et verrouillé par le VALIDATOR. *(GC-09)*
2. Chaque rôle agit dans un mandat explicite et versionné. *(GC-10, GC-30)*
3. Aucune action opérationnelle n'a eu lieu sans transition autorisée. *(GC-45)*
4. La consommation de chaque autorisation est prouvée par un reçu. *(GC-47)*
5. Les affirmations importantes sont classées et les preuves référencées. *(GC-18, GC-23)*
6. Aucun `NOT_CHECKED` n'a été compté comme `PASS`. *(GC-25)*
7. Les anomalies sont signalées et qualifiées, y compris celles qui dégradent le résultat. *(GC-41, GC-42)*
8. Les permissions sont classées, et `technical_enforced` n'est employé qu'après vérification. *(GC-36)*
9. Aucun secret n'a été exposé. *(GC-33)*
10. Les divergences documentaires constatées sont signalées. *(GC-31)*

Un point non établi n'est pas « probablement conforme » : il est **non établi**.

---

## 13. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 1) — 54 règles issues de F3 §2-16 et F1 §4-14 |
