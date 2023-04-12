# Natural Language Guided Reasoning

![Bigger landscape](https://raw.githubusercontent.com/nikett/about/main/criterium-annotated.jpg)


## Problem
Visionaries in AI and psychology have considered feedback and correction (i.e., guidance) as a requirement for truly intelligent AI systems that learn from errors and improve with time. However, models can be unreasonable and large models especially can be hard to finetune. Can we guide them at inference time? Guidance can take up different forms such as corrections, knowledge, Web retrieval based guidance, and theories and schemas e.g. from psychology, and human preferences. 

## Goal
A computational model of the "theory of recursive reminding" from psychology that suggests humans record error context and correction received in their episodic memory for the future. To realize such a computational model, we need a general memory architecture where input = question, output = critiqueable output and this receives guidance from various agents, to optionally, iteratively improve the output. To avoid repeating similar mistakes, this is recorded in a memory (analogous to episodic memory). This memory can be per user, thus leading to personalized models.

## Approach
Iterative approach to effectively use guidance obtained from various critics. We build upon four key questions:
- Who to ask (sources of guidance in the memory component)
- What to ask (critiqueable output y)
- When to ask (arrow from critiqueable output y to memory component)
- How to apply (arrow applying NL guidance to LM)


![NL Guided Reasoning](https://raw.githubusercontent.com/nikett/about/main/nl-guided-reasoning-annotated.jpg)


## Details

### Who to ask?
|Critic category        | Critics                 | Representative papers     |
|---                    |---                      |---                        |
|Knowledge as guidance  |Pre-constructed KG       | WebChild-KB [[1]](https://www.mpi-inf.mpg.de/departments/databases-and-information-systems/research/yago-naga/commonsense/webchild)       |
|                       |On-the-fly KG            | Inference graphs [[5]](https://aclanthology.org/2021.findings-acl.456.pdf)  |
|Feedback as guidance   |Human feedback           | Interscript [[6]](https://www.semanticscholar.org/paper/Interscript%3A-A-dataset-for-interactive-learning-of-Tandon-Madaan/07d5bba7d2bc511c88eb143a926d3c297298ad15) |
|                       |Supervised feedback      | Learning-to-repair [[7]](https://aclanthology.org/2022.findings-naacl.26/)|
|                       |RL feedback              | [ACL 2023 submission](https://niket.tandon.info)   |
|                       |Self feedback            | Self-Refine [[9]](https://selfrefine.info/)      |
|Schemas as guidance    |Dyadic theory            | [[in-progress]](https://github.com/allenai/emma/tree/dev)           |
|                       |State tracking: planning | [[in-progress]](https://github.com/allenai/openpi_v2)           |
|                       |Claim graphs: scholar    | [[in-progress]](https://github.com/nikett/claimgraph)           |
|Preference as guidance |User personalization     | [[in-progress]](https://niket.tandon.info)           |



### What to ask?
|Critiqueable category    | Critiqueable output     | Representative papers  |
|---                      |---                      |---                     |
|Structured explanation   | Inference graph         | Curious [[4]](https://aclanthology.org/2021.emnlp-main.508/)  |
|                         | Reasoning chain         | Quartet [[3]](https://aclanthology.org/2020.findings-emnlp.300.pdf) , CoT [[in-progress]](https://niket.tandon.info) |
|Unstructured explanation | Query understanding     | MemPrompt [[8]](https://memprompt.com) | 
|Structured output        | Script generation       | Interscript [[6]](https://www.semanticscholar.org/paper/Interscript%3A-A-dataset-for-interactive-learning-of-Tandon-Madaan/07d5bba7d2bc511c88eb143a926d3c297298ad15) |
|                         | Moral graph             | [EMMA](https://github.com/nikett/emma) |
|                         | State tracking tensor   | [[in-progress]](https://github.com/allenai/openpi_v2)         |



### When to ask?
|Critiqueability category | Critiqueability       | Representative papers |
|---                      |---                    |---                    |
|Unsupervised             | Inconsistency detector| [EMMA](https://github.com/nikett/emma)| 
|                         | Few-shot detector     | Self-Refine [[9]](https://selfrefine.info/) |



### How to apply?
|Critique-apply category | Applying the critique | Representative papers  |
|---                     |---                    |---                     |
|at the input            | Input context         | MemPrompt [[8]](https://memprompt.com) | 
|at the output           | Decoder, corrector    | Learning-to-repair [[7]](https://aclanthology.org/2022.findings-naacl.26/) |
|at the parameters       | Loss function         | ProStruct [[2]](https://aclanthology.org/D18-1006.pdf) |
|                        | Causal tracing        | [[in-progress]](https://niket.tandon.info) |



## Current/ Q2:
| Topic | Research Questions | Collaborators | Target |
|---    |---                 |---            |---     |
| Personalizing LLMs for user values | How well can LLMs be swayed towards a human's values? What about malicious users? | Bodhi, EunJeong (UBC) | NL Reasoning workshop @ACL, and EMNLP |
| Personalizing LLMs for procedures  | How important is personalization in procedural text? Can LLMs generate personalized procedural content?   | Yash | NL Reasoning workshop @ACL |
| OpenPI 2.0 | Understanding salient state changes and their impact | Harry, HaiNiu, Abhinav | EMNLP, arxiv May 2023 | 
| Tracking for LLMs | Can we assist LLMs on reasoning tasks through state tracking? | Yash (summer internship) | arxiv Aug 2023 |
| Self-Refine 2.0 | End2end system for iterative refinement | Aman, Aristo, Mosaic, others | NeurIPS, arxiv May 2023 | 
| Teachable CoT | Can we leverage step-by-step reasoning for step-by-step feedback? | Veronica (UPenn), Harry, Aristo, Mosaic, others | arxiv Aug 2023 | 
| Model editing | How well does model editing in MEMIT apply to commonsense facts? | Lorraine (Mosaic), Sarah (Aristo), UMass students | EMNLP, arxiv May 2023 | 
| S2 claims | Can LLMs uncover underlying assumptions for a claim? Can we use them for inference? | Neset (Auckland), David Wadden (S2) | EMNLP, arxiv May 2023 | 
| Moral bottleneck models | How well can LLMs rely on the dyadic theory from psychology? | Kurt Gray, Daniaca, Yuling, Nouha, Valentina | Nature Aug 2023 |
| Moral reasoning | Abductively generate moral updates with explanations | UW student, Nouha, Valentina, Liwei, Yuling | EMNLP 2023, arxiv May 2023 | 

## Q3/ Q4 ideas:
- A collaborative framework for multi-critics
- Study the effect of noisy critics
- Analyzing how RL generalizes memory
- Iterative RL to generate better feedback
- Create a reasoning test benchmark for procedural understanding
- Planning bottleneck models using an external engine to plan
- What is the best representation of memory, how does memory evolve


## Selected references:
1. Niket, Gerard, Fabian, Gerhard Weikum. “WebChild: harvesting and organizing commonsense knowledge from the web.” WSDM 2014
2. Niket, Bhavana, Joel et. al. “Reasoning about Actions and State Changes by Injecting Commonsense Knowledge.” EMNLP 2018
3. Dheeraj, Niket, Peter Clark et. al. “What-if I ask you to explain: Explaining the effects of perturbations in procedural text.” EMNLP Findings 2020
4. Aman, Niket, Dheeraj, et. al. “Think about it! Improving defeasible reasoning by first modeling the question scenario.” EMNLP 2021
5. Aman, Dheeraj, Niket et. al. “Could you give me a hint? Generating inference graphs for defeasible reasoning.” EMNLP Findings 2021
6. Niket, Aman, Peter et. al. “Interscript: A dataset for interactive learning of scripts through error feedback.” AAAI Workshop on Interactive ML (2021)
7. Niket, Aman, Peter et. al. “Learning to repair: Repairing model output errors after deployment using a dynamic memory of feedback.” NAACL 2022.
8. Aman, Niket, Peter et. al. “Memory-assisted prompt editing to improve GPT-3 after deployment.” EMNLP 2022.
9. Aman, Niket, et. al. "Self-Refine: Iterative Refinement with Self-Feedback." ArXiv abs/2303.17651 (2023)


