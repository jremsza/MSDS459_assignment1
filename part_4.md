# Part 4: Natural Language Processing in Action - Chapter 10

The focus of chapter 10 is about large language models (LLMs) and how they work that spands from ethics and usage to custom user applications.

### Ethics and Control in LLM Usage

Popular LLM chatbots appear to be intelligent as they demonstrate their abilities with carrying out complex instructions to user inputs such as composing essays, code or even lines of argument for debates. However, these models have been trained on billions of parameters of data for lengthy periods of time. What is actually occurring is the machines are identifying word sequences it has seen before and repeating back a pattern of mashed up words that look like reasonable answers to questions that have been posed online. However intelligent these models seem to be, they often give false information that are known as "hallucinations". In a blog post on vellum.ai, author Anita Kirkovska outlines the four types of LLM hallucinations as input-conflicting, context-conflicting, fact-conflicting, and forced. The first, input-conflicting, is a hallucination in which the generated content deviates from the input often due to misunderstanding the users intent. Context-conflicting arises when the model generates content that conflicts with previously generated information, usually as a result of lengthy conversations in which the model loses track. Fact-conflicting is a hallucination in which the model is just factually incorrect. Lastly, forced hallucinations can happen in a situations when external users try to break the system prompt configuration of your deployed prompt by using jail-break techniques (Kirkovska 2024).

Given the numerous applications of LLMs it is often necessary to control for reasoning errors and potential toxicity. This can be accomplished with scaling, guardrails, retrieval and grounding. Scaling is meant to make the model bigger and in turn fix reasoning errors. Guardrails are placed to monitor output to prevent it from saying harmful things. Retrieval is a way to augment with a search engine to retrieve text used to generate responses, while grounding is augmenting with real time facts. Interestingly, it was found that model scaling in non-linear. Increasing the size of an LLM does not increase the accuracy of the LLM on benchmark tasks by any measurable amount. Changing to a different model architecture is necessary of your language model if you ever want to achieve superior results.

Under the hood LLMs operate on as a probability distribution function. During the training process the input text allows the model to learn how often each word occurs based on the words that preceded it. The training process compresses these statistics into a function that generalizes from these word-occurrence patterns, so it can fill in the blanks for new prompts and input text.

### Customization and Fine-Tuning of LLMs

Customizing and fine-tuning LLMs involves semantic routing, leveraging semantic search to direct user prompts to the most suitable LLM based on a trained model using successful prompt data. This enhances search results and efficiency. However, relying solely on LLMs for routing can be unreliable, leading to the complex field of prompt engineering to navigate each LLM's unique guardrails and quirks. Semantic chain-of-thought reasoning automates some prompt engineering for code generation. To prevent LLMs from producing toxic or erroneous outputs—like biases, violence, or privacy breaches—NLP filters and classifiers are essential. These require training with examples of good and bad text, a process as challenging as detecting human-generated toxic content, necessitating traditional machine learning approaches. 

To filter chatbot outputs effectively, a binary classifier is needed to distinguish between allowed and disallowed responses. A multi-label classifier (tagger) is even more effective, as it can identify a wider range of toxic responses, such as biases, violence, or privacy violations. Instead of exhaustively describing potential issues in prompts, collecting examples of undesirable behavior into a training set is more practical. Post-deployment, new examples of toxicity or chatbot errors can be added to the training set, enabling continuous improvement. Each time new toxic examples are identified and filters are retrained, confidence in the chatbot’s guardrails strengthens, enhancing its reliability and safety.

Below is a list of open source tools to use to help with general filter rules, using languages similar to regular expressions:

- SpaCy’s Matcher class
- Regular expressions for language models (ReLM) patterns
- EleutherAI’s LM Evaluation Harness package
- NeMo Guardrails’s Colang language

The text walks through an example of RAG using GPT-2. Using Retrieval-Augmented Generation (RAG) with GPT-2 involves fine-tuning the model on custom datasets to generate contextually relevant text by integrating retrieved external information with its language capabilities (in the text example they use the book chapter to train with). Training GPT-2 with your own data adjusts its weights to better suit specific domains, enhancing its ability to produce tailored responses. However, GPT-2’s default greedy search generation, which selects the most probable token at each step, can lead to repetitive outputs, as it prioritizes immediate choices without long-term planning. For example, selecting a word like "data" may increase its likelihood in subsequent steps, causing loops. To address this, techniques like repetition penalties and temperature adjustments are used. Increasing the temperature above 1.0 reduces greediness, fostering creativity, while penalties help break repetitive cycles, ensuring more coherent and diverse outputs when combined with custom-trained, retrieval-augmented approaches. 

### Application of LLMs in Knowledge Retrieval

A QA pipeline for RAG requires: a model to create text embeddings, an Approximate Nearest Neighbors (ANN) library for indexing documents and retrieving ranked matches, and a model to extract or generate answers from relevant documents. Frameworks like Jina, Haystack, txtai, and LlamaIndex simplify building, evaluating, and scaling such pipelines. LlamaIndex offers plugins for databases, vector stores, and LLMs, while Haystack combines LLMs, guardrails, and vector search to create robust QA RAG systems, ensuring accurate and safe responses in custom-trained, retrieval-augmented applications.

To expand on the textbooks customized QA bot I found an aritcle to build a RAG from scratch. The author walked through the process. Implementing RAG from scratch, was done with GPT-3.5, and involved processing document directories, chunking texts into manageable sizes, generating embeddings, and indexing them for retrieval using cosine similarity. This retrieved context is fed into the LLM to generate improved responses, and tailored to the input data. Building without high-level libraries like LlamaIndex or LangChain provides deeper insight into RAG’s underlying mechanisms, ensuring precise control over the workflow for customized, accurate, and efficient query responses in domain-specific applications (Syeda 2024).

### References


Kirkovska, Anita. 2024. "Four LLM Hallucinations and Ways to Fix Them: What Is LLM Hallucination & the Four Most Common Hallucination Types and the Causes for Them." Vellum.ai. January 1, 2024. https://www.vellum.ai/blog/llm-hallucination-types-with-examples.

Lane, Hobson, and Maria Dyshel. 2025. Natural Language Processing in Action. 2nd ed., 410–469. Shelter Island, NY: Manning Publications.

Syeda, Mahnoor. "Building Retrieval Augmented Generation (RAG) From Scratch." Medium, July 30, 2024. https://medium.com/red-buffer/building-retrieval-augmented-generation-rag-from-scratch-74c1cd7ae2c0.
