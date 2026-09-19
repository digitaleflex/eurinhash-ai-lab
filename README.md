# EurinHash AI Lab

**Research, experimentation and evaluation laboratory for reliable, economical and verifiable AI engineering.**

Le laboratoire EurinHash AI Lab est l'espace de recherche de l'écosystème EurinHash. Il transforme des problèmes techniques réels en hypothèses, expériences reproductibles, benchmarks, algorithmes et technologies validées.

## Mission

Le Lab étudie notamment :

- l'intelligence et le routage des modèles ;
- l'intelligence des ressources, quotas et providers ;
- la résilience des systèmes IA ;
- l'économie des tokens et des missions ;
- la vérification des missions et la production de preuves ;
- la sécurité des contextes, agents et modèles ;
- l'évaluation des systèmes agentiques.

## Principe directeur

```text
PROBLEM
  ↓
HYPOTHESIS
  ↓
RESEARCH
  ↓
EXPERIMENT
  ↓
DATA
  ↓
RESULT
  ↓
ALGORITHM / PROTOTYPE
  ↓
BENCHMARK
  ↓
VALIDATION
  ↓
PACKAGE / INTEGRATION
```

Une expérimentation n'est jamais considérée comme une fonctionnalité de production sans preuve suffisante.

## Standard expérimental des PoC

Chaque PoC doit être un objet de recherche autonome et reproductible :

```text
experiments/poc-XX-name/
├── research/
│   └── QUESTION.md
├── protocol.yaml
├── baselines/
├── datasets/
├── runner/
├── results/            # JSON/CSV bruts, générés par les runs
├── analysis/           # scripts, tableaux et graphiques dérivés
└── FINDING.md
```

Le runner doit enregistrer au minimum : version du code, version du dataset, seed, configuration, modèles/providers, métriques, erreurs et horodatage. Les résultats bruts sont immuables ; les analyses sont dérivées des résultats.

Un PoC doit comparer au moins une baseline pertinente et définir avant exécution : question, hypothèse falsifiable, variables, protocole, métriques et menaces à la validité.

Aucun résultat n'est présenté comme preuve de supériorité sans réplication suffisante et analyse des limites. `INCONCLUSIVE` est un résultat valide.

## Architecture de l'écosystème

```text
EURINHASH ENGINEERING
        │ defines problems, specifications and acceptance criteria
        ▼
EURINHASH AI LAB
        │ researches, experiments, benchmarks and validates
        ▼
OPENCODE-CONFIG
        │ orchestrates validated capabilities
        ▼
EURINHASH-OPENCODE
        │ executes and presents real missions
        ▼
REAL-WORLD OBSERVATIONS
        └──────────────────────────────► AI LAB
```

## Research tracks

| Track | Question centrale |
|---|---|
| `model-intelligence` | Quel modèle est suffisamment capable pour cette tâche ? |
| `resource-intelligence` | Quelle ressource est réellement disponible et utilisable ? |
| `resilience` | Comment continuer correctement malgré les défaillances ? |
| `ai-economy` | Quel est le coût réel d'une mission ? |
| `mission-verification` | Comment prouver qu'une mission est réellement terminée ? |
| `ai-security` | Quel contexte peut être envoyé à quelle ressource ? |
| `evaluation` | Comment mesurer objectivement qualité, fiabilité et efficacité ? |

## Règles scientifiques et d'ingénierie

1. `UNKNOWN ≠ ZERO`.
2. `CONFIGURED ≠ AVAILABLE`.
3. `AVAILABLE ≠ USABLE`.
4. `REQUESTED ≠ RUNNING`.
5. `RUNNING ≠ COMPLETED`.
6. `COMPLETED ≠ VERIFIED`.
7. `SKIPPED ≠ PASSED`.
8. Toute affirmation importante doit être associée à une observation, une source ou une expérience.
9. Les résultats négatifs sont des résultats valides et doivent être conservés.
10. Les benchmarks doivent être reproductibles autant que possible.
11. Les secrets, credentials et données privées ne doivent jamais entrer dans les datasets ou expériences publiques.
12. Le Lab ne devient pas un dépôt de code de production par défaut.

## Structure

```text
eurinhash-ai-lab/
├── research/          # Questions et axes de recherche
├── experiments/       # Expériences reproductibles
├── benchmarks/        # Suites et résultats comparatifs
├── datasets/          # Datasets documentés et autorisés
├── prototypes/        # Implémentations exploratoires
├── algorithms/        # Algorithmes candidats
├── evaluations/       # Méthodes et rapports d'évaluation
├── findings/          # Conclusions et résultats de recherche
├── papers/            # Notes techniques et publications
├── docs/              # Méthodologie et gouvernance
├── schemas/           # Formats machine-readable
└── scripts/            # Outils reproductibles du Lab
```

## Relation avec les autres repositories

- **`eurinhash-engineering`** : définit le problème, le produit attendu et les critères d'acceptation.
- **`eurinhash-ai-lab`** : cherche et teste les solutions.
- **`opencode-config`** : orchestre les capacités validées.
- **`eurinhash-opencode`** : intègre et expose les capacités dans le produit.

Le Lab peut proposer une solution ; il ne décide pas seul de son intégration en production.

## Statut

Le repository constitue maintenant la fondation du laboratoire expérimental. Les premiers travaux doivent privilégier des PoC reproductibles, mesurables et falsifiables avant toute multiplication de prototypes.

Voir :

- [`docs/RESEARCH-OPERATING-SYSTEM.md`](docs/RESEARCH-OPERATING-SYSTEM.md)
- [`docs/RESEARCH-LIFECYCLE.md`](docs/RESEARCH-LIFECYCLE.md)
- [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md)
- [`docs/EXPERIMENT-TEMPLATE.md`](docs/EXPERIMENT-TEMPLATE.md)
- [`docs/PROMOTION-POLICY.md`](docs/PROMOTION-POLICY.md)
- [`docs/CONTRIBUTING.md`](docs/CONTRIBUTING.md)
