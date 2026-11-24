# Profil Lite

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | Projets à faible risque, faiblement exposés, réversibles |
| Autorité | Niveau d'exigence |
| Vague | 2 |

**Sources citées :** `F3` = `AKORIS_consolide.md` §4.1 · `F2` = `AKORIS_architecture_documentaire.md` §4.3 · `GC` = `protocol/governance_core.md` · `STD` = `protocol/profile_standard.md`.

---

## 0. Nature du profil

Le profil Lite **allège les exigences procédurales du profil Standard**. Il n'allège jamais le socle : `governance_core.md` s'applique intégralement (`GC-01`, `GC-02`).

Ce fichier se lit **avec** `profile_standard.md` : il n'en répète pas les dispositions communes, il énonce uniquement les **écarts**.

**Disponibilité (A3).** La doctrine maintient les trois profils. Leur disponibilité dans l'implémentation de référence n'est **pas établie** ; voir §9.

---

## 1. Usage et niveau de risque

| Élément | Valeur |
|---|---|
| Usage type | Prototype, projet personnel, outil éducatif, expérimentation |
| Exposition | Faible |
| Réversibilité attendue | R0 (facilement réversible) |
| Données | Aucune donnée sensible |
| Utilisateurs | Restreints, connus |
| Coût d'un échec | Faible et réparable |

---

## 2. Critères de sélection

Le profil Lite est admissible si **toutes** les conditions suivantes sont réunies :

- le logiciel est facilement réversible ;
- l'exposition est faible ;
- aucune donnée sensible n'est traitée ;
- aucun engagement réglementaire, financier, médical ou administratif n'est en jeu ;
- l'échec est sans conséquence grave et réparable simplement.

**Interdiction explicite :** un projet ne peut pas choisir Lite pour éviter un contrôle rendu nécessaire par son niveau de risque. Si un critère du profil Reinforced s'applique, le projet relève de Reinforced, quel que soit son confort.

> **INCONNU.** Aucune échelle de risque chiffrée n'existe dans les sources. L'appréciation reste qualitative et doit être tracée.

---

## 3. Exigences documentaires

| Document | Exigence Lite |
|---|---|
| Cadrage | **Court** — vision, problème, périmètre, exclusions |
| Périmètre | **Explicite et borné** |
| Exigences principales | Obligatoires, sans exhaustivité formelle |
| Décisions techniques importantes | Tracées |
| Mandat de tâche | Obligatoire |
| Architecture détaillée | Non exigée |
| ADR | Non exigés (décisions importantes seulement, sous forme de note) |
| Roadmap | Non exigée |
| Critères d'acceptation | Essentiels, rattachés aux tâches |
| État central | Obligatoire (`state.json`) |
| Rapports | Obligatoires, format allégé |

---

## 4. Exigences de preuve

| Type de critère | Preuve minimale admise |
|---|---|
| Critère essentiel | `directly_verified` ou `reproduced` |
| Critère secondaire | `declared_only` admis, signalé comme tel |
| Critère critique | **Jamais** `declared_only` (`GC-24`) |

Les tests essentiels sont obligatoires. Les tests exhaustifs ne le sont pas.

---

## 5. Validations humaines

| Objet | Exigence Lite |
|---|---|
| Choix du profil | VALIDATOR |
| Checkpoints | **Peuvent être regroupés** |
| Chaque transition | Autorisation VALIDATOR maintenue (`GC-45`) |
| Revue avant livraison | **Obligatoire** |
| Fusion vers `main` | Décision humaine maintenue (`GC-14`) |

Le regroupement des checkpoints allège la **forme**, jamais le **principe** : aucun checkpoint n'est supprimé ; tous sont examinés ensemble.

---

## 6. Audit

| Élément | Exigence Lite |
|---|---|
| Fréquence | **Ciblé** — sur les points à risque, non systématiquement par sprint |
| Objet | Livrable, tests essentiels, périmètre |
| Indépendance | Procédurale (`GC-37`) |
| Règle intangible | **L'agent qui produit le code ne doit pas être l'unique juge de son résultat** (`GC-17`) |
| Rapport | Obligatoire, même court |

Le profil Lite réduit la **couverture** de l'audit. Il ne supprime jamais la **contre-vérification** : un audit réalisé par le producteur seul n'est pas un audit.

---

## 7. Écarts par rapport au profil Standard

| Sujet | Standard | Lite |
|---|---|---|
| Checkpoints | CP1, CP2, CP3 distincts | Regroupables |
| Exigences | Fonctionnelles et non fonctionnelles | Principales seulement |
| Architecture | Obligatoire | Non exigée |
| ADR | Obligatoire | Notes de décision |
| Roadmap | Obligatoire | Non exigée |
| Audit | Chaque sprint | Ciblé |
| Changements | Procédure complète pour les majeurs | Gestion simplifiée |
| Réserves | Registre complet | Registre allégé, réserves tracées |
| Revue avant livraison | Avant fusion | Avant livraison |

---

## 8. Limites du profil

Le profil Lite **ne dispense de rien** en matière de :

- autorité humaine (`GC-04`) ;
- séparation des rôles (`GC-10` à `GC-17`) ;
- traçabilité des décisions structurantes (`GC-29`) ;
- preuve des critères critiques (`GC-24`) ;
- interdiction d'exposer un secret (`GC-33`) ;
- transitions autorisées et reçues (`GC-45`, `GC-47`).

Il n'est **pas** un mode « sans gouvernance ». C'est un mode de gouvernance à faible couverture.

---

## 9. Disponibilité dans l'implémentation de référence

| Élément | Constat |
|---|---|
| Profil déclaré dans `state.json` | Absent du pilote |
| Valeurs de décision | 3 au lieu de 5 |
| Mécanisme de reçu | Présent |
| Conclusion | Aucun profil n'est aujourd'hui **opérationnel** dans le pilote, Lite compris |

---

## 10. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 2) |
