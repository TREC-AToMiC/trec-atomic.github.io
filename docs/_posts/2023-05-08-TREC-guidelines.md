---
title: "TREC 2023 AToMiC Track Guidelines"
permalink: /trec-2023-guidelines/
date: 2023-05-08T08:00:00-00:00
categories:
  - Annoucements
tags:
  - Guidelines
  - TREC 2023
classes: wide
toc: true
---

Welcome to the TREC 2023 AToMiC (Authoring Tools for Multimedia Content) track. 
This page provides essential guidelines about the track, including important dates, registration instructions, tasks, datasets, submission requirements, and evaluation methods.

## Important Dates
- Development topics released: June 2nd, 2023
- Test topics released: ~~June 26th, 2023~~ June 29th, 2023
- Submission deadline: July 24th, 2023
- Assessment period: August 2023


## Registration
To participate in TREC, please register at the TREC [website](https://ir.nist.gov/trecsubmit.open/application.html)


## Introduction
Multimedia content creation involves understanding the connections between elements encoded in different modalities.
Visual elements such as photos, graphics, and diagrams are often used to supplement textual information, serving different purposes such as decoration, complementing, or transforming the meaning of the content. 
However, searching for and adding a suitable visual element to articles can be a time-consuming task. 
Our goal is to build automatic tools that can enrich multimedia content, making information easier and faster to comprehend, and ultimately breaking down the barrier to accessing information.

Image understanding is primarily concerned with concrete descriptions of depicted scenes and entities, their attributes and relations, as well as the events they participate in.
Current search engines often index attribute metadata and textual descriptions of images.
However, attribute metadata often fail to cover the salient aspects of the image content.
While textual descriptions often provide precise information, they are frequently scarce in terms of availability. 
In contexts that require a precise understanding of images, search is frequently limited by the availability of text descriptions or the cost of obtaining accurate image captions.


## Datasets
- 🤗 Dataset: [Text Collection](https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Texts-v0.2.1)
- 🤗 Dataset: [Image Collection](https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Images-v0.2)
- 🤗 Dataset: [Sparse Judgments](https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Qrels-v0.2)
- Looking for more information?
  - Check our [paper](https://arxiv.org/abs/2304.01961) (accepted to SIGIR23)
  - Check our repo: [AToMiC](https://github.com/TREC-AToMiC/AToMiC)
- Development topics/qrels: check our latest [post](/annoucements/dev-queries/)


## Tasks: *ad hoc* retrieval
TREC 2023 AToMiC Track features an image suggestion task as the primary task, while keeping image promotion as the secondary task.


### Task 1: Image Suggestion (Primary)
The goal of this task is to find relevant images from a predefined [image collection](https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Images-v0.2), given a specific section of an article.
The task involves creating high-quality representations of information presented in images, so that appropriate images can be attached to the corresponding article sections.

The participants are expected to use the following fields:
- Topics (texts): the five textual fields `page_title`, `section_title`, `hierachy`, `context_page_description`, `context_section_description`. 
Other fields such as `page_url`, `media` and `category` are free to use, but we encourage participants provide descriptions when submitting their results.
- Items (images): the pixel values in the `image` field and the corresponding textual descriptions such as `caption_reference_description`, `caption_alt_text_description`, `caption_attribution_description`.
Other fields such as `language` and `image_url` are free to use, but we encourage participants to provide descriptions when submitting their results.


### Task 2: Image Promotion (Secondary)
This task is the inverse of the image suggestion task. 
Given a specific image represented by its pixel values, the goal is to identify a section of an article where the image can be appropriately attached.
The participants are expected to retrieve relevant items from a predefined [text collection](https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Texts-v0.2.1).
The objective is to prevent attaching the image to an irrelevant article, which could introduce noise when comprehending multimedia articles. 
Although not the primary focus of this track, models built for this purpose could support authoring tools for crafting precise captions in multimedia content.

The participants are expected to use the following fields:
- Topics (images): the pixel values in the `image` field and the corresponding textual descriptions such as `caption_reference_description`, `caption_alt_text_description`, `caption_attribution_description`.
Other fields such as `language` and `image_url` are free to use, but we encourage participants to provide descriptions when submitting their results.

- Items (texts): the five textual fields `page_title`, `section_title`, `hierachy`, `context_page_description`, `context_section_description`. 
Other fields such as `page_url`, `media` and `category` are free to use, but we encourage participants provide descriptions when submitting their results.

**Note**:
The evaluation of this task will use the annotations collected from the image suggestion task. 
The assumption is that the two tasks are correlated, and the annotations could be transferred to this task.


## Submission
Submissions for the ad-hoc retrieval task should be in standard TREC 6-column format. 
The six columns are `TopicID`, `Q0`, `ItemID`, `Rank`, `Score`, and `RunID` separated by spaces. 
A submission should include at least one result for every topic in the test set. 
Participants may submit up to **5** runs, each a separate 6-column file consisting of ranked results for all topics in the test set. 
Participants are asked to return a ranked list of at most **1,000** items for each topic.

The six column format: 
```bash
TopicID Q0 ItemID Rank Score RunID
```
- `TopicID` contains the unique topic (query) identifiers. A submission should include at least one result for every topic in the test set.
- `Q0` contains a static string "Q0". It's a placeholder that we're not using.
- `ItemId` contains the unique item identifiers for the retrieved candidates.
- `Rank` is the rank at which the candidate is retrieved.
- `Score` shows the score (interger or floating point) corresponding to the `TopicID` and `ItemID` pair. This score **must be in descending order**.
- `RunID` is the tag for your submission run.

Example submission:
```bash
topic_1 Q0 item_1 1 2.73 runid1
topic_1 Q0 item_5 2 2.71 runid1
topic_1 Q0 item_9 3 2.61 runid1
topic_2 Q0 item_9 1 7.15 runid1
topic_2 Q0 item_15 2 0.89 runid1
```


### Submission Types
There are two types of submissions:

1. **Automatic**:
The main type of submission, where there is **no manual intervention** in running the test topics. 
The ideal case is that you only look at the test topics to check that they ran properly (i.e., no bugs), and then you submit your automatic runs.
You should not adjust your runs, rewrite the query, retrain your model, or make any other sorts of manual adjustments after you see the test topics.

2. **Manual**:
If you want to have a human in the loop for your run or do anything else that uses the test topics to adjust your model or ranking, you can mark your run as manual. 
Manual runs are still welcome, but these are distinct from our main scenario, which is a system that responds to unseen topics automatically.


## Evaluation
Unlike other machine learning competitions, the TREC 2023 AToMiC Track will not have a public/private leaderboard analogy. 
The annotations will be constructed *after* collecting all the submissions. 
We will use depth pooling and construct the item pools for the queries. 
Items in these pools will then be annotated by NIST assessors with graded relevance judgments.
The final evaluation results will be announced at the TREC 2023 workshop.

In addition to the [sparse judgments](https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Qrels-v0.2), a set of development topics with judgments will be released for early evaluation before submitting the test runs. 
However, these judgments are not guaranteed to be similar to the final assessments by NIST annotators.


## Additional Resources
Contributing more resources and suggtsions are welcome.

### Prebuilt indexes
The prebuilt indexes are now avaiable on [🤗 datasets](https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Baselines).
You can use the following command to download the prebuilt indexes:
```bash
wget https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Baselines/resolve/main/indexes/ViT-L-14.laion2b_s32b_b82k.image.faiss.flat.tar.gz
wget https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Baselines/resolve/main/indexes/ViT-L-14.laion2b_s32b_b82k.text.faiss.flat.tar.gz
``` 


## Contact Information
If any question, comments, or suggestions for organizers:
- Email [Jheng-Hong Yang](mailto:jheng-hong.yang@uwaterloo.ca) or [AToMiC organizers](mailto:trec-atomic-organizers@googlegroups.com)

Discuss with other participants:
- Mail loop for further annocements: [Google group](https://groups.google.com/g/atomic-participants)
- Chit-chat & quick discussion: [Discord](https://discord.gg/pgDMArnGAH)


## Organizers
- Jheng-Hong Yang, Univeristy of Waterloo
- Carlos Lassance, Naver Labs Europe
- Rafael S. Rezende, Naver Labs Europe
- Krishna Srinivasan, Google Research
- Miriam Redi, Wikimedia Foundation
- Stéphane Clinchant, Naver Labs Europe
- Jimmy Lin, University of Waterloo

Thank you for your interest in the TREC 2023 AToMiC Track. We look forward to your participation.
