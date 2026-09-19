# Contributing to EurinHash AI Lab

## Avant de coder

1. Identifier le problème.
2. Vérifier les recherches et expériences existantes.
3. Ouvrir ou relier une question de recherche.
4. Définir l'hypothèse et les métriques.
5. Décrire le protocole.

## Une contribution doit distinguer

- observation ;
- hypothèse ;
- mesure ;
- interprétation ;
- conclusion.

Ne pas présenter une interprétation comme une mesure.

## Données

Ne jamais publier :

- clés API ;
- tokens ;
- credentials ;
- données personnelles ;
- code privé sans autorisation ;
- prompts ou contextes confidentiels ;
- traces permettant d'identifier un utilisateur ou une organisation.

Les datasets publics doivent documenter leur source, licence et transformation.

## Code expérimental

Le code peut être volontairement imparfait lorsqu'il sert à tester une hypothèse. Il doit toutefois indiquer clairement son statut et ne doit pas être présenté comme production-ready.

## Reproductibilité

Une contribution expérimentale doit fournir suffisamment d'informations pour permettre une reproduction raisonnable du résultat.

## Résultats négatifs

Les résultats négatifs sont les bienvenus s'ils sont correctement documentés. Ils évitent de reproduire des expériences déjà invalidées.

## Intégration

Une technologie validée destinée à EurinHash doit passer par une proposition d'intégration et respecter la frontière :

```text
AI LAB → VALIDATED CAPABILITY → TARGET REPOSITORY
```

Le Lab ne doit pas modifier silencieusement les repositories produit ou configuration.
