---
title: "🆕 TREC 2024 AToMiC Track Guidelines"
permalink: /trec-2024-guidelines/
date: 2024-06-03T08:00:00-00:00
categories:
  - Annoucements
tags:
  - Guidelines
  - TREC 2024
classes: wide
toc: true
---
Hey, look who’s back?
Welcome to the TREC 2024 AToMiC (Authoring Tools for Multimedia Content) track. This page is your go-to for all the essentials: important dates, registration instructions, task details, datasets, submission requirements, and evaluation methods.

## Important Dates (AOE)

- Development Data: June 7th, 2024
- Corpus: June 7th, 2024
- Test Topics: June 14th, 2024
- Submission deadline: August 28th, 2024
- Assessment period: September 2024

## Registration

Organizations eager to join TREC 2024 need to submit a fresh application, even if they've danced this dance before. 
Simply head over to [Evalbase](http://ir.nist.gov/evalbase), create an account and profile, and then register your organization from the main page.
If you have any questions about joining the conference, just drop a line to trec[at]nist.gov.

## Submission Form

Use [Evalbase](https://ir.nist.gov/evalbase/conf/trec-2024) to submit.

## Introduction

AToMiC is on a mission to revolutionize multimedia content creation with cutting-edge multimodal models, seamlessly blending text and images like never before. We aim to transform complex, lengthy documents into visually compelling masterpieces by weaving in graphs, maps, charts, photos, and paintings. By making information more accessible and engaging, we're not just connecting dots; we're connecting people.

Multimedia content creation involves understanding the intricate connections between elements encoded in different modalities. Visual elements such as **photos, graphics, and diagrams** often supplement textual information, serving purposes from **decoration** to **enhancing** or **transforming** the content's meaning. However, finding and adding suitable visual elements can be a time-consuming task. Our goal is to build automatic tools that enrich multimedia content, making information easier and faster to comprehend, ultimately breaking down barriers to accessing information.

Image understanding focuses on detailed descriptions of depicted scenes, entities, their attributes and relations, as well as the events they participate in. Current search engines often index attribute metadata and textual descriptions of images, but these methods frequently fall short. Attribute metadata often miss salient aspects of image content, and while textual descriptions can be precise, they are often scarce. In contexts requiring precise image understanding, search is frequently limited by the availability of text descriptions or the cost of obtaining accurate captions. Our innovative approach aims to overcome these limitations, making multimedia content creation more efficient and effective.

## Datasets

### 2024 Resource

- 🤗 [Development Data (Nightly, subject to change)](https://huggingface.co/datasets/TREC-AToMiC/atomic2023-small_text2image)
- 🤗 [2024 test topics](https://huggingface.co/datasets/TREC-AToMiC/atomic2024/tree/main/query)

### 2023 Resource

- 🤗 Dataset: [Text Collection](https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Texts-v0.2.1)
- 🤗 Dataset: [Image Collection](https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Images-v0.2)
- 🤗 Dataset: [Sparse Judgments](https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Qrels-v0.2)
- [2023 Dev Data](/annoucements/dev-queries/)
- [2023 Test topics](/annoucements/test-queries/)
- [Paper](https://arxiv.org/abs/2304.01961) (accepted to SIGIR23)
- [Repo](https://github.com/TREC-AToMiC/AToMiC)

## Task: *ad hoc* image--text retrieval

TREC 2024 AToMiC Track features **image suggestion task** as the primary task.

### Image Suggestion

> TL;DR: Mixed Modal Text2Image Retrieval Task

Image suggestion is a mixed modal Text2Image retrieval task where the queries are long-form, complex textual inputs, and the images comprise both pixel values and attached captions.
The goal of this task is to find relevant images from a predefined image collection for specific sections of an article. This involves creating high-quality representations of the information presented in images, enabling the appropriate images to be attached to corresponding article sections.

Participants are expected to use the following fields:

- Topics (texts): Utilize the five textual fields—page_title, section_title, hierarchy, context_page_description, and context_section_description. Additional fields such as page_url, media, and category are optional but are encouraged to include descriptions when submitting results.

- Items (images): Use the pixel values in the image field and the corresponding textual descriptions such as caption_reference_description, caption_alt_text_description, and caption_attribution_description. Additional fields like language and image_url are optional but are encouraged to include descriptions when submitting results.

Participants should focus on accurately matching images to article sections.
The grading rubrics will be around

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

Unlike other machine learning competitions, we will not have a public/private leaderboard analogy.
The annotations will be constructed *after* collecting all the submissions.
We will use depth pooling and construct the item pools for the queries.
Items in these pools will then be annotated by NIST assessors with graded relevance judgments.
The final evaluation results will be announced at the TREC workshop.

## Additional Resources

Contributing more resources and suggtsions are welcome.
Leave an issue in our [repo](https://github.com/TREC-AToMiC/AToMiC).

### Prebuilt indexes

The prebuilt indexes are now avaiable on [🤗 datasets](https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Baselines).
You can use the following command to download the prebuilt indexes:

```bash
wget https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Baselines/resolve/main/indexes/ViT-L-14.laion2b_s32b_b82k.image.faiss.flat.tar.gz
wget https://huggingface.co/datasets/TREC-AToMiC/AToMiC-Baselines/resolve/main/indexes/ViT-L-14.laion2b_s32b_b82k.text.faiss.flat.tar.gz
```

## Contact Information

If any question, comments, or suggestions for organizers:

- [Jheng-Hong Yang](mailto:jheng-hong.yang@uwaterloo.ca)
- [AToMiC organizers](mailto:trec-atomic-organizers@googlegroups.com)

Discuss with other participants:

- Mail loop for further annocements: [Google group](https://groups.google.com/g/atomic-participants)
- Chit-chat & quick discussion: [Discord](https://discord.gg/pgDMArnGAH)

## Organizers

- Jheng-Hong Yang, Univeristy of Waterloo
- Carlos Lassance, Cohere
- Mariya Hendriksen, University of Amsterdam
- Thong Nguyen, University of Amsterdam
- Andrew Yates, University of Amsterdam
- Krishna Srinivasan, Google Research
- Miriam Redi, Wikimedia Foundation
- Jimmy Lin, University of Waterloo
