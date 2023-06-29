---
title: "TREC 2023 AToMiC - Test queries"
date: 2023-06-29T08:00:00-00:00
categories:
  - Annoucements
tags:
  - Development queries
  - TREC 2023
classes: wide
toc: true
---

We are pleased to announce the release of the **test** topics for the TREC-AToMiC task. 
These topics have been carefully selected from the AToMiC text collection, and we invite participants to submit their runfiles based on these test topics.


## Topic Selection
In order to ensure a diverse range of topics, we employed two primary criteria for topic selection:
- Unillustrated sections in enwiki: 
  We identified sections within the English Wikipedia (enwiki) that do not have accompanying images but potentially have matching images in other Wikipedia pages from foreign languages.

- Vital articles at level 3:
  We referred to [Wikipedia:Vital_articles](https://en.wikipedia.org/wiki/Wikipedia:Vital_articles) and selected articles classified as level 3 vital articles. These articles serve as quality control monitors for Wikipedia.

Additionally, we considered the following sub-criteria:
- Article Quality: 
  We sampled 100 topics from C-class articles, 50 topics from B-class articles, and 50 topics from Featured or Good Articles.
- AToMiC Text Collection Coverage: 
  The coverage of the AToMiC text collection for the test topics is as follows: 180 topics belong to the *other* set with no sparse labels at all, 19 topics are from the *training* set, and 1 topic represents the *test* set.

We believe that this selection process ensures a diverse and representative set of topics for the TREC-AToMiC task. 
We look forward to receiving your runfiles based on these test topics.
Please don't hesitate to reach out if you have any questions or need further clarification.

Thank you for your participation!


## Download Links
The dataset is avaliable on HuggingFace 🤗:
* [Query dataset](https://huggingface.co/datasets/TREC-AToMiC/TREC-2023-Text-to-Image)
* Query embeddings (TBA)
* Baseline runfiles (TBA)