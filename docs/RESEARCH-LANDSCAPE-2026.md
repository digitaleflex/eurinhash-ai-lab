# EurinHash AI Lab — Research Landscape 2026

## Purpose

Ce document établit une carte initiale de l'état de l'art avant toute invention d'algorithme EurinHash. Il distingue les approches déjà publiées, les outils existants, leurs hypothèses et les zones où le Lab peut chercher une contribution originale.

> Règle : EurinHash ne revendique pas comme nouveau ce qui existe déjà. Toute hypothèse doit être comparée à des baselines reproductibles.

## 1. Model routing

### RouteLLM
RouteLLM apprend à router une requête entre modèles forts et faibles à partir de données de préférence. Il explore notamment matrix factorization, ranking et classifieurs. Le principe central est l'optimisation du compromis qualité/coût.

Reference: https://arxiv.org/abs/2406.18665
Code/reference implementation: https://github.com/lm-sys/RouteLLM

### RouterBench
RouterBench fournit un benchmark multi-LLM pour comparer des systèmes de routing. Il formalise notamment les métriques de qualité et coût et facilite la comparaison de plusieurs routeurs.

Reference: https://github.com/withmartian/routerbench

### LLMRouterBench
LLMRouterBench étend fortement l'espace d'évaluation : 33 modèles, 21+ datasets, 10 algorithmes de routing et plus de 400K instances dans sa version 2026 publiée. Il couvre notamment math, code, logique, connaissance, instruction following et tool use.

Reference: https://github.com/ynulihao/LLMRouterBench

### FrugalGPT
FrugalGPT explore prompt adaptation, approximation et cascades de modèles pour réduire le coût tout en maintenant ou améliorant la qualité.

Reference: https://arxiv.org/abs/2305.05176

### Direction récente
Les travaux 2026 explorent aussi les préférences coût-performance personnalisées et le routage comme allocation de budget. Cela suggère que le routing purement statique est insuffisant pour notre problème.

Reference: https://arxiv.org/abs/2606.06178

## 2. Ce qui semble déjà bien couvert

La communauté sait déjà faire :

- routage fort/faible ;
- routing basé sur préférences ;
- seuil qualité/coût ;
- cascades ;
- benchmarks de routing ;
- routage performance-only et performance-cost ;
- adaptation à des pools de modèles ;
- stratégies de budget dans certains domaines.

Donc « choisir le modèle le moins cher » n'est PAS une contribution suffisante.

## 3. Resource intelligence

Le problème est moins standardisé que le model routing : disponibilité réelle, autorisation, quota, santé, fraîcheur du catalogue, identité du compte et état du gateway sont souvent traités comme des préoccupations opérationnelles plutôt que comme une couche scientifique unifiée.

Hypothèse de recherche EurinHash : représenter explicitement la confiance et la fraîcheur de chaque état de ressource, puis injecter cette information dans la décision de routing.

Invariant :

```text
CONFIGURED ≠ DISCOVERED ≠ AVAILABLE ≠ AUTHORIZED
≠ HEALTHY ≠ USABLE ≠ ACTIVE ≠ USED
```

## 4. Resilience

Les gateways et frameworks d'inférence traitent retry, fallback, timeouts et rate limits. Le problème de recherche EurinHash est de ne pas réduire la résilience à un mécanisme `catch → next provider`.

Questions :

- quelle erreur est récupérable ?
- quel fallback reste compatible avec la mission ?
- quand faut-il arrêter les retries ?
- comment traiter un stream connecté mais silencieux ?
- comment intégrer quota et santé dans la décision ?
- comment mesurer le coût de la récupération ?

## 5. AI economy

Les travaux existants couvrent largement les cascades et le coût qualité/performance. Le Lab doit donc étudier le coût réel d'une mission, incluant lorsqu'ils sont mesurables : tokens, retries, latence, échecs, escalades, cache et coût d'opportunité.

Travail connexe : optimisation de cache pour la latence de queue et routage basé sur budget de tokens.

References:
- https://arxiv.org/abs/2510.15152
- https://arxiv.org/abs/2604.09613

