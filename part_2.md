# Part 2: Summary of Knowledge Graphs Textbook - Chapters 3 & 5

Chpater 3 and 5 focus on Knowledge graph construction. Chapter 3 zeros in on domain discovery. It is one thing to find topics on a certain domain but the key to building suitable knowleadge bases is finding relavent domain topics.

### Crawlers

**Focused crawlers** - Crawling refers to a set of techniques primarily used for domain discovery. A crawler is a specialized program that navigates the web and collects a corpus of data by following predefined criteria that is user or domain specific. 
Four issues must be addressed before designing a focused crawler.
1.) How do we specify the domain to begin with?
2.) How do we explore the link structure of the web to discover relevant pages? 
3.) How do we use the content of the web pages to determine relevance?
4.) What kinds of user interactions are permitted when performing domain discovery?

The overall goal is to keep the downlaoded webpages for processing at a minimum while maximizing the relavent webpages processed. Using good seed pages is a way to ensure webpages are relavent. General elements needed when designing a crawler include: input mechanism, page retrival, content processing, priority assignment, and expansion. Best-First crawlers use term frequency vectors for computing topic relevance. 

Another type of focused crawler is the semantic crawler. This type uses term taxonomies or ontologies to deviate from solely reling on lexical matching like tf. The appraoch is to retrieve all terms that are conceptually similar to the topic terms in the ontology and use the additional terms to supplement the topic description.

**Inteligent crawlers** - 

Learning crawlers employ supervised machine learning to identify web pages relevant to user interests. They function by training classifiers on labeled datasets where users have marked pages as relevant or irrelevant. During crawling, these classifiers evaluate each new page and assign priority levels. Research demonstrates that combining page content analysis with link context produces superior results compared to either method independently.

### Domain Discovery Tool
 
 The Domain Discovery Tool (DDT) is an interactive system designed to help users explore and understand specific topics or domains as they appear on the web. Users analyze web pages from search engines or crawlers, give feedback on their relevance, and use this feedback to train classifiers for identifying relevant content.

 A web search for domain discovery tool yielded a landing page that walks users through a DDT tool built by NYU scholars. Further investigation points to a GitHub repo for the tool and how to use it. What is unclear is if this the tool or a tool for DDT. Further review in the web serach did not clarify this as the other hits were not realated.

https://domain-discovery-tool.readthedocs.io/en/latest/
https://github.com/ViDA-NYU/domain_discovery_tool

## Chapter 5: Web Information Extraction:

Chapter 3 was concerned with finding relevant domain specfic sources but chapter 5 focuses on extracting that information from those sources.

Challenges arise when performing web information extraction due to factors such as inconsistent web source structure, the need for automation at scale, and the high volume and velocity of web content. These elements can complicate data parsing, increase the likelihood of extraction errors, and demand robust systems that can adapt to dynamic web environments.

### Wrappers 

One way to deal with these challenges is to use a wrapper. A wrapper is designed to extract structured data from semi-structured sources like HTML web pages. Wrappers serve as the interface between a web data source and a downstream application, converting the loosely structured content into a machine-readable format such as JSON, XML, or CSV. The key function of a wrapper is to identify, locate, and extract specific pieces of information from a page—such as product names, prices, publication dates, or article titles—based on patterns, layout, or structure. Different types of wrappers are needed for different structured web pages the three outline in the text are:
1.) Manual Wrappers (Rule-Based) - Hand-coded scripts that rely on hardcoded rules.
2.) Supervised - generated using labeled training examples where the desired information has been manually identified. 
3.) Unsupervised - Unsupervised wrappers attempt to learn data extraction rules without any labeled examples, relying instead on patterns, visual similarity, repetition, or structural cues in the HTML.

The text examines web information extraction (web IE) systems and their comparative analysis across three dimensions. Unlike NLP extraction tasks with standardized datasets from venues like MUC, web IE lacks common benchmarking corpora, making empirical performance comparisons difficult. Instead, systems are typically evaluated based on capabilities and features. The analysis reveals several important trends, particularly in the task domain dimension. Manual and supervised web IE systems generally target cross-website extraction, while semisupervised and unsupervised systems focus on template pages common in the Deep Web. Unsupervised systems inherently require common templates to function effectively, which is reasonable given their lack of labeled training data. Additionally, wrapper systems show considerable heterogeneity in their extraction levels (field, record, page, and site), with tools like RoadRunner and STALKER capable of record or page-level extraction, but site-level extraction remains largely unexplored, presenting a clear opportunity for future research.

I found an interesting paper that takes wrappers and scales them to the web rather than just a website. The paper _Automatic Wrappers for Large Scale Web Extraction_ focuses on developing automated techniques for creating wrappers from web pages at scale. It proposes methods to generate wrappers without manual intervention by leveraging patterns in web page structures, such as HTML tags and DOM trees, to identify and extract relevant information. The authors emphasize improving accuracy and scalability, addressing challenges like handling diverse website layouts and dynamic content. Their approach demonstrates effectiveness in large-scale experiments, achieving high precision and recall compared to traditional manual or semi-automated wrapper induction methods (Davli, Kumar, Soliman 2011).


#### References 

Dalvi, Nilesh, Ravi Kumar, and Mohamed A. Soliman. "Automatic Wrappers for Large Scale Web Extraction." Proceedings of the VLDB Endowment 4, no. 4 (2011): 219-230.

Kejriwal, Mayank, Knoblock, Craig A., and Szekely, Pedro. Knowledge Graphs: Fundamentals, Techniques, and Applications. The MIT Press, 2021.

VIDA-NYU. "Domain Discovery Tool (DDT) Documentation." Read the Docs. Accessed April 12, 2025. https://domain-discovery-tool.readthedocs.io/en/latest/.