---
title: 'Summary of prompt engineering'
date: 2024-01-11
category: ML
tags:
  - generative ai
  - prompt engineering
---

the original article is here. [link](https://towardsdatascience.com/how-i-won-singapores-gpt-4-prompt-engineering-competition-34c195a93d41)

The author shared her tips acquired during the Singapore's ChatCPT competition. 

## Structuring Prompts using the CO-STAR framework

- `context`, `objective`, `style`, `tone`, `audience`, `response`
- Style: particular famous person's style of writing, a particular expert in a profession (CEO)
- Tone: formal, humorous, empathetic
- Response: a list, a JSON, a professional report

```
# CONTEXT #
I want to advertise my company’s new product. My company’s name is Alpha and the product is called Beta, which is a new ultra-fast hairdryer.

# OBJECTIVE #
Create a Facebook post for me, which aims to get people to click on the product link to purchase it.

# STYLE #
Follow the writing style of successful companies that advertise similar products, such as Dyson.

# TONE #
Persuasive

# AUDIENCE #
My company’s audience profile on Facebook is typically the older generation. Tailor your post to target what this audience typically looks out for in hair products.

# RESPONSE #
The Facebook post, kept concise yet impactful.
```

## Sectioning Prompts using delimiters

Delimiters are special tokens that help the LLM distinguish which parts of your prompt it should consider as a single unit of meaning. Example: ###, ===, >>>
Or use them as XML tags. 

## Creating system prompts with LLM guardrails

"system prompts" = "system messages" = "custom instructions" -> provide instructions that you want the LLM to remember when responding throughout the entire chat

- task definition - e.g. You will answer questions using this text: [insert text].
- output format - e.g. You will respond with a JSON object in this format: {“Question”: “Answer”}.
- guardrails (Hallucination) - e.g. If the text does not contain sufficient information to answer the question, do not make up information and give the answer as “NA”.
- guardrails (Scope) - e.g. You are only allowed to answer questions related to [insert scope]. Never answer any questions related to demographic information such as age, gender, and religion.

## Analyzing datasets using only LLMs, without plugins or code

- Not good at: 1) descriptive statistics 2) correlation analysis 3) statistical analysis 4) machine learning
- Great at: 1) anomaly detection 2) clustering 3) cross-column relationshipt 4) textual analysis 5) trend analysis 

1. Breaking down a complex task into simple steps
2. Referencing intermediate outputs from each step
3. Formatting the LLM’s response
4. Separating the instructions from the dataset

```
System Prompt:
I want you to act as a data scientist to analyze datasets. Do not make up information that is not in the dataset. For each analysis I ask for, provide me with the exact and definitive answer and do not provide me with code or instructions to do the analysis on other platforms.

Prompt:
# CONTEXT #
I sell wine. I have a dataset of information on my customers: [year of birth, marital status, income, number of children, days since last purchase, amount spent].

#############

# OBJECTIVE #
I want you use the dataset to cluster my customers into groups and then give me ideas on how to target my marketing efforts towards each group. Use this step-by-step process and do not use code:

1. CLUSTERS: Use the columns of the dataset to cluster the rows of the dataset, such that customers within the same cluster have similar column values while customers in different clusters have distinctly different column values. Ensure that each row only belongs to 1 cluster.

For each cluster found,
2. CLUSTER_INFORMATION: Describe the cluster in terms of the dataset columns.
3. CLUSTER_NAME: Interpret [CLUSTER_INFORMATION] to obtain a short name for the customer group in this cluster.
4. MARKETING_IDEAS: Generate ideas to market my product to this customer group.
5. RATIONALE: Explain why [MARKETING_IDEAS] is relevant and effective for this customer group.

#############

# STYLE #
Business analytics report

#############

# TONE #
Professional, technical

#############

# AUDIENCE #
My business partners. Convince them that your marketing strategy is well thought-out and fully backed by data.

#############

# RESPONSE: MARKDOWN REPORT #
<For each cluster in [CLUSTERS]>
— Customer Group: [CLUSTER_NAME]
— Profile: [CLUSTER_INFORMATION]
— Marketing Ideas: [MARKETING_IDEAS]
— Rationale: [RATIONALE]

<Annex>
Give a table of the list of row numbers belonging to each cluster, in order to back up your analysis. Use these table headers: [[CLUSTER_NAME], List of Rows].

#############

# START ANALYSIS #
If you understand, ask me for my dataset.
```

### why separate the instructions from the dataset?

context window size - prevent forgetting