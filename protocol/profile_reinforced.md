# Profil Reinforced

| Champ | Valeur |
|---|---|
| Version | 0.1 |
| Date | 2026-11-20 |
| Statut | **PROPOSITION — à valider par le VALIDATOR** |
| Portée | Projets sensibles, critiques, réglementés ou difficilement réversibles |
| Autorité | Niveau d'exigence |
| Vague | 2 |

**Sources citées :** `F3` = `AKORIS_consolide.md` §4.3 · `F2` = `AKORIS_architecture_documentaire.md` §4.5 · `GC` = `protocol/governance_core.md` · `STD` = `protocol/profile_standard.md`.

---

## 0. Nature du profil

Le profil Reinforced **ajoute des exigences au profil Standard**. Il n'en retire aucune.

Ce fichier se lit **avec** `profile_standard.md` : toutes les exigences Standard s'appliquent, et ce document n'énonce que les **ajouts**.

**Disponibilité (A3).** La doctrine maintient les trois profils. Leur disponibilité dans l'implémentation de référence n'est **pas établie** ; voir §11.

---

## 1. Usage et niveau de risque

| Élément | Valeur |
|---|---|
| Usage type | Système traitant des données sensibles, soumis à des obligations, ou critique |
| Exposition | Élevée, publique ou réglementée |
| Réversibilité attendue | R2 à R3 (migration lourde à irréversible) |
| Données | Sensibles, personnelles, financières, médicales ou administratives |
| Coût d'un échec | Élevé, potentiellement irréparable |
| Tolérance à l'incertitude | Faible |

---

## 2. Critères de sélection

Le profil Reinforced s'applique dès qu'**un seul** des critères suivants est présent :

- manipulation de données sensibles ;
- soumission à des obligations réglementaires ;
- exposition à un risque financier, médical ou administratif ;
- difficulté ou impossibilité de restauration ;
- exposition large au public ;
- opérations irréversibles ;
- dépendance à une infrastructure critique.

Le profil est **cumulatif** : un seul critère suffit. En cas de doute, le niveau supérieur s'applique.

---

## 3. Exigences supplémentaires — sécurité et données

| Exigence | Contenu |
|---|---|
| Classification des données | Inventaire des données, niveaux de sensibilité, règles d'accès |
| Analyse de sécurité | Menaces, surfaces d'attaque, contrôles retenus, risques acceptés |
| Contrôle des dépendances | Origine, version, vulnérabilités connues, politique de mise à jour |
| Gestion des secrets | Stockage, rotation, révocation, absence dans le dépôt |
| Journalisation | Traces d'accès et d'actions sensibles, conservation définie |

L'analyse de sécurité est un livrable attendu, pas une intention.

---

## 4. Exigences supplémentaires — réversibilité

| Exigence | Contenu |
|---|---|
| Sauvegarde | Fréquence, périmètre, intégrité, conservation |
| Restauration | Procédure testée, durée cible, responsable |
| Stratégie de rollback | Conditions de déclenchement, procédure, validation |
| Preuve de restauration | Test réalisé et daté — pas une procédure déclarée |

Une stratégie de rollback non testée est un `declared_only` : elle ne vaut pas preuve pour un critère critique.

---

## 5. Exigences supplémentaires — preuves et audit

| Élément | Exigence Reinforced |
|---|---|
| Preuves | **Reproductibles** — une tierce partie doit pouvoir refaire le contrôle |
| Audit | Chaque sprint **et** audit complet des exigences critiques |
| Éléments non vérifiés | Déclarés explicitement, avec justification |
| Risques résiduels | Analysés et acceptés par le VALIDATOR |
| Mesures compensatoires | Obligatoires si une protection technique est absente |
| Violation de permission | Peut invalider le résultat même si le code fonctionne (`GC-44`) |

---

## 6. Exigences supplémentaires — autorisations

| Élément | Exigence Reinforced |
|---|---|
| Autorisations | **Versionnées** et, si pertinent, **expirantes** |
| Portée | Minimale et explicitement bornée |
| Révocation | Possible à tout moment, tracée |
| Réutilisation | Impossible ; tout rejeu est une violation |
| Durée | Limitée, avec expiration vérifiable |

L'expiration n'est pas une commodité : c'est un contrôle qui réduit la fenêtre d'exploitation d'une autorisation oubliée.

---

## 7. Validations humaines renforcées

En plus des validations Standard :

| Objet | Exigence |
|---|---|
| Analyse de sécurité | Validation explicite avant CP3 |
| Stratégie de sauvegarde et de rollback | Validation explicite avant CP3 |
| Risques résiduels | Acceptation explicite, nominative, datée |
| Mesures compensatoires | Validation explicite |
| Opération irréversible | Autorisation distincte, postérieure à l'audit |
| Déploiement | Autorisation distincte, jamais groupée avec l'acceptation |

---

## 8. Écarts par rapport au profil Standard

| Sujet | Standard | Reinforced |
|---|---|---|
| Classification des données | — | Obligatoire |
| Analyse de sécurité | — | Obligatoire |
| Sauvegarde / restauration | — | Obligatoire et testée |
| Rollback | — | Obligatoire et testé |
| Preuves | Vérifiées ou reproduites | **Reproductibles** |
| Audit | Chaque sprint | Chaque sprint + exigences critiques |
| Autorisations | Simples | Versionnées, expirantes |
| Risques résiduels | Suivi | Analysés et acceptés |
| Mesures compensatoires | — | Obligatoires si protection absente |
| Dépendances | — | Contrôlées |

---

## 9. Limites du profil

- Le profil Reinforced **n'élimine pas le risque** : il le rend visible et traité.
- Il ne remplace ni l'expertise sécurité, ni l'expertise juridique, ni l'audit externe lorsqu'ils sont requis.
- Il ne garantit aucune conformité réglementaire : la conformité se démontre par référence à un texte, pas par l'application d'un profil.
- Il augmente le coût et la durée ; ce coût ne justifie jamais un déclassement.

---

## 10. Ce que le profil n'autorise pas

- Déclasser un projet vers Standard ou Lite pour tenir un délai.
- Déclarer une sauvegarde « en place » sans test de restauration.
- Accepter un risque résiduel sans décision humaine tracée.
- Remplacer une mesure compensatoire par une déclaration d'intention.
- Grouper l'acceptation du sprint et l'autorisation de déploiement.

---

## 11. Disponibilité dans l'implémentation de référence

| Élément | Constat |
|---|---|
| Profil déclaré dans `state.json` | Absent du pilote |
| Classification des données | Absente |
| Analyse de sécurité | Absente (`docs/security/` existe, sans analyse formelle) |
| Sauvegarde / rollback | Absents |
| Autorisations expirantes | Absentes — aucune date d'expiration dans les transitions du pilote |
| Conclusion | Le pilote **ne satisfait pas** le profil Reinforced |

---

## 12. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 2) |
