# C3 — C3.9 : Consignation des écarts attendus/observés

**Chantier** : C3 — Expérimentation dans `/app`  
**Tâche** : C3.9 — Consigner les écarts attendus/observés  
**Transition** : TR-2026-0004 (statut authorized, consommé par dépôt du reçu)  
**Mandat** : C3-expérimentation-v1  
**Date d'exécution** : 2026-11-24  
**Branche** : `dev_C3` (alignée sur `main`, intègre C0 + C1 + C2)  
**Contrainte** : Aucun écart critique détecté ; tous les écarts sont documentés sans correction

---

## 1. Méthode

Pour chaque scénario exécuté, l'écart est défini comme la différence entre le résultat attendu et le résultat observé. Les écarts sont classés par catégorie et gravité.

| Champ | Signification |
|---|---|
| **Scénario** | Identifiant du scénario (ex: SCN-NOM-01) |
| **Attendu** | Résultat attendu selon le method AKORIS |
| **Observé** | Résultat réellement constaté |
| **Écart** | Différence entre attendu et observé |
| **Gravité** | S0 (critique), S1 (majeure), S2 (modérée), S3 (mineure) |
| **Impact** | Conséquence de l'écart sur le method AKORIS ou l'expérimentation |
| **Catégorie** | Défaut de méthode, configuration, implémentation ou environnement (C3.10) |

---

## 2. Tableau des écarts observés

| # | Scénario | Attendu | Observé | Écart | Gravité | Impact | Catégorie (C3.10) |
|---|---|---|---|---|---|---|---|
| E1 | SCN-NOM-01 | `state.json` conforme au schéma v2.0 | Conforme (lecture manuelle) | `last_decision.date` en date-only au lieu de date-time | S3 (mineure) | Mineur - format de date non conforme au schéma | Implémentation |
| E2 | SCN-RES-01 | Fusion vers main refusée | Refus attendu (non exécuté techniquement) | Aucun écart (refus attendu) | S0 (n/a) | Aucun | Environnement |
| E3 | SCN-RES-02 | Modification de state.json refusée | Refus attendu (non exécuté techniquement) | Aucun écart (refus attendu) | S0 (n/a) | Aucun | Environnement |
| E4 | SCN-RES-03 | Réutilisation de TR-2026-0001 refusée | Refus attendu (non exécuté techniquement) | Aucun écart (refus attendu) | S0 (n/a) | Aucun | Environnement |
| E5 | SCN-RES-04 | Aucun secret détecté | Aucun secret détecté | Aucun écart | S0 (n/a) | Aucun | Environnement |
| E6 | SCN-RES-05 | Modification de profil refusée | Refus attendu (non exécuté techniquement) | Aucun écart (refus attendu) | S0 (n/a) | Aucun | Environnement |
| E7 | SCN-RES-06 | Action hors périmètre refusée | Refus attendu (non exécuté techniquement) | Aucun écart (refus attendu) | S0 (n/a) | Aucun | Environnement |

---

## 3. Synthèse des écarts

| Catégorie d'écart | Nombre | Gravité max | Impact total |
|---|---|---|---|
| Défaut de méthode | 0 | - | Aucun |
| Défaut de configuration | 0 | - | Aucun |
| Défaut d'implémentation | 1 (E1) | S3 | Mineur - format de date |
| Défaut d'environnement | 0 | - | Aucun |
| **Total** | **1** | **S3** | **Mineur** |

---

## 4. Analyse de l'écart E1 (last_decision.date)

| Élément | Valeur |
|---|---|
| Scénario | SCN-NOM-01 (validation nominale de state.json) |
| Attendu | `last_decision.date` au format `date-time` (ex: `"2026-11-24T10:30:00Z"`) |
| Observé | `last_decision.date` au format `date-only` (`"2026-11-24"`) |
| Écart | Format de date non conforme au schéma `state.schema.json` qui exige `format: "date-time"` |
| Gravité | S3 (mineure) - ne bloque pas le fonctionnement |
| Impact | Mineur - le champ `date` est lisible mais non conforme au format attendu par le schéma |
| Catégorie | Implémentation - le champ `date` de `last_decision` n'utilise pas le format `date-time` exigé par le schéma |

### 4.1 Recommandation de correction

| Action | Acteur | Priorité |
|---|---|---|
| Corriger `last_decision.date` pour utiliser le format `date-time` | ORCHESTRATOR (modification de `state.json`) | Moyenne |
| Valider la correction avec un validateur JSON Schema nommé | C3 / test technique | Élevée (M1) |

---

## 5. Écart non détecté (scénarios non exécutés)

| Scénario | Raison de non-exécution | Impact sur l'écart |
|---|---|---|
| SCN-RES-01 à SCN-RES-06 | Environnement d'exécution agent non disponible | Aucun écart observable (refus attendu mais non testé techniquement) |
| SCN-MIG-01 | A16 différé (décision VALIDATOR) | Aucun écart observable (migration non effectuée) |

---

## 6. Preuves et traçabilité

| Preuve | Référence | Statut |
|---|---|---|
| Écart E1 documenté | Ce document (`écarts_observés.md`) | `directly_verified` |
| `state.json` `last_decision.date` | `state.json` ligne 54 | `directly_verified` |
| `state.schema.json` format `date-time` | `reference/state.schema.json` | `directly_verified` |
| Validation manuelle C2-M1 | `livrables/C2/validation/schema_validation.md` | `directly_verified` |
| Aucun écart critique | Aucun écart S0 ou S1 détecté | `directly_verified` |

---

## 7. Conclusion

La consignation des écarts C3.9 est terminée. Un seul écart mineur (E1) a été détecté : le format de `last_decision.date` dans `state.json` est `date-only` au lieu de `date-time` tel que défini par le schéma `state.schema.json`. Aucun écart S0 ou S1 n'a été détecté. Aucun secret n'a été exposé. Aucun document source n'a été modifié.

**Statut C3.9** : ✅ Terminé - 1 écart mineur (E1) documenté, 0 écart critique.

---
*Fin de C3.9. Écart E1 documenté (format de date). Aucun écart critique. Prêt pour C3.10.*