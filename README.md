# Natural Language Guided Reasoning

## Problem
Models can be unreasonable and large models can be hard to finetune, can we guide them at inference time? Guidance takes up different forms such as corrections, knowledge, Web retrieval based guidance, and theories and schemas e.g. from psychology, and human preferences. Visionaries in AI and psychology have considered feedback and correction (i.e., guidance) as a requirement for truly intelligent AI systems that learn from errors and improve with time.


## Goal
A computational model of the theory of recursive reminding suggesting that humans record error context and correction received in their episodic memory for the future. To realize this, we need a general memory architecture where input = question, output = critiqueable output and then guidance from various agents can iteratively improve the output. This memory can be per user, thus leading to personalized models.

## Approach
Iterative approach to effectively use guidance obtained from various agents:

- Background Knowledge as guidance (pre-large models):
|.|details|
|---|---|
|pre-constructed KG | canonical WebChild-KB [1], free form triples [2] |
|pre-designed rules| Verb-rules [8] |
|pre-compiled sentences or paragraphs| hasPart-KB [7] |
|on-the-fly generated KG| inference graphs [4] |


- Feedback as guidance:
|.|details|
|---|---|
|human| Interscript [11] |
|supervised| Learning-to-repair [9] |
|RL| ACL 2023 (under review)  |
|Self| Self-Refine [10] |


- Schemas as guidance:
|.|details|
|---|---|
|dyadic theory from psychology| todo |
|state tracking from planning| todo |
|claim graphs from scholar | todo |


### Open research questions:
| . | Title | Description |
|---|---|---|
| RQ1| Can we assist LLMs by letting them think via state tracking? | e.g., for event reasoning or other QA tasks? |
|RQ2|  (a) Can we define and develop a model of saliency for state changes?  (b) Do salient state changes assist LLMs w/ state tracking | Among the many possible state changes, can we identify the salient ones that will likely carry across different descriptions of the process. |
|Resource| A reasoning benchmark for procedural understanding. | Small training partition, largely a test set |
|RQ3| PDDL bottleneck models with an external planning engine | thinking of collaborating with Chris Callison Burch on his research idea |
| RQ1| Multiple agents as MoE effectively collaborate | e.g., ethical values guidance via human or supervised on human feedback and factual via Web? |



References:
1. Tandon, Niket, Gerard de Melo, Fabian M. Suchanek and Gerhard Weikum. “WebChild: harvesting and organizing commonsense knowledge from the web.” WSDM 2014
2. Dalvi, Bhavana, Niket Tandon and Peter Clark. “Domain-Targeted, High Precision Knowledge Extraction.” TACL 2017
3. Tandon, Niket, Bhavana Dalvi, Joel Grus, Wen-tau Yih, Antoine Bosselut and Peter Clark. “Reasoning about Actions and State Changes by Injecting Commonsense Knowledge.” EMNLP 2018
4. Madaan, Aman, Dheeraj Rajagopal, Niket Tandon, Yiming Yang and Eduard H. Hovy. “Could you give me a hint? Generating inference graphs for defeasible reasoning.” EMNLP Findings 2021
5. Madaan, Aman, Niket Tandon, Dheeraj Rajagopal, Peter Clark, Yiming Yang and Eduard H. Hovy. “Think about it! Improving defeasible reasoning by first modeling the question scenario.” EMNLP 2021
6. Rajagopal, Dheeraj, Niket Tandon, Peter Clarke, Bhavana Dalvi and Eduard H. Hovy. “What-if I ask you to explain: Explaining the effects of perturbations in procedural text.” EMNLP Findings 2020
7. Bhakthavatsalam, Sumithra, Kyle Richardson, Niket Tandon and Peter Clark. “Do Dogs have Whiskers? A New Knowledge Base of hasPart Relations.” ArXiv abs/2006.07510 (2020)
8. Clark, Peter, Bhavana Dalvi and Niket Tandon. “What Happened? Leveraging VerbNet to Predict the Effects of Actions in Procedural Text.” ArXiv abs/1804.05435 (2018)
9. Tandon, Niket, Aman Madaan, Peter Clark and Yiming Yang. “Learning to repair: Repairing model output errors after deployment using a dynamic memory of feedback.” NAACL (2021).
10. Madaan, Aman, Niket Tandon, et. al. "Self-Refine: Iterative Refinement with Self-Feedback." ArXiv abs/2303.17651 (2023)
11. Tandon, Niket, Aman Madaan, Peter Clark, Keisuke Sakaguchi and Yiming Yang. “Interscript: A dataset for interactive learning of scripts through error feedback.” AAAI Workshop on Interactive ML (2021)


- Who to ask : human agent, supervised agent, RL agent, self agent, KB agent, Web agent
- When to ask: supervised detector, inconsistency detector, few shot detector
- What to ask: critique the explanation, critique the understanding, 
- How to use: 
|---|---|
|on the parameter side| as loss function or decoding function, as multitask learning|
|on the input side| input context enrichment, in-context examples or prompt enrichment|
|on the output side| decoders and correctors|
|on the overall architecture side| as a bottleneck (retrievals, theories)|

