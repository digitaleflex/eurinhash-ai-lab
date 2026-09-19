# Promotion Policy

## Principe

Le Lab privilégie la preuve avant l'intégration.

## Gates

### Gate 0 — Relevance

Le problème est réel, clairement formulé et utile à l'écosystème ou à la communauté.

### Gate 1 — Experimental

Le protocole est exécutable et les métriques sont définies.

### Gate 2 — Evidence

Les résultats sont accompagnés d'artefacts et d'observations vérifiables.

### Gate 3 — Replication

Le résultat est reproduit ou les limites de reproductibilité sont explicitement documentées.

### Gate 4 — Benchmark

La solution est comparée à une baseline appropriée.

### Gate 5 — Engineering

Le prototype possède :

- contrat d'interface ;
- tests ;
- gestion des erreurs ;
- limites connues ;
- documentation ;
- analyse sécurité ;
- analyse performance ;
- stratégie de maintenance.

### Gate 6 — Integration proposal

Une proposition d'intégration précise :

- repository cible ;
- boundary ;
- dépendances ;
- API ;
- migration ;
- rollback ;
- critères d'acceptation.

## Ce qui n'est pas suffisant

Les éléments suivants ne constituent pas une preuve suffisante seuls :

- une démo unique ;
- une réponse d'un seul modèle ;
- une capture d'écran ;
- un benchmark non reproductible ;
- une amélioration sur un dataset unique sans analyse ;
- un résultat sans baseline ;
- un prototype qui fonctionne uniquement dans l'environnement du chercheur.

## Règle de promotion

```text
Finding
  ↓
Evidence
  ↓
Replication
  ↓
Benchmark
  ↓
Engineering Review
  ↓
Integration Proposal
```

Le Lab peut recommander une intégration. Le repository cible décide de son acceptation selon ses propres contraintes.
