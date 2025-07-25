---
icon: layer-group
---

# Continuous Learning (RAG)

When using an Extraction Model regularly, it can happen that the extraction is not satisfying on a given document or particular template.

If you notice this, you have a way to improve durably the performance of the model for the next predictions you'll make. The solution you need is the RAG feature.

## What is RAG?&#x20;

RAG stands for Retrieval-Augmented Generation, a novel approach in artificial intelligence that combines the strengths of retrieval-based models with generative LLM text production.

Essentially, RAG leverages a rich database of source documents and embeddings to augment the knowledge base from which it draws responses. This means that the system retrieves specific and context-based data snippets and then uses them to generate semantic and fine-tuned responses that are both creative and factually accurate.

## How does RAG work?&#x20;

To make the RAG system effective, there are 3 main steps to have in mind.&#x20;

1. Annotating a given sample, which means giving the model the difference between the extracted data and the expected value(s). When activated, this example will be added to the RAG Database for the future.
2. Retrieval: When a next document will be send with the RAG option activated, the model will try to search for a similar example in the existing database. The question here is : "Maybe there is an existing example where I need to follow the instructions so that I'm not doing a same mistake again".  If no example found, no need to augment the prediction. If an examples is matched in the RAG Database, here comes step 3.&#x20;
3. Augmented Generation: A document was matched in the RAG Database. The model will use the instructions you gave on the RAG sample to make a better prediction this time. The prediction generated is augmented with an existing context helping the model to be better this time.

## How do I set up RAG with Mindee?&#x20;

To use RAG on a given Extraction Model, you should click on the RAG tab. \
\
This tab allows you to enrich your RAG Database by uploading a document with an unsatisfying behavior. You need to annotate the document, ticking the fields you want to be covered by the RAG augmentation on this template, and having the possibility to give additional guidelines using natural language.&#x20;

Once this document is annotated, be sure to activate it, and go to the Live test tab. \
\
You should click on RAG Activated, and upload a document. Ideally, pick a document with the same template (another invoice from the same supplier for instance), but not exactly the one you used in the RAG database. You will see the before/after predictions and should be able to check that the extra instructions were taken into account to augment properly the prediction.\
\
In the future, the documents respecting the same template should be augmented, which should increase a lot the performances on this given template. For other types of documents, the behavior remain the same, which means that RAG is improving the result with no regression on other documents.&#x20;

## Is my data shared with other users?&#x20;

A unique RAG, and thus a unique RAG Database is linked to a unique Model.

It means the only people who will have access to your RAG data are the users of the organization the model is associated with.

## How do I benefit from RAG when processing my documents?

When enqueuing a file, simply add `rag=true`&#x20;
