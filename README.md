# AKORIS — Documentation

> **Adaptive Knowledge and Orchestrated Reviews for Iterative Systems**
> Cadre de gouvernance et de contrôle du développement assisté par IA.

**L'IA propose. Les contrôles vérifient. L'humain décide.**

---

## ⚠ État de la documentation

| Indicateur | Valeur |
|---|---|
| Documents produits | **34 / 34** |
| Vague en cours | Vague 7 close — 3 livrables validés le 2026-11-21 ; reste du corpus en attente de validation du VALIDATOR |
| Documents normatifs disponibles | socle, profils, état, transitions, permissions, décisions, changements, reprises, audit, versionnement |
| Dernière mise à jour | 2026-11-21 |

**Les 34 documents cibles sont produits**, y compris les trois livrables de la vague 7 : [guide de démarrage](protocol/getting_started.md), [carte de traçabilité](reference/traceability_map.md) et [politique de versionnement](reference/versioning_policy.md). Ces trois livrables portent le statut **VALIDÉ PAR LE VALIDATOR — 2026-11-21** ; le reste du corpus demeure soumis à son statut propre. Cette validation partielle ne vaut ni validation générale du corpus ni autorisation d'exécution. Les registres, l'état et les preuves du projet gouverné ne font pas partie de ce dépôt. Un lecteur ne doit pas en déduire que le cadre est opérationnel, que des tests T1 à T5 ont été exécutés ou qu'une permission est certifiée.

L'état détaillé, fichier par fichier, se trouve dans la [carte documentaire](reference/document_map.md).

---

## 1. Qu'est-ce qu'AKORIS

AKORIS est un cadre de gouvernance, de contrôle et de traçabilité destiné aux projets développés avec l'assistance d'agents d'intelligence artificielle.

Il organise la compréhension du besoin, la formalisation des décisions, la préparation des tâches, l'exécution, la vérification indépendante, la gestion des changements, la conservation des preuves et la décision humaine.

AKORIS **ne remplace pas** l'expertise métier, technique, juridique ou de sécurité. Il structure les décisions et réduit les erreurs non détectées. Il ne garantit rien par lui-même : les garanties dépendent de l'environnement, et elles doivent être vérifiées, pas supposées.

Le cadre est **agnostique de l'outil**. OpenCode en est l'implémentation de référence, documentée séparément.

---

## 2. À qui s'adresse cette documentation

| Lecteur | Ce qu'il y trouve |
|---|---|
| Décideur / VALIDATOR | Ce qu'il doit valider, quand, et sur quelles preuves |
| ORCHESTRATOR | Cadrage, mandats, transitions, état opérationnel |
| BUILDER | Périmètre autorisé, preuves attendues, rapport |
| AUDITOR | Méthode de contre-vérification, limites, désaccord |
| Rédacteur documentaire | Structure, sources uniques, règles de non-duplication |
| Lecteur curieux | Le cadre, ses principes, son vocabulaire |

---

## 3. Par où commencer

