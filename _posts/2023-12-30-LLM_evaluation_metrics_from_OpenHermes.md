---
title: 'Large Language Model Evaluation Metrics'
date: 2023-12-30
tags:
  - ml
  - paper
  - llm
---

Large language models are evaluated using various metrics to measure their performance. Some of the most common evaluation metrics include:

- Perplexity
- BLEU (Bilingual Evaluation Understudy)
- ROUGE (Recall-Oriented Understudy for Gisting Evaluation)
- BERTScore
- COMET (Concept-oriented Metric for Evaluating Translation)
- METEOR (Metric for Evaluation of Translation with Opinion from Reference)
- BLEURT (Bilingual Evaluation Understanding with Response Time)
- GPTScore
- PRISM (Predicate-Resource Inference and Sentiment Measurement)
- BARTScore (Bidirectional and Autoregressive Transformer Score)
- G-Eval
- Human Evaluation

## Metric Descriptions:

### Perplexity
Perplexity measures how well a model can predict the next word in a sequence. A lower score indicates better performance, while a higher score means the model performs poorly at coming up with the next word.

### ROUGE
ROUGE (Recall-Oriented Understudy for Gisting Evaluation) measures a translated or summarized text's quality by calculating recall based on n-gram matching between the generated text and a reference corpus.

### BLEU
BLEU (Bilingual Evaluation Understudy) is used to evaluate the quality of machine-translated text. The score is better if the language model's output is closer to the output of a human. A brevity penalty is introduced in the BLEU formula because it tends to give higher scores to shorter predictions.

### BERTScore
BERTScore is a pre-trained BERT-based method used for evaluating summaries and translations. In addition to providing a score, BERTScore also computes precision, recall, and F1 measure metrics. The metric has been tested on image captioning as well.

### COMET
COMET uses pre-trained language models to generate scores for candidate sentences, making it possible for the metric to depend solely on n-grams. It is a set of models that can be used for machine translation, and custom models can be trained.

### METEOR
METEOR is a metric that requires training and relies on token alignment. It evaluates machine-translated text from the reference text by unigram matching the human text. The matching is done based on unigram-precision and unigram-recall.

### BLEURT
BLEURT (Bilingual Evaluation Understanding with Response Time) is a metric that evaluates the response time of machine translation models. It is trained on human annotations of translation quality and fluency.

### GPTScore
GPTScore uses generative pre-trained models to score the generated text. The evaluation framework for GPTScore is shown in the following