## 6. Mission verification

La vérification des sorties par un autre LLM, les évaluations reference-based et reference-free, ainsi que les systèmes multi-agents d'évaluation existent déjà.

Le Lab ne doit donc pas prétendre inventer « la vérification par LLM ».

La piste EurinHash est plus précise : vérifier une **mission exécutable** à partir d'un contrat, de critères d'acceptation et de preuves observables provenant de l'environnement réel.

Modèle de départ :

```text
MISSION CONTRACT
 ↓
EXECUTION
 ↓
OBSERVABLE EVIDENCE
 ↓
DETERMINISTIC CHECKS
 ↓
SEMANTIC CHECKS
 ↓
VERIFIER
 ↓
PROOF + LIMITATIONS
```

Invariant :

```text
COMPLETED ≠ VERIFIED
NO EVIDENCE → NO VERIFIED
```

## 7. Agent security

La sécurité des agents, notamment prompt injection, exfiltration et manipulation de contexte, fait déjà l'objet de benchmarks et de défenses multi-couches.

Exemple : un travail de 2025 évalue 847 cas adversariaux dans cinq catégories et combine filtrage, garde-fous hiérarchiques et vérification multi-étapes.

Reference: https://arxiv.org/abs/2511.15759

La piste EurinHash doit donc porter sur la décision de routage elle-même : quelles données, instructions, outils et permissions peuvent être exposés à quelle ressource ?

## 8. Agent evaluation

L'évaluation reference-based et reference-free, les juges LLM et les systèmes multi-agents sont déjà établis. Pour EurinHash, il faut ajouter une dimension opérationnelle : l'agent a-t-il produit les artefacts attendus, passé les contrôles, respecté les contraintes et laissé suffisamment de preuves ?

## 9. Positionnement de recherche EurinHash

La contribution potentielle n'est donc pas un « nouveau routeur » isolé.

Nous devons étudier l'intersection :

```text
MODEL CAPABILITY
      ×
RESOURCE TRUTH
      ×
MISSION CONSTRAINTS
      ×
COST / BUDGET
      ×
RELIABILITY
      ×
SECURITY POLICY
      ×
EXECUTION STATE
      ×
VERIFICATION EVIDENCE
```

Question centrale proposée :

> Comment orchestrer dynamiquement des ressources IA hétérogènes pour accomplir une mission sous contraintes, tout en minimisant le coût attendu, en récupérant des défaillances et en produisant des preuves vérifiables de résultat ?

## 10. Ce que le Lab doit faire maintenant

1. Reproduire plusieurs baselines existantes.
2. Construire un benchmark EurinHash sur des tâches représentatives.
3. Ajouter progressivement les dimensions que les benchmarks de routing classiques n'intègrent pas toutes ensemble : état de ressource, quota, panne, budget, sécurité et preuve de mission.
4. Mesurer les gains et régressions.
5. Publier les résultats négatifs.
6. Ne proposer un algorithme EurinHash que lorsqu'il bat des baselines sur un protocole reproductible.

## 11. Première hypothèse testable

> Un routeur qui prend en compte simultanément les capacités requises par la mission, l'état réel et la confiance des ressources, le budget, la fiabilité historique et les contraintes de sécurité peut réduire le coût et les échecs par rapport à un routeur qualité/coût classique, sans dégrader le taux de missions vérifiées.

Cette phrase est une **hypothèse**, pas une conclusion.

## 12. Sources principales à suivre

- RouteLLM — https://arxiv.org/abs/2406.18665
- FrugalGPT — https://arxiv.org/abs/2305.05176
- RouterBench — https://github.com/withmartian/routerbench
- LLMRouterBench — https://github.com/ynulihao/LLMRouterBench
- MetaRouter — https://arxiv.org/abs/2606.06178
- Tail-Optimized Caching — https://arxiv.org/abs/2510.15152
- Token-Budget-Aware Pool Routing — https://arxiv.org/abs/2604.09613
- Agent prompt-injection benchmark — https://arxiv.org/abs/2511.15759
