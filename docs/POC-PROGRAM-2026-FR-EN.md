# EurinHash AI Lab — Programme de PoC 2026 / 2026 PoC Program

## FR — Pourquoi des PoC ?

Le Lab ne doit pas seulement affirmer que les problèmes étudiés sont importants. Il doit produire des expériences reproductibles permettant de mesurer :

- la valeur réelle d'une décision d'orchestration ;
- le coût évité ;
- les échecs évités ou récupérés ;
- la qualité vérifiée ;
- la latence ;
- la sécurité ;
- la qualité des preuves produites.

Le standard de preuve est : **baseline → expérience contrôlée → métriques → comparaison → reproduction → conclusion limitée aux conditions testées**.

Une proposition EurinHash n'est pas considérée comme nouvelle simplement parce qu'elle combine plusieurs concepts connus. Toute revendication de nouveauté doit être précédée d'une recherche de prior art et d'une comparaison expérimentale.

## EN — Why PoCs?

The Lab must not merely claim that these problems matter. It must produce reproducible experiments measuring:

- orchestration decision value;
- avoided cost;
- prevented or recovered failures;
- verified quality;
- latency;
- security;
- quality of produced evidence.

The evidence standard is: **baseline → controlled experiment → metrics → comparison → replication → conclusion limited to tested conditions**.

A proposal is not considered novel merely because it combines known concepts. Any novelty claim requires prior-art review and experimental comparison first.

---

# 1. State of the art / État de l'art

| Domaine | Travaux / auteurs | Institution / communauté | Ce que cela démontre |
|---|---|---|---|
| Model routing | Isaac Ong, Amjad Almahairi, Vincent Wu, Wei-Lin Chiang, Tianhao Wu, Joseph E. Gonzalez, M. Waleed Kadous, Ion Stoica — RouteLLM (2024) | UC Berkeley / LMSYS research ecosystem | Le choix dynamique entre modèles peut traiter le compromis coût/qualité. |
| Routing benchmark | Qitian Jason Hu, Jacob Bieker, Xiuyu Li, Nan Jiang, Benjamin Keigwin, Gaurav Ranganath, Kurt Keutzer, Shriyash Kaustubh Upadhyay — RouterBench (2024) | UC Berkeley / Martian et collaborateurs | Le routing multi-LLM mérite un benchmark dédié et des données à grande échelle. |
| Routing benchmark 2026 | équipe LLMRouterBench | communauté académique ACL 2026 | Le domaine s'est élargi à 33 modèles, 21+ datasets et 10 algorithmes représentatifs. |
| Cost optimization | FrugalGPT (2023/2024) | Stanford / recherche académique | Les cascades, adaptations et sélections de modèles peuvent fortement réduire le coût dans certains protocoles. |
| Agent evaluation | Xiao Liu et al. — AgentBench | Tsinghua University / THUDM | L'évaluation d'agents nécessite des environnements interactifs et révèle des écarts importants entre modèles. |
| Software-agent verification | Carlos E. Jimenez et al. — SWE-bench | Princeton / communauté SWE | Les tâches GitHub réelles permettent de mesurer l'exécution de travaux logiciels plutôt que la simple génération de texte. |
| LLM-as-a-judge | Lianmin Zheng et al. — MT-Bench / Chatbot Arena | UC Berkeley / LMSYS | L'évaluation par modèles peut être utile à grande échelle mais possède des biais et limites documentés. |
| Research-agent verification | Giulio Starace et al. — PaperBench | OpenAI | La reproduction d'un travail scientifique peut être décomposée en milliers de sous-tâches vérifiables avec rubriques et évaluateurs. |
| Agent security | Badrinath Ramakrishnan, Akshaya Balaji — prompt injection benchmark | recherche académique 2025 | La sécurité agentique peut être évaluée par attaques reproductibles et défenses mesurées. |
| Inference economics | Huamin Chen, Xunzhuo Liu, Junchen Jiang, Bowei He, Xue Liu — token-budget-aware routing | recherche systèmes 2026 | Le budget de tokens peut être utilisé comme signal de routage pour réduire les ressources nécessaires sous certaines charges. |

## Sources primaires

1. RouteLLM — Isaac Ong et al., 2024: https://arxiv.org/abs/2406.18665
2. RouterBench — Qitian Jason Hu et al., 2024: https://arxiv.org/abs/2403.12031
3. LLMRouterBench: https://github.com/ynulihao/LLMRouterBench
4. RouteLLM implementation: https://github.com/lm-sys/RouteLLM
5. AgentBench — Xiao Liu et al.: https://arxiv.org/abs/2308.03688
6. SWE-bench — Carlos E. Jimenez et al.: https://arxiv.org/abs/2310.06770
7. MT-Bench / LLM-as-a-Judge — Lianmin Zheng et al.: https://arxiv.org/abs/2306.05685
8. PaperBench — Giulio Starace et al., OpenAI: https://openai.com/index/paperbench/
9. Prompt injection benchmark — Badrinath Ramakrishnan, Akshaya Balaji: https://arxiv.org/abs/2511.15759
10. Token-Budget-Aware Pool Routing — Huamin Chen et al.: https://arxiv.org/abs/2604.09613

---

# 2. PoC portfolio

## POC-01 — Capability-aware model routing

