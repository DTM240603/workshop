---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Amazon OpenSearch Service: Improving Order History Search with Semantic Search

**Author:** Pham Anh Hao &emsp; | &emsp; **Team:** ITSoldier

A practical technical breakdown of how the Amazon team improved the purchase history feature — a system managing billions of orders dating back to 1995. To power virtual assistants like Rufus and Alexa in handling natural-language questions such as *"Find the healthy drinks I bought last year,"* Amazon upgraded the system with Semantic Search built on Amazon OpenSearch Service and Amazon SageMaker.

### Limitations of the Old System

The old system relied on keyword matching (Lexical Matching – BM25).

* **Problem:** It only worked well when the exact product name was entered. Searching for a general phrase like "healthy drinks" would miss "kombucha" or "green tea" because their titles don't contain that keyword.
* **Solution:** Semantic Search is needed to understand the actual meaning and intent behind a user's query.

### Challenges

* **Massive scale:** Processing and vector-searching across billions of accumulated records.
* **Zero Downtime:** Ensuring the system stays 100% available throughout the upgrade.
* **Search quality:** Avoiding diluted results when users search for something exact (e.g., "iPhone 15") and handling non-semantic identifiers like Order IDs (which still rely on Lexical Search).

### The Solution

To solve this, Amazon split the solution into two main parts:

#### 1. Improving resilience with a Cell-Based Architecture

* The system is broken into independent clusters called **cells**, each serving a separate slice of customers.
* Request routing is handled flexibly using a cache or Amazon DynamoDB.
* If a cell fails, the system only loses capacity proportional to that cell (the **blast radius** is contained within it) instead of the whole system going down. Data is also replicated across cells to prevent loss.

#### 2. Implementing Semantic Search

* Used the **LLM-as-a-judge** approach with Anthropic's Claude on Amazon Bedrock to score candidate models based on NDCG, MRR, Precision, and Recall metrics.
* Packaged and deployed models via **Amazon SageMaker Inference Endpoints** combined with Amazon Elastic Container Registry.
* Used the `knn_vector` field in OpenSearch. Since each customer's order count is bounded, the system runs an exact k-NN algorithm directly on the server via Scripted Scoring to optimize for both accuracy and speed.
* The system runs Lexical Search and Semantic Search in parallel: results from both streams are merged, scores normalized, and returned to the user. If a user searches by an identifier (like an Order ID), the system automatically skips Semantic Search. If the vector pipeline fails, the system automatically falls back to traditional Lexical Search, ensuring customers always get results.

#### Backfilling Historical Data

To make Semantic Search effective for older orders, Amazon built a large-scale data processing pipeline using **AWS Step Functions** for orchestration and **AWS Lambda** for execution, generating embedding vectors for billions of historical records without impacting the performance of the live system.

### Business Impact

* Smarter search (e.g., searching "sustainable eating utensils" returns "wooden spoon" even without a matching keyword).
* 10% increase in Query Recall and a 20% increase in search success rate.
* 48% expansion in Result Coverage, helping Rufus and Alexa perform more effectively.

### Key Takeaways

From this article, I learned that improving search isn't just about applying new technology. Infrastructure resilience and maintaining the stability of the existing system are just as critical to ensuring an uninterrupted user experience.

Semantic Search and Hybrid Search are valuable approaches that let Amazon OpenSearch Service deliver a smarter search experience based on the customer's actual intent, rather than relying solely on basic keyword matching as before.

**Original article:** [aws.amazon.com/vi/blogs/big-data/improving-order-history-search...](https://aws.amazon.com/vi/blogs/big-data/improving-order-history-search-using-semantic-search-with-amazon-opensearch-service/)

**Posted link on AWS Study Group VN:** [facebook.com/groups/awsstudygroupfcj/permalink/2177864399645187](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2177864399645187/)

![Cell-Based Architecture and Semantic Search on Amazon OpenSearch Service](/images/3-BlogsPosted/3.2-Blog2/1.jpg)

![Architecture combining Lexical Search and Semantic Search](/images/3-BlogsPosted/3.2-Blog2/2.jpg)

![Embedding vector backfill pipeline with AWS Step Functions and Lambda](/images/3-BlogsPosted/3.2-Blog2/3.jpg)

![Improved Query Recall and Result Coverage results](/images/3-BlogsPosted/3.2-Blog2/4.jpg)
