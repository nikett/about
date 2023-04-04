
## Natural Language Guided Reasoning

### Problem
LLMs can be unreasonable, can we guide through corrections, knowledge, Web retrieval, theories e.g. from psychology, and human preferences. 

### Goal
A general memory architecture where input = question, output = critiqueable output and then guidance from various agents can iteratively improve the output. It can be viewed as a computation model of the theory of recursive reminding.

### Approach
Iterative approach to inject guidance obtained from various agents. The guidance is optimized for current input (can recall guidance from a memory). LLM  is frozen.

### Insights
Memory based architecture ... leading to ... Personalization


Background knowledge as guidance:
|.|details|
|---|---|
|pre-constructed KG (with free-form/ canonical/ verbalized triples)| todo |
|pre-designed rules| todo |
|on-the-fly generated KG| todo |
|pre-compiled sentences or paragraphs| todo |


Open research questions:
| . | Title | Description |
|---|---|---|
| RQ1| Can we assist LLMs by letting them think via state tracking? | e.g., for event reasoning or other QA tasks? |


Feedback as guidance:
|.|details|
|---|---|
|human| todo |
|supervised| todo |
|RL| todo |
|Self| todo |


Open research questions:
| . | Title | Description |
|---|---|---|
| RQ1| Multiple agents as MoE effectively collaborate | e.g., ethical values guidance via human or supervised on human feedback and factual via Web? |


Schemas as guidance:
|.|details|
|---|---|
|dyadic theory from psychology| todo |
|state tracking from planning| todo |
|claim graphs from scholar | todo |

Open research questions (todo add more):
| . | Title | Description |
|---|---|---|
| RQ1| Can we assist LLMs by letting them think via state tracking? | e.g., for event reasoning or other QA tasks? |
|RQ2|  (a) Can we define and develop a model of saliency for state changes?  (b) Do salient state changes assist LLMs w/ state tracking | Among the many possible state changes, can we identify the salient ones that will likely carry across different descriptions of the process. |
|Resource| A reasoning benchmark for procedural understanding. | Small training partition, largely a test set |
|RQ3| PDDL bottleneck models with an external planning engine | thinking of collaborating with Chris Callison Burch on his research idea |





- Who to ask : human agent, supervised agent, RL agent, self agent, KB agent, Web agent
- When to ask: supervised detector, inconsistency detector, few shot detector
- What to ask: critique the explanation, critique the understanding, 
- How to use: 
|---|---|
|on the parameter side| as loss function or decoding function, as multitask learning|
|on the input side| input context enrichment, in-context examples or prompt enrichment|
|on the output side| decoders and correctors|
|on the overall architecture side| as a bottleneck (retrievals, theories)|

