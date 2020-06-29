# Day 1:

## William Cohen: KR for KBQA and KBC

### Abstract: 
Interesting classification of KG-facts:  
*  (True facts) - which are there in KG.  
*  (Plausible facts) - extracted by KBC techniques (involves generalization).  
*  (Entailed facts) - result of logical operations on existing facts without involving generalization   
*  (Entailment+Inference) - logical operations + generalizations

The current talk focuses on Logical facts while Jure's talk focuses on Entailment+Inference.
 
Typical KB-QA: Question --> Symbolic logical form --> Answer
However, this requires gold-symbolic forms which are tough to collect. The solution is to make them as soft-logical forms, which are then executed. The soft-logical forms use predefined templates :thought_balloon: *(Choosing or generating templates automatically is an open problem)* whose arguments are soft (uses weighted sets). NQL and EmbQL are papers in this direction.

**Facts as Experts** is another interesting direction where they try to add this capability to an open-domain question answering model, using a triple-store from KB as a memory. The transformer is added with a capability to query the KB using automatically generated soft-logical forms.

Papers: 
* NQL (Cohen et. al., 19), EmbQL
* Facts as Experts (Paper not yet available). Background: Entity as Experts (Fevry et. al., 20)

## Jure Leskovec: Representation Learning for Logical Reasoning in Knowledge Graphs
BetaE (ComplexLinkPrediction)

## Jamie Taylor: A long view on Identity

Linguistic analysis of what it takes to construct a knowledge base 

## Xin Luna Dong: Harvesting knowledge from the semi-structured web

Abstract: OpenIE from semi-structured data. Web-documents like movie page contain clear fields which can be used to extract information. :thought_balloon: *This is apparently more difficult than I would have guessed - due to the difference in web-page structures, etc.* :thought_balloon: *Looks like a practical-industrial use for OpenIE. However, precision for open-relations is not yet at 90.* :bulb: *I believe we can take support from OpenIE extractions of unstructured text to improve confidence in existing extractions.* :bulb: *They extract each extraction from a web-page independently. Trivial to add iterations as in imojie.*

Papers: Ceres (Lockard et al., VLDB18), OpenCeres (Lockard et al., NACL19), ZeroShotCeres (Lockard et al., ACL20)  
Resources: SWDE benchmark, DI2KG benchmark

# Day 2:

# Day 3:
## Jonathan Berant: Symbolic and distributed representations for question answering

* Reasoning: combining evidence from multiple parts of input
* Reasoning can be easily probed by complex questions
* Answering research questions are very complex
---
* Web as Knowledge-base for answering complex questions (NAACL 18)
* Issue with symbolic models - limiting to certain formalisms
---
* QDMR - Question decomposition meaning representation 
* Question understanding as a standalone task (Leaderboard)
---
* Use it for Open Domain QA
* BreakRC+BERTQA
* Question decomposition improves Open Domain QA 
* But use it only for retrieval phase
* As exact answers from decomposition graphs are very noisy
---
* Faithfulness of modules
* Contextualized representations hurt!
* Parameterization affects faithfulness!
---
* Injecting reasoning skills in pre-trained LMs
* Numerical reasoning, "systematic" logical reasoning
* Reason over input-text and soft knowledge 
* Injecting numerical examples!

## Benjamin Van Durme: Embracing uncertainty as the target of prediction

(Joining Microsoft semantic machines in Summer 2020. Joint position with JHU)

* Definition of an agent
* Humans are uncertain in their judgements
* Crowdsourcing annotations with uncertainities
* http://decomp.io

## Heng Ji: Event-Centric Knowledge Base Construction

Entity-centric vs event-centric knowledge bases
Multi-view verification
Connect dots among multi-source, multi-media data

Event Graph Schema Induction Framework
Cross-media transfer - multi-media event extraction
Cross-media consistency reasoning - cross-media coreference accuracy
Ground events onto a Timeline

Hallway Chats:

Berant:
Tree-based
you don't want phrase embeddings to be completely contextualized
no generalization when you see contextualization
training on explanations helps to generalize on other datasets. SNLI --> MNLI
Dataset biases
common sense qa dataset + explanations

