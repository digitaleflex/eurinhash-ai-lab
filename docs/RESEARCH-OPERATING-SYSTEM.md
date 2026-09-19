# Research Operating System

## Objectif

Le Research Operating System (ROS) définit comment le Lab transforme un problème en connaissance reproductible puis, éventuellement, en technologie intégrable.

## Cycle canonique

```text
PROBLEM
  ↓
RESEARCH QUESTION
  ↓
HYPOTHESIS
  ↓
EXPERIMENT DESIGN
  ↓
CONTROLLED RUN
  ↓
MEASUREMENT
  ↓
ANALYSIS
  ↓
FINDING
  ↓
REPLICATION
  ↓
BENCHMARK
  ↓
PROMOTION
```

## 1. Problem

Décrire un problème observable, son contexte, son impact et les preuves existantes.

Un problème ne doit pas être formulé comme une solution imposée.

Mauvais : `Créer un meilleur routeur LLM.`

Bon : `Le système sélectionne parfois une ressource indisponible ou insuffisamment capable.`

## 2. Research Question

La question doit être falsifiable ou mesurable.

Exemple :

> Peut-on réduire le coût attendu d'une mission sans diminuer son taux de réussite vérifié ?

## 3. Hypothesis

Une hypothèse doit prévoir un résultat observable.

Format recommandé :

```text
IF [condition]
THEN [expected effect]
BECAUSE [mechanism]
```

## 4. Experiment

Chaque expérience définit :

- objectif ;
- hypothèse ;
- variables ;
- contrôles ;
- dataset ;
- environnement ;
- métriques ;
- protocole ;
- critères d'arrêt ;
- menaces à la validité.

## 5. Run

Une exécution doit être identifiable et enregistrer au minimum :

- date/version ;
- configuration ;
- inputs ou dataset version ;
- ressources utilisées ;
- métriques ;
- erreurs ;
- résultat ;
- artefacts ;
- seed lorsque pertinente.

## 6. Evidence

Une conclusion doit pointer vers les observations qui la supportent.

```text
CLAIM
 ↓
EVIDENCE
 ↓
ANALYSIS
 ↓
CONFIDENCE
```

## 7. Reproductibilité

Une expérience doit pouvoir être rejouée avec :

- le même protocole ;
- les mêmes versions ;
- le même dataset lorsque sa licence le permet ;
- les mêmes paramètres ;
- un environnement documenté.

Une expérience non reproductible peut rester informative, mais son niveau de confiance doit le refléter.

## 8. Résultats négatifs

Les résultats suivants sont valides :

- hypothèse rejetée ;
- gain inférieur au seuil ;
- régression ;
- instabilité ;
- impossibilité de reproduire ;
- absence de différence statistiquement exploitable.

Le Lab conserve ces résultats afin d'éviter de répéter les mêmes recherches.

## 9. Promotion

Un prototype ne devient pas production-ready simplement parce qu'il fonctionne une fois.

Il doit passer les critères de [`PROMOTION-POLICY.md`](PROMOTION-POLICY.md).
