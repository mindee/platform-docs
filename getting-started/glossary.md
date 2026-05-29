---
description: A glossary of common Mindee terminology.
icon: book
---

# Glossary

You will frequently encounter these concepts throughout this documentation as Mindee is centered around them.

### Annotation

The values (labels) a human enters to train, test, or alter an [ML](glossary.md#ml-machine-learning) processing pipeline.

Mindee uses annotations notably for the RAG feature.

### API (Application Programming Interface)

A set of protocols and rules to define how applications or devices can connect to and communicate with each other.

In the context of Mindee, the API defines how to send files and receive results.

### Catalog

A list of [model](glossary.md#model) templates you can search and use to create your own models.

### Custom Model

A [model](glossary.md#model) you create from scratch for your own [document](glossary.md#document) type and use case.

### Data Schema

A set of [fields](glossary.md#field) and their [guidelines](glossary.md#guideline) for data extraction. Associated to a [model](glossary.md#model).

### Document

A structured or semi-structured written or graphical representation of human thought, such as an invoice, receipt, ID card, W9 form, contract, train ticket, etc.

Mindee processes documents contained in various [file](glossary.md#file) formats.

### Extraction Model

A type of Mindee model designed to extract structured data from a [document](glossary.md#document).

Includes a [Data Schema](glossary.md#data-schema) and any optional features.

### Field

A single data point to extract from a document. Part of a [Data Schema](glossary.md#data-schema).

### File

A computer file. In the context of Mindee, a file may contain one or several [documents](glossary.md#document).

### Guideline

A set of instructions provided by the user, to clarify or alter the behavior of a [ML model](glossary.md#ml-machine-learning).

### Inference

The processing step where a [ML model](glossary.md#ml-machine-learning) performs an operation on a [file](glossary.md#file).

By extension, this also refers to response or results that our API returns for a given file.

### Job

The asynchronous processing task created when a file or URL is sent to the Mindee [API](glossary.md#api-application-programming-interface) for processing.

### ML (Machine Learning)

Algorithms that learn and generalize from data, and can perform tasks without explicit programming instructions.

This is the backbone of Mindee's technology.

### Model

A set of instructions for processing [files](glossary.md#file). There are several types of Mindee models that correspond to different uses.

A model can operate on a single document or multiple documents within the same file.

### Multimodal Model

A type of deep-learning model that processes multiple types of data, such as text and vision.

Mindee uses multimodal models when processing documents.

### OCR

Optical Character Recognition (OCR) is the process by which a machine reads text on printed documents and transcribes them into a machine-readable format, like a `.txt` file.

### OpenAPI

An industry specification that defines a language-agnostic interface for RESTful APIs.

### Payload

A payload refers to data that is submitted to the Mindee server and the data returned by the server when an API request is made.

### Polling

A result retrieval flow where your application repeatedly checks the processing status of a [job](glossary.md#job).

### Mindee

Pronounced "mind - ee", because we are like a helpful **mind** to you!

### SDK (Software Development Kit)

A set of software development tools developers can use to facilitate the creation of applications.

### Utility Model

A [model](glossary.md#model) used to preprocess or analyze documents, such as Split, Crop, Classification, or raw OCR.

### Webhook

A result retrieval flow where Mindee sends the processing result directly to your Web server.
