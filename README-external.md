# Natural Language Guided Reasoning


## Problem
Feedback and correction (i.e., guidance) to learn from errors and improve with time, is a requirement for truly intelligent AI systems. However, models can be unreasonable and large models can be especially prohibitive to finetune. The central problem we address is "Can we guide them at inference time?" Guidance can take up different forms such as corrections, knowledge, Web based guidance, and theories and schemas e.g. from psychology, and human preferences. 

## Goal
We are inspired by the "theory of recursive reminding" from Psychology which suggests that humans record error context and correction received in their episodic memory for the future. Our goal is a general memory architecture where input = question, output = critiqueable output and the model receives guidance from various agents, potentially iteratively. To avoid repeating similar mistakes, mistakes with context is recorded in a memory (analogous to episodic memory). This memory can also be per user, resulting in personalized models.

## Approach: overview
We suggest an iterative approach to effectively use guidance obtained from various critics, that builds upon four key questions:
- Who to ask (sources of guidance in the figure)
- What to ask (various forms that the critiqueable output y can take)
- When to ask (ask when necessary, depicted in the figure with. anarrow from critiqueable output y to memory component)
- How to apply (various ways of injecting this guidance, depicted in the figure with an arrow applying NL guidance to LM)


![NL Guided Reasoning](https://raw.githubusercontent.com/nikett/about/main/nl-guided-reasoning-annotated.jpg)


## Approach: details
In the last years, I have answered some aspects of these big-four research questions. Firstly, on sources of guidance, there are four major categories: Knowledge as guidance, Feedback as guidance, neuro-symbolic schemas as guidance, human preference as guidance. Each category comes with one or more critics, depicted in the table below. 

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


The second question is what should be the output that must be critiqued. Structued or unstructured? 


### What to ask?
|Critiqueable category    | Critiqueable output     | Representative papers  |
|---                      |---                      |---                     |
|Structured explanation   | Inference graph         | Curious [[4]](https://aclanthology.org/2021.emnlp-main.508/)  |
|                         | Reasoning chain         | Quartet [[3]](https://aclanthology.org/2020.findings-emnlp.300.pdf) , CoT [[in-progress]](https://niket.tandon.info) |
|Unstructured explanation | Query understanding     | MemPrompt [[8]](https://memprompt.com) | 
|Structured output        | Script generation       | Interscript [[6]](https://www.semanticscholar.org/paper/Interscript%3A-A-dataset-for-interactive-learning-of-Tandon-Madaan/07d5bba7d2bc511c88eb143a926d3c297298ad15) |
|                         | Moral graph             | [EMMA](https://github.com/nikett/emma) |
|                         | State tracking tensor   | [[in-progress]](https://github.com/allenai/openpi_v2)         |


The third question is whether the output needs to be critiqued? We optimize for should be able to use feedback only when necessary. 


### When to ask?
|Critiqueability category | Critiqueability       | Representative papers |
|---                      |---                    |---                    |
|Unsupervised             | Inconsistency detector| [EMMA](https://github.com/nikett/emma)| 
|                         | Few-shot detector     | Self-Refine [[9]](https://selfrefine.info/) |


The final question is crucial as well, how to update the model behavior by using the guidance? It could be done at the input (enhancing the context), at the output (with a supervised corrector) or update the model parameters (for comparabLMs  smaller models or when models weights are accessible).

### How to apply?
|Critique-apply category | Applying the critique | Representative papers  |
|---                     |---                    |---                     |
|at the input            | Input context         | MemPrompt [[8]](https://memprompt.com) | 
|at the output           | Decoder, corrector    | Learning-to-repair [[7]](https://aclanthology.org/2022.findings-naacl.26/) |
|at the parameters       | Loss function         | ProStruct [[2]](https://aclanthology.org/D18-1006.pdf) |
|                        | Causal tracing        | [[in-progress]](https://niket.tandon.info) |


## How does this research position in the bigger picture of ChatGPT and LLMs?
LLMs have several important aspects with open research questions that we abbreviate as "The CRITERIUM". LLMs must be controllable, responsible, interactive, trustworthy, environmental friendly, reasonable, be able to induce facts, and work in a multimodal+multilingual setting. The proposed topic of natural language guided reasoning broadly covers two of these aspects *interactive* systems that learn from errors and are teachable and personalized; and *reasonable* systems that exhibit for instance commonsense and moral reasoning. We also strive for the models to be trustworthy and faithful in their reasoning.

![Bigger landscape](https://raw.githubusercontent.com/nikett/about/main/criterium-annotated.jpg)



## Selected publications:
1. Niket, Gerard, Fabian, Gerhard Weikum. “WebChild: harvesting and organizing commonsense knowledge from the web.” WSDM 2014
2. Niket, Bhavana, Joel et. al. “Reasoning about Actions and State Changes by Injecting Commonsense Knowledge.” EMNLP 2018
3. Dheeraj, Niket, Peter Clark et. al. “What-if I ask you to explain: Explaining the effects of perturbations in procedural text.” EMNLP Findings 2020
4. Aman, Niket, Dheeraj, et. al. “Think about it! Improving defeasible reasoning by first modeling the question scenario.” EMNLP 2021
5. Aman, Dheeraj, Niket et. al. “Could you give me a hint? Generating inference graphs for defeasible reasoning.” EMNLP Findings 2021
6. Niket, Aman, Peter et. al. “Interscript: A dataset for interactive learning of scripts through error feedback.” AAAI Workshop on Interactive ML (2021)
7. Niket, Aman, Peter et. al. “Learning to repair: Repairing model output errors after deployment using a dynamic memory of feedback.” NAACL 2022.
8. Aman, Niket, Peter et. al. “Memory-assisted prompt editing to improve GPT-3 after deployment.” EMNLP 2022.
9. Aman, Niket, et. al. "Self-Refine: Iterative Refinement with Self-Feedback." ArXiv abs/2303.17651 (2023)

