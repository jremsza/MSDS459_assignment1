# Part 1: Summary of Knowledge Graphs - Chapters 1 & 2

Chapter 1 and 2 present the fundamentals of knowledge graphs. Chapter 1 introduces graph theroy and knowleadge graphs and chapter 2 walks through knowledge graph modeling and representation.

### Knowledge Graphs

Graph theory studies the properties and relationships of graphs, which are structures made up of nodes (vertices) connected by edges. It originated as a formal study with mathematicians like Euler, who used graphs to solve problems like the Seven Bridges of Konigsberg, focusing on the connections between objects rather than their physical properties.

In computer science, graph theory became a fundamental framework for solving computational problems involving networks and relationships. Key applications include:

Algorithms: Classic algorithms like Edsger Dijkstra’s shortest-path algorithm, used for finding the most efficient routes in networks (e.g., GPS navigation), and solutions to problems like the traveling salesman problem, which optimizes paths through multiple nodes.
Data Structures: Graphs are a core data structure, used to model relationships in databases, social networks, and the internet’s structure.
Artificial Intelligence (AI): Graph theory supports AI through expert systems, sequential models like Hidden Markov Models (HMMs) and Conditional Random Fields (CRFs) for pattern recognition, planning (where state and action spaces are graphs), constraint satisfaction (e.g., graph coloring for scheduling), and graph databases for structured data querying.

Graph theory has enabled the emergence of knowledge graphs (KGs) as a popular method for representing data by providing a mathematical foundation for modeling complex relationships and networks. KGs are valuable because they add semantic meaning to data through structured relationships, enabling better query interpretation, enhanced reasoning, and more precise search results at scale.

Knowledge graphs are deployed in a number of industries such as scientific publications and acedemic papers, ecommerce products and companies, social networks, and geopolitical events.

 A blog titled _Why You Need a Knowledge Graph, And How to Build It_ goes deeper on Knowledge graphs giving examples of there applications of fraud detection, supply chain and healthcare case managment. In addition, the author lays out a solid case for when to drop relational database for graph databases. Relational databases face significant challenges when managing networks of events, people, and resources, as their performance degrades exponentially with larger network sizes, creating difficulties for SQL analysts. In contrast, graph databases offer a more efficient solution, maintaining relatively linear performance regardless of network complexity, making them ideal for handling intricate, interconnected data. Looking ahead, enterprise data groups are likely to adopt a hybrid strategy, leveraging relational databases for isolated, function-specific analysis while employing knowledge graphs to manage complex processes that span multiple areas of a business (Pugsley 2023).

### Knowledge Graph Modeling

The most important aspect of knowledge graph modeling is the triple. The triple is standardized structure for representing relationships between entities. As the name implies their are 3 parts, subject: The entity or thing being described, predicate, the relationship connecting the subject to the object and object, the entity related to the subject through the predicate.

**Resource Description Framework**
Resource description framework is a standardized method to represent and connect data for representing information on the web. RDF organizes information into triples, where entities are represented as nodes and relationships as edges. The RDF Schema (RDFS) is a semantic extension of the Resource Description Framework (RDF) that provides a standardized vocabulary for defining classes and properties, enabling the creation of simple ontologies to structure RDF data. RDFS enhances RDF by adding semantics, allowing it to serve as a language for building schemas that specify domain-specific vocabularies. 

**Property-Centric Models**
Property-centric models on the other hand are simpler versions of the RDF that rely on properties to be directly attached to nodes and edges as key-value pairs. This structure is particularly useful when relationships themselves have important attributes (logistics systems - where a route might have a "capacity" property). 

A comparison of the two data models is highlighted in the article _Property Graphs vs. Knowledge Graphs_. Property Graphs, built using property-centric models, are usually described as simpler, with a focus on user-friendly visual representations and no fixed schema. This makes them adaptable to structured and semi-structured data. Where as RDF offers a more uniform and flexible way to represent knowledge, especially for semantic reasoning and integration across diverse ontologies, as it treats predicates (properties) as resources themselves, enabling advanced querying with languages like SPARQL (Foote 2022). 

**Wikidata Model**
The aim of this model is to build a cental, multilingual knowledge graph to record the structured data of Wikipedia articles. This model is a way to structure and organize knowledge, making it easy for computers to understand and connect information to mitigate the need for volunteers to maintain the data.
The Wikidata model uses items to represent entities with each identifier. These items are connected through properties, which are relationships like "is an instance of" or "was born in." This creates a network where everything is interconnected.

### Semantic Web Architecture

The Semantic Web is about transforming the web from a collection of documents meant for human consumption into a web of data that computers can understand, reason with, and act upon. The architecture of the semantic web can be thought of as a layered cake.  RDF provides the base and extensions such as RDFS and OWL enable increasingly complex modeling. This hierarchical structure spans from basic elements (URIs and Unicode) at the bottom to user-facing applications at the top. The middle layers contain critical components for querying, ontological modeling, and rule-based reasoning. The architecture also addresses important considerations like data provenance and trust, as verifying the accuracy and reliability of knowledge remains an ongoing research challenge in knowledge graph systems. 

### References

Foote, Keith D. "Property Graphs vs. Knowledge Graphs." DATAVERSITY. January 5, 2022. https://www.dataversity.net/property-graphs-vs-knowledge-graphs/.

Kejriwal, Mayank, Knoblock, Craig A., and Szekely, Pedro. Knowledge Graphs: Fundamentals, Techniques, and Applications. The MIT Press, 2021.

Pugsley, Stan. 2023. "Why You Need a Knowledge Graph, and How to Build It: A Guide to Migrating from a Relational Database to a Graph Database." Towards Data Science. August 9, 2023. https://towardsdatascience.com/why-you-need-a-knowledgegraph-and-how-to-build-it-ac4f35cb75b7/.