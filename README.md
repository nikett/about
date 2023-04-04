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
|Critic category | Critics| Representative paper |
|---|---|---|
|Knowledge as guidance| pre-constructed KG | WebChild-KB [[1]]() |
|  |pre-designed rules| Verb-rules [[8]]() |
|  |pre-compiled sent.| hasPart-KB [[7]]() |
|  |on-the-fly KG| inference graphs [[4]]() |
|Feedback as guidance |human feedback| Interscript [[11]]() |
|  |supervised feedback| Learning-to-repair [[9]]() |
|  |RL feedback| [ACL 2023 submission]()  |
|  |Self feedback| Self-Refine [[10]]() |
|Schemas as guidance | dyadic theory| [in-progress]() |
|  |state tracking: planning| [in-progress]() |
|  |claim graphs: scholar | [in-progress]() |


### What to ask?
|Critiqueable output <br>category | Critiqueable output     | Representative paper  |
|---|---|---|
|Structured explanation| Inference graph | Curious Model [[5]]() |
|| Reasoning chain | Quartet [[11]]() |
|| Moral graph | [EMMA](https://github.com/nikett/emma) |
|Unstructured explanation | Query understanding | MemPrompt [[x]]() |
|Structured output| Script generation | Interscript [[11]]() |
|| State tracking tensor | [in-progress]() |
|Unstructured output| Moral acceptability | [in-progress]() |


### When to ask?
|Critiqueability category | Critiqueability | Representative paper  |
|---|---|---|
|Supervised|supervised detector||
|Unsupervised| inconsistency detector|| 
||Few-shot detector |Self-Refine [[10]]() |

### How to apply?
|Critique-apply category | Applying the critique | Representative paper  |
|---|---|---|
|at parameters| loss func | ProStruct [[3]]() | 
|at input| input context | MemPrompt [[12]](memprompt.com) | 
|at output| decoder, corrector | Learning-to-repair [[9]]() |

### personalization


#### Some open research questions:
|  | Research Question |
|---|---|
|RQ| A collaborative framework for multi-critics |
|RQ| Study the effect of noisy critics | 
|RQ| Personalizing LLMs to user values, iteratively | 
|RQ| Analsis of how RL generalizes memory | 
|RQ| Iterative RL to generate better feedback | 
|RQ| Can we assist LLMs on reasoning tasks through state tracking? |
|RQ| Understanding salient state changes and their impact|
|RQ| Create a reasoning test benchmark for procedural understanding |
|RQ| Moral bottleneck models that rely on a theory of psychology |
|RQ| PDDL bottleneck models with an external planning engine |


#### References:
1. Tandon, Niket, Gerard de Melo, Fabian M. Suchanek and Gerhard Weikum. “WebChild: harvesting and organizing commonsense knowledge from the web.” WSDM 2014
2. Dalvi, Bhavana, Niket Tandon and Peter Clark. “Domain-Targeted, High Precision Knowledge Extraction.” TACL 2017
3. Tandon, Niket, Bhavana Dalvi, Joel Grus, Wen-tau Yih, Antoine Bosselut and Peter Clark. “Reasoning about Actions and State Changes by Injecting Commonsense Knowledge.” EMNLP 2018
4. Madaan, Aman, Dheeraj Rajagopal, Niket Tandon, Yiming Yang and Eduard H. Hovy. “Could you give me a hint? Generating inference graphs for defeasible reasoning.” EMNLP Findings 2021
5. Madaan, Aman, Niket Tandon, Dheeraj Rajagopal, Peter Clark, Yiming Yang and Eduard H. Hovy. “Think about it! Improving defeasible reasoning by first modeling the question scenario.” EMNLP 2021
6. Rajagopal, Dheeraj, Niket Tandon, Peter Clarke, Bhavana Dalvi and Eduard H. Hovy. “What-if I ask you to explain: Explaining the effects of perturbations in procedural text.” EMNLP Findings 2020
7. Bhakthavatsalam, Sumithra, Kyle Richardson, Niket Tandon and Peter Clark. “Do Dogs have Whiskers? A New Knowledge Base of hasPart Relations.” ArXiv abs/2006.07510 (2020)
8. Clark, Peter, Bhavana Dalvi and Niket Tandon. “What Happened? Leveraging VerbNet to Predict the Effects of Actions in Procedural Text.” ArXiv abs/1804.05435 (2018)
9. Tandon, Niket, Aman Madaan, Peter Clark and Yiming Yang. “Learning to repair: Repairing model output errors after deployment using a dynamic memory of feedback.” NAACL 2021.
10. Madaan, Aman, Niket Tandon, et. al. "Self-Refine: Iterative Refinement with Self-Feedback." ArXiv abs/2303.17651 (2023)
11. Tandon, Niket, Aman Madaan, Peter Clark, Keisuke Sakaguchi and Yiming Yang. “Interscript: A dataset for interactive learning of scripts through error feedback.” AAAI Workshop on Interactive ML (2021)
12. Madaan, Aman, Niket Tandon, Peter Clark and Yiming Yang. “Memory-assisted prompt editing to improve GPT-3 after deployment.” EMNLP 2022.

