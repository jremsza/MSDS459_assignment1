## Part 5: Natural Language Processing in Action - Chapter 11

This chapter discusses knowleadge graphs and information retrivial with the goal. The authors definition of a knowleadge graph is a flexible data structure designed to store knowledge. This allows for the model to extract meaningful information about a topic to essentially understand what it reads (Lane and Dyshel 2025). Below is a summary from the main topics in the text.  

#### Information Extraction from Natural Language

At a high level, the way that the model can extract facts from the text is by parsing the text into entities and discovering the relations between them. A graph data structure is an appropriate data store for the knowledge graph, also called knowledge database. The nodes in the graph would are the entities, and the the edges represent the relations between entities. 

Bridging the commonsense gap in LLMs requires integrating knowledge graphs and symbolic reasoning. This "missing link" in NLP enables grounding — anchoring model outputs in real-world knowledge — and brings us closer to building truly intelligent AI systems. The most important algorithm in this grounding process is knowledge extraction.

The process of knowleadge extract involves 4 main steps:
1. Named entity recognition
2. Corefernce resolution
3. Relation extraction
4. Update knowleadge graph

 The spaCy language models include the building blocks for knowledge extraction: named entity recognition, coreference resolution, and relation extraction.

 - **Named entity recognition (NER)**

 The first step in knowledge extraction is identifying named entities—people, places, dates, and other meaningful elements in text. This process, known as Named Entity Recognition (NER), can be approached using pattern-matching (e.g., regex) or neural models. While neural methods are common, regular expressions can be more precise for extracting structured data like GPS coordinates, dates, prices, and numbers.  The first algorithm in the knowledge extraction pipelinethe is the spaCy language model that tokenizes text, and tags each token with the linguistic features needed for knowledge extraction. 

 - **Coreference resolution**

 Coreference resolution identifies all mentions of the same noun in a sentence, helping to consolidate references to the same entity. This prevents redundancy in a knowledge graph and reduces the risk of introducing incorrect relationships.

 - **Relation extraction**
 
 Sentence can contain several relations as well that need to be extracted. The two main ways in NLP to perform relation extraction is dependency parsing and constituency parsing. Dependency parsing uses tree data structures to give the model a representation of the logic and grammar of a sentence and illistrates the relationships between words. Constituency parsing aims to parse a sentence into a series of sub constituents. Its approach is more top down, trying to iteratively break constituents into smaller units and relationships between them.

To extract relations from text, we identify subject-verb-object triplets using the spaCy package's Matcher method, which recognizes patterns of part-of-speech (POS) tags in sequences.

#### Semantic Structure Analysis

Document chunking is a prerequisite for knowledge extraction, helping convert unstructured text into semistructured segments that are easier to search and extract facts from — a necessary step in building knowledge bases like NELL or Freebase. Sentence segmentation is the most common form of chuncking and is the first step in the knowledge extraction pipeline. Sentence segmentation is done using regex or ML algothrims wiht the latter being the perferred method.

If you do a web search for sentence segmenters, you’re likely to be pointed to various regular expressions intended to capture the most common sentence boundaries.

A web search for sentence segmenters gives mixed results. Some are browser based hybrid AI regex model (crimson.ai 2025) and there are others that give strictly ML such as the huggingface segment any text model 

SpaCy Python library offers convenient tools for sentence segmentation, and its accuracy largely stems from its use of dependency parsing. Dependency parsing identifies the grammatical relationships between words in a sentence enabling spaCy to handle ambiguous punctuation and capitalization more reliably. When combined with token embeddings, this structure enhances the precision of segmentation, even in complex or informal text. However, there is a tradeoff between speed and accuracy. The regex method is very fast but not accurate, and the spaCy method is much slower but much more accurate.

The text recomends using MiniML for text embedding. MiniLM is a compact, high-performance distilled BERT model that balances accuracy and speed. In sentence segmentation pipelines, MiniLM is used to encode each sentence's meaning into vector form. This allows for more intelligent splitting, filtering, and downstream processing — especially when extracting knowledge or performing retrieval based on semantic similarity, not just surface features. (serach web for MiniML info)

#### Building Knowledge Graphs

Knowledge triples represent isolated facts using the structure: entity–relation–value (e.g., "Einstein–has-profession–physicist"). The NELL system by Carnegie Mellon focuses on extracting "kind-of" relationships and normalizes text by lowercasing and removing punctuation, using underscores for multi-word names. Each triple captures a factual relationship, where the relation (often a verb phrase like is or has) links an entity to a value, both of which are named entities.

Knowledge retrival in a graph database is done using SPARQL, Cypher, and AQL quary langauges. SPARQL is open source and not desginated for a specfic graph database so that is the focus of this text. A quick internet search about SPARQL sheds light on the recomended data base titled GraphDB. The website states "SPARQL is a SQL-like query language for RDF data. SPARQL queries can produce result sets that are tabular or RDF graphs depending on the kind of query used" (Ontotext 2023). Further more the website gives better guidance to written quaries in a general form:

First, define prefixes to URIs with the PREFIX keyword. In the example below, we set bedrock as the default namespace for the query.

Next, use INSERT DATA to signify you want to insert statements. Write the subject predicate object statements.

Finally, execute this query

##### References

Crimson AI. 2025. "Katana: A Fast, Accurate Sentence Segmenter." Accessed April 8, 2025. https://www.crimsoni.ai/katana/.​

Lane, Hobson, and Maria Dyshel. 2025. Natural Language Processing in Action. 2nd ed., 470–512. Shelter Island, NY: Manning Publications.

Ontotext. 2025. "SPARQL." GraphDB Documentation, version 10.1. Last updated January 23, 2025. Accessed April 8, 2025. https://graphdb.ontotext.com/documentation/10.1/sparql.html.