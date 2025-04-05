## Part 4: Natural Language Processing in Action - Chapter 10

The focus of chapter 10 is about large language models (LLMs) and how they work that spands from ethics and usage to custom user applications.

- **Ethics and Control in LLM Usage**

Popular LLM chatbots appear to be intelligent as they demonstrate their abilities with carrying out complex instructions to user imputs such as composing essays, code or even lines of argument for debates. However, these models have been trained on billions of parameters of data for lengthy periods of time. What is actually occuring is the machines are identifying word sequences it has seen before and repeating back a pattern of mashed up words that look like reasonable answers to questions that have been posed online. However intelligent these models seem to be, they often give false information that are known as "hallucinations". In a blog post on vellum.ai, author Anita Kirkovska outlines the four types of LLM hallucinations as input-conflicting, context-conflicting, fact-conflicting, and forced. The first, input-conflicting, is a hallucination in which the generated content deviates from the input often due to misunderstanding the users intent. Context-conflicting arises when the model generates content that conflicts with previously generated information, usually as a result of lengthy conversations in which the model loses track. Fact-conflicting is a hallucination in which the model is just factually incorrect. Lastly, forced can happen in a situations when external users try to break the system prompt configuration of your deployed prompt by using jail-break techniques (Kirkovska 2024).

Given the numerous applications of LLMs it is often nessecary to control for reasoning errors and potential toxicity. This can be accomplished with scaling, guardrails, retrival and grounding. Scaling is meant to make the model bigger and in turn fix reasoning errors. Guardrails are placed to monitor output to prevent from saying harmful things. Retrival is a way to augment with a serach engine to retrive text used to generate responses, while grounding is augmenting with real time facts.

- **Customization and Fine-Tuning of LLMs**

- **Application of LLMs in Knowledge Retrieval**

### References

Kirkovska, Anita. 2024. "Four LLM Hallucinations and Ways to Fix Them: What Is LLM Hallucination & the Four Most Common Hallucination Types and the Causes for Them." Vellum.ai. January 1, 2024. https://www.vellum.ai/blog/llm-hallucination-types-with-examples.