**Question:** un routeur tenant compte du type de tâche et des contraintes peut-il réduire le coût tout en conservant une qualité vérifiée acceptable ?

**Baselines:** modèle fort systématique ; modèle faible systématique ; RouteLLM ; règle coût/qualité simple.

**EurinHash hypothesis:** ajouter capability/task-fit + contexte + budget + état de ressource + historique de fiabilité peut améliorer le compromis coût/qualité par rapport à un routeur uniquement préférence/coût.

**Métriques:** verified success rate, cost/task, tokens/task, latency P50/P95, fallback rate, failure rate.

**Stop condition:** aucune amélioration statistiquement ou expérimentalement crédible sur plusieurs catégories → hypothèse rejetée ou reformulée.

## POC-02 — Resource truth / quota intelligence

**Question:** une représentation explicite de `configured/discovered/available/authorized/healthy/usable/active` réduit-elle les mauvais choix de ressources ?

**Baseline:** disponibilité binaire.

**Experiment:** simulateur de providers avec quotas, expiration, 401/403/429, latence et informations manquantes.

**Métriques:** invalid dispatches, unnecessary retries, time-to-recovery, false-available rate, stale-state rate.

**Point critique:** `UNKNOWN` doit rester inconnu ; il ne doit jamais être converti en disponibilité.

## POC-03 — Failure-aware resilience

**Question:** classifier la panne avant retry/fallback réduit-il les boucles inutiles et le temps de récupération ?

**Baseline:** retry générique + fallback séquentiel.

**Experiment:** injection de 401/403/404/429/502/503/504, timeout, stalled stream, invalid tool call.

**Métriques:** recovery rate, recovery time, retry count, wasted tokens, duplicate requests, stuck sessions.

## POC-04 — Mission economy

**Question:** un budget de mission intégrant coût financier, tokens, retries, latence et échec permet-il d'accomplir la même mission à coût réel inférieur ?

**Baselines:** cheapest-first, strongest-first, fixed provider.

**Experiment:** missions de difficulté faible/moyenne/forte avec budgets différents.

**Métriques:** verified success / total cost, cost per verified success, wasted tokens, budget overruns.

## POC-05 — Mission verification

**Question:** un verifier fondé sur acceptance criteria + artefacts + tests + exécution peut-il distinguer `COMPLETED` de `VERIFIED` ?

**Baselines:** agent self-report ; LLM judge seul ; tests seuls lorsque disponibles.

**Experiment:** missions volontairement terminées partiellement, avec bugs subtils et affirmations incorrectes de l'agent.

**Métriques:** false acceptance, false rejection, verification precision/recall, evidence coverage.

## POC-06 — Evidence / proof engine

**Question:** une chaîne de provenance des preuves améliore-t-elle l'auditabilité d'une mission ?

**Experiment:** chaque acceptance criterion doit être relié à une preuve : test, diff, log, command output, runtime observation ou artefact.

**Métriques:** criteria coverage, evidence validity, orphan claims, reproducibility rate.

## POC-07 — Security-aware routing

**Question:** une politique de routage tenant compte de la sensibilité des données et de la confiance du provider réduit-elle l'exposition sans rendre le système inutilisable ?

**Baselines:** routage sans politique ; blocage total des données sensibles.

**Experiment:** données publiques, internes, sensibles et secrets synthétiques ; providers locaux et distants ; attaques prompt injection.

**Métriques:** leakage rate, blocked unsafe dispatches, successful task rate, false blocks, attack success rate.

## POC-08 — Unified EurinHash Mission Router

**Question:** un moteur combinant capability, resource truth, budget, reliability, security policy et verification peut-il améliorer le **verified mission success / effective cost** par rapport aux baselines spécialisées ?

**Baselines:** strongest-first ; cheapest-first ; RouteLLM-style quality/cost router ; fixed provider; random.

**Experiment:** benchmark multi-domaines avec tâches code, recherche, raisonnement, tool use et workflows multi-étapes.

**Primary metric:** `verified_mission_success / effective_mission_cost`.

**Secondary metrics:** latency, token usage, failure recovery, security violations, evidence completeness.

**Important:** ce PoC ne cherche pas à prouver qu'EurinHash est « meilleur » par principe. Il cherche à déterminer expérimentalement si l'intégration de plusieurs signaux apporte une amélioration mesurable et reproductible.

---

# 3. Promotion gate

Un PoC peut passer de `IDEA` à `EXPERIMENTAL` seulement si son protocole est écrit. Il peut passer à `PROMISING` seulement si une baseline est exécutée et que les résultats sont conservés. `VALIDATED` exige reproduction indépendante ou répétée, comparaison avec baselines pertinentes et analyse des limites. `STABLE` exige documentation, tests et absence de régression connue dans le périmètre déclaré.

Aucun résultat de benchmark ne doit être généralisé au-delà de sa population, de ses modèles, de ses datasets et de son protocole.

# 4. EN — Promotion gate

A PoC moves from `IDEA` to `EXPERIMENTAL` only after its protocol is specified. It reaches `PROMISING` only after a baseline is executed and results are preserved. `VALIDATED` requires repeated or independent reproduction, comparison against relevant baselines, and limitations analysis. `STABLE` requires documentation, tests, and no known regression within the declared scope.

No benchmark result may be generalized beyond its tested population, models, datasets, and protocol.