# Workshops:
8:00-8:25 (SciNLP) Ryan McDonald, End-to-end Neural Models for Evidence Retrieval from Biomedical Literature
8:25-8:50 (SciNLP) Vivi Nastase, Looking for the dark matter within knowledge graphs
9:15-10:00  (KBMM) Chenyan Xiong, Representation Learning and Reasoning with Semi-structured Free-Text Knowledge Graph
10:00-10:25 (SciNLP) Poster sessions - Session 1: Semi-Open Relation Extraction from Scientific Texts, Session 2: Incorporating Knowledge Bases into SciBERT and BioBERT pre-trained language models
10:25-10:50 (SciNLP) Iris Shen, Enriching a Web-scale Scientific Taxonomy by Combining Textual and Structural Information
10:45-11:15 (USKB) Fabio Petroni, How can we compare unstructured, structured and self-structured knowledge representation?
11:15-11:45 (USKB)  Colin Raffel, Answering Questions by Querying the Implicit Knowledge Base Inside T5
11:45-12:00 Break
12:00-12:45 (USKB) Panel Discussion

## (SciNLP) Ryan McDonald, End-to-end Neural Models for Evidence Retrieval from Biomedical Literature

covid-19 explorer, AUEB covid-19 search engine

Retrieval for scientific questions is much more challenging (BioASQ). Better retrievers are important
Retrieval model + Rescoring model
(Relevance/Term-based) + (Dense Interaction/X-attention)

First-stage retrieval - *hard to beat BM25*, need lots of data

Question-Generation Approach: pre-train with actual answer-question pairs. Use it on medline/pubmed articles
Approach for data augmentation

Neural models fail to capture required lexical matching
Hybrid models: term-vector + neural-vector

Better Search + Evidence

## (SciNLP) Vivi Nastase, Looking for the dark matter within knowledge graphs

"general" knowledge graphs - skipped

## (KBMM) Chenyan Xiong, Representation Learning and Reasoning with Semi-structured Free-Text Knowledge Graph
Microsoft AI Research

Transformer-XH (ICLR 2020)

Symbolic knowledge vs. Free-Text information
Our world is not so well-structured
Language is the carrier of our knowledge

Free-text Knowledge Graphs
Semi-structured Texts

Complex Factoid Question ANswering with a Free-text knowledge graph (WebConf 20)

Coverage is a huge issue in KG's impact
Wikipedia entities have high coverage
BERT Tagger can extract entities even on Open Domains

Relations are much more long-tailed

Free-Text KG
QbLink, QANTA

Transformer-XH : BERT+GAT
GAT vs BERT 
BERT: fully connected bag-of-words graph
Application in Multi-Hop/Evidence QA

Fully connected graph gives to very small change in result

Q: Connections are based on matching entities and not relations --> not so useful - can learn mostly on it's own

## (SciNLP) Iris Shen, Enriching a Web-scale Scientific Taxonomy by Combining Textual and Structural Information

Microsoft Academic Graph project
https://academic.microsoft.com/home

Taxonomy enrichment - required for academic papers which continuously introduce new concepts

## (USKB) Fabio Petroni, How can we compare unstructured, structured and self-structured knowledge representation?

Knowledge Representation - Unstructured, Structured
*Self-structured* knowledge can be stored in the parameters of a neural model
local information is often sufficient to solve the task

Knowledge intensive nlp tasks
1 slot filling
IE + QA
LAMA probe

Automatic KG accuracy on LAMA equivalent to training BERT on Wikipedia
Explainability - provide Wikipedia page or sufficient context

2 entity linking 

dense retrieval with MIPS and bi-encoder

3 open domain qa

TriviaQA, HotpotQA, Natural Questions, ELI5

Roberts et al T5, Guu et al REALM, Karphukhin et al DPR, Lewis et al RAG (2020)

Evidence

4 factual checking

FEVER

DREAM, RoBERTa, BART, RAG

5 factual generation

GPT, BART, RAG can generate factually

Hill climb on dataset and test on LAMA!

## (USKB)  Colin Raffel, Answering Questions by Querying the Implicit Knowledge Base Inside T5

T5!

Context-Free TriviaQA
Closed-Book Question Answering 
Knowledge internalization insider parameters
Was absolutely suprising initially!

REALM (Guu et al.) - mask only salient spans

multi-task pretraining did not help
T5-1.1+XXL
Close-book QA: brittle evaluation procedure
GPT-3
Retrieval-based approaches are required for evidences

## (USKB) Panel Discussion

Fine-tuning to primarily understand the QA format - not really to learn facts - it has learnt quite a bit in the pre-training stage itself

Disentangle linguistic and general knowledge

Automatically building knowledge bases as tough as solving the downstream application

High-precision language understanding

Incorporating logical rules in modern language models: 
Rules along with examples to generate training data for the model

Answering questions on logical structure of the text

Given the facts in context, transformers can perform multi-hop reasoning - complex reasoning tasks
More parameters --> more hops!

Structure of KB should be influence by machine and not the humans

