# Natural Language Guided Reasoning

## Problem
Models can be unreasonable and large models can be hard to finetune, can we guide them at inference time? Guidance takes up different forms such as corrections, knowledge, Web retrieval based guidance, and theories and schemas e.g. from psychology, and human preferences. Visionaries in AI and psychology have considered feedback and correction (i.e., guidance) as a requirement for truly intelligent AI systems that learn from errors and improve with time.

## Goal
A computational model of the theory of recursive reminding that suggests humans record error context and correction received in their episodic memory for the future. To realize this, we need a general memory architecture where input = question, output = critiqueable output and then guidance from various agents can iteratively improve the output. This memory can be per user, thus leading to `personalized models`.

## Approach
Iterative approach to effectively use guidance obtained from various critics. We build upon four key questions:
- Who to ask
- What to ask
- When to ask
- How to apply


### Who to ask?
|Critic category        | Critics                 | Representative papers     |
|---                    |---                      |---                        |
|Knowledge as guidance  |Pre-constructed KG       | WebChild-KB [[1]](https://www.mpi-inf.mpg.de/departments/databases-and-information-systems/research/yago-naga/commonsense/webchild)       |
|                       |On-the-fly KG            | Inference graphs [[3]](https://aclanthology.org/2021.findings-acl.456.pdf)  |
|Feedback as guidance   |Human feedback           | Interscript [[7]](https://www.semanticscholar.org/paper/Interscript%3A-A-dataset-for-interactive-learning-of-Tandon-Madaan/07d5bba7d2bc511c88eb143a926d3c297298ad15) |
|                       |Supervised feedback      | Learning-to-repair [[6]](https://aclanthology.org/2022.findings-naacl.26/)|
|                       |RL feedback              | [ACL 2023 submission](https://niket.tandon.info)   |
|                       |Self feedback            | Self-Refine [[9]](https://selfrefine.info/)      |
|Schemas as guidance    |Dyadic theory            | [in-progress](https://github.com/allenai/emma/tree/dev)           |
|                       |State tracking: planning | [in-progress](https://github.com/allenai/openpi_v2)           |
|                       |Claim graphs: scholar    | [in-progress](https://github.com/nikett/claimgraph)           |
|Preference as guidance |User personalization     | [in-progress](https://niket.tandon.info)           |



### What to ask?
|Critiqueable category    | Critiqueable output     | Representative papers  |
|---                      |---                      |---                     |
|Structured explanation   | Inference graph         | Curious [[4]](https://aclanthology.org/2021.emnlp-main.508/)  |
|                         | Reasoning chain         | Quartet [[5]](https://aclanthology.org/2020.findings-emnlp.300.pdf)       |
|Unstructured explanation | Query understanding     | MemPrompt [[8]](https://memprompt.com) | 
|Structured output        | Script generation       | Interscript [[7]](https://www.semanticscholar.org/paper/Interscript%3A-A-dataset-for-interactive-learning-of-Tandon-Madaan/07d5bba7d2bc511c88eb143a926d3c297298ad15) |
|                         | Moral graph             | [EMMA](https://github.com/nikett/emma) |
|                         | State tracking tensor   | [in-progress](https://github.com/allenai/openpi_v2)         |



### When to ask?
|Critiqueability category | Critiqueability       | Representative papers |
|---                      |---                    |---                    |
|Unsupervised             | Inconsistency detector| [EMMA](https://github.com/nikett/emma)| 
|                         | Few-shot detector     | Self-Refine [[9]](https://selfrefine.info/) |



### How to apply?
|Critique-apply category | Applying the critique | Representative papers  |
|---                     |---                    |---                     |
|at the input            | Input context         | MemPrompt [[8]](https://memprompt.com) | 
|at the output           | Decoder, corrector    | Learning-to-repair [[6]](https://aclanthology.org/2022.findings-naacl.26/) |
|at the parameters       | Loss function         | ProStruct [[2]](https://aclanthology.org/D18-1006.pdf) |
|                        | Causal tracing        | [in-progress](https://niket.tandon.info) |



## Open research questions:
|  | Research Question |
|---|---|
|RQ| Personalizing LLMs to user values, iteratively | 
|RQ| Moral bottleneck models relying on the dyadic theory from psychology |
|RQ| A collaborative framework for multi-critics |
|RQ| Study the effect of noisy critics | 
|RQ| Analyzing how RL generalizes memory | 
|RQ| Iterative RL to generate better feedback | 
|RQ| Can we assist LLMs on reasoning tasks through state tracking? |
|RQ| Understanding salient state changes and their impact|
|RQ| Create a reasoning test benchmark for procedural understanding |
|RQ| Planning bottleneck models using an external engine to plan |
|RQ| What is the best representation of memory, how does memory evolve |
|RQ| Effect of adversarial feedback on the memory |
|RQ| Effect of faith harming feedback in the memory in a multiuser setup |



## Selected references:
1. Niket, Gerard de Melo, Fabian M. Suchanek and Gerhard Weikum. “WebChild: harvesting and organizing commonsense knowledge from the web.” WSDM 2014
2. Niket, Bhavana, Joel, Wen-tau Yih, Antoine and Peter Clark. “Reasoning about Actions and State Changes by Injecting Commonsense Knowledge.” EMNLP 2018
3. Aman, Dheeraj, Niket, Yiming Yang and Eduard H. Hovy. “Could you give me a hint? Generating inference graphs for defeasible reasoning.” EMNLP Findings 2021
4. Aman, Niket, Dheeraj, Peter Clark, Yiming Yang and Eduard H. Hovy. “Think about it! Improving defeasible reasoning by first modeling the question scenario.” EMNLP 2021
5. Dheeraj, Niket, Peter Clarke, Bhavana and Eduard H. Hovy. “What-if I ask you to explain: Explaining the effects of perturbations in procedural text.” EMNLP Findings 2020
6. Niket, Aman, Peter Clark and Yiming Yang. “Learning to repair: Repairing model output errors after deployment using a dynamic memory of feedback.” NAACL 2022.
7. Niket, Aman, Peter Clark, Keisuke and Yiming Yang. “Interscript: A dataset for interactive learning of scripts through error feedback.” AAAI Workshop on Interactive ML (2021)
8. Aman, Niket, Peter Clark and Yiming Yang. “Memory-assisted prompt editing to improve GPT-3 after deployment.” EMNLP 2022.
9. Aman, Niket, et. al. "Self-Refine: Iterative Refinement with Self-Feedback." ArXiv abs/2303.17651 (2023)


