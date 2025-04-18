# Part 3: Summary of Knowledge Graphs - Chapter 4

Chapter 4 focuses on named entity recognition which is a critical element to building information extraction systems.

**Named Entity Recognition (NER)** is the process of identifying instances of predefined concepts within a specific domain from a corpus of texts. An Information Extraction (IE) system detects specific mentions in the text that correspond to these concepts, which are typically linked to classes in an ontology. A significant challenge is distinguishing and linking different mentions—like "The United Nations" and "U.N."—that refer to the same entity. This requires an additional step called instance matching to ensure the extracted data can be effectively queried, aggregated, or analyzed

NER is a KG construction problem (KGC): It builds the initial structure of the knowledge graph by identifying and extracting entities from text - gathering all the pieces (entities) needed to start assembling the graph.
Instance matching is a KG completion problem: It refines and enhances the graph by linking different mentions that refer to the same real-world entity. This ensures the graph is accurate and complete, like making sure all puzzle pieces that belong together are connected.
Both tasks are essential for creating a high-quality knowledge graph, which can be used in applications like semantic search, recommendation systems, or data integration.

### Challenges in Information Extraction (IE)

The text outlines several factors:
- IE is nontrivial due to the complexity and ambiguity of natural language - many different ways to say the same thing
- Models trained on concepts with a predefined ontology are not easily transferred if things change (data or language). 
- Ontology changes due to noval concepts - becomes more fine-grained. Causes a need for the entity typing mechanism to be retrained 
- Supervised and ontologically mediated NER use labeled data and ontologies and outperform Open Information Extraction (Open IE) and unsupervised NER, which rely on fewer resources. However, unsupervised NER has improved significantly over the past decade due to advancements in language models and self-supervised learning.

### Techniques for Named Entity Recognition

- **Supervised**
 Decision trees, maximum entropy models, HMMs, SVMs, and CRFs are all used for NER, most of these are sequence-labeling techniques that don't rely on the independent and identically distributed (i.i.d.) assumption common in many machine learning methods. The text illustrates why this matters: when classifying words in a sentence as entities (like locations or persons), considering words independently is flawed because context matters—for example, the word "the" is more likely to be followed by a location than not. Although classifying entire sequences jointly becomes computationally intractable for longer texts, models like HMMs and CRFs can account for dependencies between tokens without making strong independence assumptions

CRFs stand out as an appropriate model for NER with their ability to incorporate features from words before and after the target word. For instance, a CRF can use the word three positions earlier or the POS tags of words within a certain window as features. Unlike models that classify each word in isolation, CRFs excel by considering contextual relationships between words in a sequence. This is crucial for NER tasks where, for example, recognizing "United States" as a location entity requires understanding the relationship between adjacent words.

https://towardsdatascience.com/conditional-random-field-tutorial-in-pytorch-ca0d04499463/

- **Semisupervised and Unsupervised**

Running superivised models at scale requires increased manual labor for labeling training data as well as expesnive. A favorable approach in these circumstances is weak supervision or active learning. These methods require a smaller amount of human intervention, usually in the begining, to bootstrap the model and allowing to proceed without further supervision. Active learning begins with a small set of human-labeled examples, after which the learning algorithm identifies and requests labels for the most informative or uncertain samples—those where obtaining human input would provide maximum benefit to the model's performance. This targeted approach makes the annotation process more efficient by avoiding redundant labeling of samples the system can already classify with high confidence. 

- **Deep learning**

Deep learning approaches for Named Entity Recognition (NER) have gained significant popularity due to their superior performance without requiring manual feature engineering. These models can automatically learn relevant features from data, eliminating the need for handcrafted ontologies. Additionally, deep learning NER systems scale more effectively with larger datasets and more complex entity recognition tasks, making them increasingly preferred in modern NLP applications. 

RNN-LSTM approaches to NER often employ character-based architectures that model sentences as sequences of chracters rather than just words. This character-level NER methodology processes character sequences through highway networks over CNNs, followed by LSTM layers and softmax classifiers for final entity predictions. By analyzing text at the character level, these models achieve a finer-grained understanding of linguistic patterns than traditional word-level architectures, allowing them to better handle out-of-vocabulary words, morphological variations, and subword patterns critical for entity recognition.
 
### Evaluation of Information Extraction

It is nessecary to evaluate the performance of information extraction systems. Perscision and recall are metrics that are used for this purpose. 
**Precision** - measure of _correctness_ but taking the number of correct positives over the sum of correct and incorrect positives identified by the system (true positives + false positives).

**Recall**- measure of _completeness_ but taking the number of correct positives over the sum of true positives and false negitives identified by the system.

Further examination may be needed to decide which metric is of best interets based on the application. In medical diagnosis systems, high recall is typically preferred to identify as many disease cases as possible, accepting some false positives in exchange for comprehensive detection. Conversely, financial fraud detection systems often emphasize precision to minimize false positives that could inconvenience legitimate customers through wrongly declined transactions (Huilgol 2024).

There is a trade-off between the two metrics, where improving one means a loss in the other. To handle the trade-off an alternitive metric can be used known as f1-score. This metric is the weighted harmonic mean of the two metrics and fairly common to use in place.

Another metric that is specific to IE is the slot error rate (SER). This metric is difined as the sum of incorrect and missing slots over the total slots (total number of errors over total in the ground truth). 

### References

Boulton, Freddy. "Conditional Random Field Tutorial in PyTorch." Towards Data Science. May 4, 2018. https://towardsdatascience.com/conditional-random-field-tutorial-in-pytorch-ca0d04499463/.

Huilgol, Purva. "Precision and Recall in Machine Learning." Analytics Vidhya. November 18, 2024. https://www.analyticsvidhya.com/articles/precision-and-recall-in-machine-learning/.

Kejriwal, Mayank, Craig A. Knoblock, and Pedro Szekely. 2021. Knowledge Graphs: Fundamentals, Techniques, and Applications. Cambridge, MA: MIT Press. [ISBN-13: 978-0262045094] Chapter 4 Named Entity Recognition, pages 77–96.

