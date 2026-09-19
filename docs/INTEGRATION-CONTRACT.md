# Lab → EurinHash Integration Contract

## Objectif

Définir comment une découverte du Lab peut devenir une capacité utilisable par EurinHash sans mélanger expérimentation et production.

## Required package

Une proposition d'intégration doit fournir :

1. problème résolu ;
2. hypothèse et résultat ;
3. baseline ;
4. benchmark ;
5. limites ;
6. risques ;
7. contrat d'API ;
8. tests ;
9. métriques ;
10. documentation ;
11. dépendances ;
12. versioning ;
13. rollback ;
14. repository cible proposé.

## Boundary

```text
AI LAB
  │
  │ validated capability
  ▼
INTEGRATION REVIEW
  │
  ├── opencode-config  → orchestration capability
  └── eurinhash-opencode → product/runtime capability
```

Le Lab n'est pas autorisé à transformer directement une expérimentation en comportement produit implicite.

## Provenance

Toute capacité intégrée doit conserver un lien vers :

- l'expérience ;
- le finding ;
- le benchmark ;
- la version de l'algorithme.

## Rollback

Une capacité expérimentale intégrée doit pouvoir être désactivée ou remplacée sans perdre les données et preuves de recherche qui ont conduit à sa création.