| Parcours | Ordre de lecture |
|---|---|
| **Découvrir** | ce README → [terminology](reference/terminology.md) → [governance_core](protocol/governance_core.md) → [document_map](reference/document_map.md) → [guide de démarrage](protocol/getting_started.md) |
| **Appliquer** | [governance_core](protocol/governance_core.md) → [profil actif](protocol/profile_standard.md) → [modèle d'état](protocol/state_model.md) → [transitions](protocol/transition_policy.md) → [permissions](protocol/permission_policy.md) → prompt du rôle *(v6)* |
| **Maintenir** | [carte documentaire](reference/document_map.md) → [cartographie](00_cartographie.md) → [carte de traçabilité](reference/traceability_map.md), [politique de versionnement](reference/versioning_policy.md) *(v7)* → `changelog.md` |

Un seul point d'entrée par parcours. Aucun document ne doit être lu hors de son contexte : les dépendances sont décrites dans la [carte documentaire](reference/document_map.md).

---

## 4. Organisation des dossiers

```text
documentation/
├── protocol/           normes : socle, profils, politiques, manuel
├── implementations/    configuration et limites d'un environnement donné
├── prompts/            amorçage opérationnel de chaque rôle
├── templates/          modèles de livrables, sans décision de projet
└── reference/          vocabulaire, carte, traçabilité, versionnement
```

| Dossier | Question à laquelle il répond | Nature |
|---|---|---|
| `protocol/` | *Que faut-il faire, et à quel niveau d'exigence ?* | Normatif |
| `implementations/` | *Qu'est-ce que cet environnement garantit réellement ?* | Descriptif |
| `prompts/` | *Par où un rôle commence-t-il ?* | Opératoire |
| `templates/` | *Sous quelle forme livrer ?* | Formel |
| `reference/` | *Où est l'information, et comment la nommer ?* | Référentiel |

**Séparation essentielle :** `protocol/` dit ce qui est **exigé**. `implementations/` dit ce qui est **réellement obtenu**. Confondre les deux produit une fausse impression de sécurité.

---

## 5. Les rôles

| Rôle | Nature | Fonction | Document |
|---|---|---|---|
| **ORCHESTRATOR** | Agent | Cadre, prépare les décisions et mandats, gère l'état et les transitions | [guide de démarrage](protocol/getting_started.md) *(v7)* |
| **BUILDER** | Agent | Exécute le mandat autorisé, teste, commite, fournit les preuves | [prompts/akoris_builder_bootstrap.md](prompts/akoris_builder_bootstrap.md) *(v6)* |
| **AUDITOR** | Agent | Vérifie directement le résultat, sans le corriger | `protocol/audit_policy.md` *(v5)* |
| **VALIDATOR** | **Humain** | Décide, autorise, accepte, arbitre. Autorité finale | [governance_core](protocol/governance_core.md) §2 |
| DOCUMENTATION BUILDER | Rôle auxiliaire | Rédige et maintient cette documentation | **Tranché (A5)** — rôle documentaire auxiliaire, hors de la boucle d'exécution applicative |

Le VALIDATOR n'est pas un agent. Aucun agent ne décide à sa place.

---

## 6. Les profils de gouvernance

Le profil détermine le **niveau de contrôle**, jamais les principes. Il est choisi par le VALIDATOR au début du projet, en fonction du risque, puis verrouillé.

| Profil | Usage | Document |
|---|---|---|
| **Standard** | Projet logiciel réel — **profil par défaut** | [profile_standard](protocol/profile_standard.md) |
| **Lite** | Prototypes, projets personnels, logiciels réversibles, faible exposition | [profile_lite](protocol/profile_lite.md) |
| **Reinforced** | Données sensibles, obligations réglementaires, risque financier, médical ou critique | [profile_reinforced](protocol/profile_reinforced.md) |

> **Disponibilité (A3).** Les trois profils restent dans la doctrine AKORIS. Leur disponibilité dans l'implémentation de référence est déclarée séparément, et elle n'est **pas établie** : le projet pilote connu fonctionne sans profil et ne satisfait aucun des trois.

Un projet ne peut pas choisir Lite pour éviter un contrôle rendu nécessaire par son niveau de risque.

---

## 7. Les prompts

Les prompts sont **courts et référentiels** : ils orientent vers les documents, ils ne les recopient pas.

| Prompt | Rôle visé | Statut |
|---|---|---|
| [prompts/akoris_orchestrator_bootstrap.md](prompts/akoris_orchestrator_bootstrap.md) | ORCHESTRATOR | **Réalisé (v6)** |
| [prompts/akoris_builder_bootstrap.md](prompts/akoris_builder_bootstrap.md) | BUILDER | **Réalisé (v6)** |
| [prompts/akoris_auditor_bootstrap.md](prompts/akoris_auditor_bootstrap.md) | AUDITOR | **Réalisé (v6)** |
| [prompts/akoris_documentation_builder.md](prompts/akoris_documentation_builder.md) | DOCUMENTATION BUILDER | **Réalisé (v6)** |

Il n'existe pas de prompt unique couvrant tous les rôles : ce serait un méga prompt, explicitement écarté.

---

## 8. Règles de maintenance documentaire

1. **Une information, un fichier.** La source unique est recensée dans la [carte documentaire](reference/document_map.md).
2. **Référencer plutôt que recopier.** Un document qui duplique une source est un défaut, pas une commodité.
3. **Signaler plutôt que corriger.** Une divergence se signale au VALIDATOR ; elle ne se corrige jamais silencieusement.
4. **Statuer explicitement.** Tout énoncé important porte un statut : `FAIT`, `HYPOTHÈSE`, `RECOMMANDATION`, `À ARBITRER`, `INCONNU`.
5. **Ne pas confondre proposition et décision.** Un document non validé reste une proposition.
6. **Ne pas créer un fichier sans utilité.** Un document spécialisé n'existe que si son contenu ne peut pas rester dans le socle.
7. **Mettre à jour la carte à chaque fin de vague**, jamais en cours de rédaction.
8. **Tracer toute évolution** dans `changelog.md` avec version, date et documents affectés.

Les règles complètes figurent dans [governance_core](protocol/governance_core.md) §10.

---

## 9. Documents de référence (sources)

Ces documents ont alimenté la rédaction. Ils ne font pas partie de la documentation produite.

| Document | Rôle | Autorité |
|---|---|---|
| `AKORIS_consolide.md` | Référence doctrinale du cadre | Niveau 2 |
| `AKORIS_architecture_documentaire.md` | Plan d'architecture et d'organisation | Niveau 3 |
| `akoris_documentation_builder.md` | Mandat et méthode du rédacteur | Niveau 4 |
| Projet pilote `demo_web` | Matériau et preuves d'implémentation | Niveau 5 — non doctrinal |

La hiérarchie d'autorité complète est décrite dans la [carte documentaire](reference/document_map.md) §5.

---

## 10. Ce que cette documentation n'est pas

- **Pas un méga prompt.** Aucun document ne contient à lui seul tout le protocole.
- **Pas une garantie de sécurité.** Les permissions décrites sont des règles ; leur application dépend de l'environnement et doit être vérifiée.
- **Pas un substitut à l'expertise.** Le cadre organise les décisions ; il ne les prend pas.
- **Pas un état de projet.** L'état d'un projet vit dans son `state.json`, jamais ici.
- **Validation partielle.** Les trois livrables V7 portent le statut **VALIDÉ PAR LE VALIDATOR — 2026-11-21** ; le reste du corpus n'est pas présenté comme validé. Voir l'état en tête de page.

---

## 11. Points ouverts

| Réf. | Sujet | État |
|---|---|---|
| A1 | Valeurs de décision et orthographe | **Tranché** — 5 valeurs, underscore |
| A2 | Primauté état/reçu, nommage, divergences, sérialisation | **Tranché** — v2.0 structure normative ; pilote v1.0 = écart historique |
| A3 | Couche profils | **Tranché** — doctrine maintenue, disponibilité déclarée à part |
| A4 | Nommage du README | **Tranché** — `documentation/README.md` |
| A5 | VALIDATOR vs agents | **Tranché** — VALIDATOR humain ; DOCUMENTATION BUILDER rôle documentaire auxiliaire, distinct des agents |
| A6 | Statut du manuel v1 du pilote | **Tranché** — référence historique, non concurrente |
| A7 | Versionnement | **Tranché** — 5 versions distinctes |
| A8 | Socle agnostique + implémentation OpenCode | **Tranché** |
| C13 | Emplacement de la `readiness_review` | **Tranché** — `docs/governance/readiness/` ; rapport historique du pilote conservé |
| C26 | Reçu pour ORCHESTRATOR | **Tranché** — `docs/governance/receipts/` |
| C27 | Expiration des transitions | **Tranché** — aucune durée numérique par défaut ; selon mandat et profil |
| C28 | Schéma d'état | **Tranché** — `reference/state.schema.json` créé pour AKORIS v2.0 |
| C29 | Protection de `main` | `unknown` — T5 préparé, **non exécuté** |
| — | Tests T1→T5 | **Non exécutés** |

Détail et recommandations : [cartographie documentaire](00_cartographie.md) §7. Les divergences de catégories de versions et les points à arbitrer sont signalés dans [versioning_policy](reference/versioning_policy.md) §4 et §5 ; les champs de traçabilité restant à arbitrer sont recensés dans [traceability_map](reference/traceability_map.md) §7.

---

## 12. Historique

| Version | Date | Modification |
|---|---|---|
| 0.1 | 2026-11-20 | Version initiale (vague 1) |
| 0.2 | 2026-11-20 | Mise à jour après vagues 2 et 3 : 11/34, liens profils et politiques |
| 0.3 | 2026-11-20 | Mise à jour après vague 4 : 14/34 |
| 0.4 | 2026-11-20 | Mise à jour après vague 5 : 15/34 |
| 0.5 | 2026-11-20 | Maintenance I1-I2 et intégration des décisions A2, C13, C26, C27, C28, C29 : 16/34 |
| 0.6 | 2026-11-20 | Maintenance de cohérence — vague 6 : 4 prompts et 7 modèles réalisés, compteur 27/34 |
| 0.7 | 2026-11-21 | Intégration des quatre documents OpenCode de l'archive : compteur 31/34 ; vague 7 non engagée |
| 0.8 | 2026-11-21 | Vague 7 : manuel de démarrage, carte de traçabilité et politique de versionnement rédigés, puis validés par le VALIDATOR ; compteur 34/34 ; validation partielle |
