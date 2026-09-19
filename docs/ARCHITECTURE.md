# Architecture — EurinHash AI Lab

## 1. Rôle

EurinHash AI Lab est le laboratoire de recherche appliquée de l'écosystème EurinHash. Sa responsabilité est de réduire l'incertitude technique avant l'intégration produit.

Le Lab ne remplace ni le repository d'engineering, ni le control plane, ni le runtime.

## 2. Architecture logique

```text
                         EURINHASH AI LAB
                                │
              ┌─────────────────┼─────────────────┐
              │                 │                 │
              ▼                 ▼                 ▼
          RESEARCH          EXPERIMENTS       EVALUATION
              │                 │                 │
              └─────────────────┼─────────────────┘
                                ▼
                           FINDINGS
                                │
                    ┌───────────┴───────────┐
                    ▼                       ▼
               ALGORITHM               PROTOTYPE
                    │                       │
                    └───────────┬───────────┘
                                ▼
                           BENCHMARK
                                │
                                ▼
                            VALIDATED
                                │
                   ┌────────────┴────────────┐
                   ▼                         ▼
                PACKAGE                 INTEGRATION
```

## 3. Research tracks

### Model Intelligence

Étudier le matching tâche → capacités → modèle, le routage et l'apprentissage à partir des résultats historiques.

### Resource Intelligence

Étudier disponibilité, autorisation, santé, quotas, limites et confiance des providers et modèles.

### Resilience

Étudier classification d'erreurs, retry, fallback, streaming stalled, timeout et récupération.

### AI Economy

Étudier coût financier, coût token, coût de retry, latence et coût d'échec.

### Mission Verification

Étudier contrats de mission, critères d'acceptation, preuves, validation et confiance de complétion.

### AI Security

Étudier classification des données, secrets, politiques de modèles, permissions et sécurité du contexte.

### Evaluation

Construire les méthodes permettant de comparer les solutions de manière reproductible.

## 4. Flux de données

```text
Engineering specification
        ↓
Research question
        ↓
Experiment definition
        ↓
Controlled execution
        ↓
Measurements
        ↓
Analysis
        ↓
Finding
        ↓
Candidate technology
        ↓
Benchmark / validation
        ↓
Integration proposal
```

Les données issues d'EurinHash en production peuvent alimenter le Lab uniquement après filtrage, anonymisation et respect des politiques de confidentialité.

## 5. Objets canoniques

Le Lab manipule principalement :

- `ResearchQuestion`
- `Hypothesis`
- `Experiment`
- `Run`
- `Dataset`
- `Metric`
- `Finding`
- `Algorithm`
- `Prototype`
- `Benchmark`
- `Evaluation`
- `Evidence`
- `PromotionDecision`

## 6. Frontières

### Engineering → Lab

Engineering fournit le problème, le contexte, les contraintes et les critères de succès.

### Lab → Config

Le Lab fournit uniquement des capacités suffisamment documentées et validées pour être considérées par le control plane.

### Lab → Product

Une intégration produit passe par le contrat d'architecture et le control plane. Le Lab ne pousse pas directement des expérimentations dans le runtime.

## 7. Sources externes

Le Lab peut étudier et intégrer comme sources ou substrates :

- catalogues de modèles ;
- runtimes d'agents ;
- gateways ;
- benchmarks publics ;
- publications scientifiques ;
- documentation provider ;
- retours d'expérience publics.

Ces sources ne deviennent pas automatiquement la source de vérité d'EurinHash.

## 8. Principe d'indépendance

Un résultat du Lab doit rester utile même si une implémentation externe disparaît. Les expériences doivent donc décrire les principes, hypothèses, métriques et limites, pas seulement une intégration à un fournisseur.
