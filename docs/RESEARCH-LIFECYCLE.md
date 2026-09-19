# Research Lifecycle

## États

```text
IDEA
 ↓
QUESTIONED
 ↓
HYPOTHESIS
 ↓
EXPERIMENTAL
 ↓
PROMISING
 ↓
REPLICATED
 ↓
VALIDATED
 ↓
CANDIDATE
 ↓
INTEGRATION-READY
 ↓
PRODUCTION
```

`PRODUCTION` est hors du Lab : l'artefact est alors gouverné par le repository qui l'intègre.

## Définitions

- **IDEA** : observation ou piste non étudiée.
- **QUESTIONED** : question de recherche explicitement formulée.
- **HYPOTHESIS** : mécanisme supposé et prédiction mesurable.
- **EXPERIMENTAL** : protocole exécutable, premiers résultats disponibles.
- **PROMISING** : signal positif, pas encore suffisamment robuste.
- **REPLICATED** : résultat reproduit dans les conditions définies.
- **VALIDATED** : résultat satisfait les critères scientifiques et d'ingénierie du projet.
- **CANDIDATE** : technologie proposée pour intégration.
- **INTEGRATION-READY** : contrat, API, limites, tests et documentation préparés.
- **PRODUCTION** : accepté par le repository produit concerné.

## Transitions

Chaque transition importante doit être justifiée dans un finding ou une décision.

Aucune transition vers `VALIDATED` sans résultats et critères explicites.

Aucune transition vers `INTEGRATION-READY` sans tests, documentation et analyse des limites.

## Reproductibilité

Un résultat qui ne peut pas être reproduit ne doit pas être présenté comme établi. Il peut rester une observation exploratoire avec un niveau de confiance approprié.
