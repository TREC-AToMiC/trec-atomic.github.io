---
permalink: /quick-start-guide/
title: "Quick Start Guide"
---

## Ad-hoc Retrieval
Given an arbitrary query, retrieve tok-$$k$$ relevant document from the collection.
For the image suggestion task, the query is a text, where the document is an image.
(For the image promotion task, the query is an image, where the document is a text.)
See [about](/about) for more details of these two tasks.

- A text is composed of textual information, e.g., title and context decriptions.
- An image is composed of its visual information (pixel values) and metadata (reference, alt-text, and attribution captions).

## Submission Format

Submissions for the ad hoc retrieval task should be in standard TREC 6-column format.

```bash
Query_ID Q0 DOC_ID RANK SCORE RUN_ID
```
- Query\_ID (DOC\_ID): the unique identifier for each text (or image)
- Q0: placeholder
- RANK: the rank of the retrieved DOC\_ID (for Query\_ID)
- SCORE: the score of the retrieved DOC\_ID (for Query\_ID)
- RUN\_ID: systems's identifier

Example (Text-to-Image) Run:
```bash
wit-test-topic-000000001 Q0 ba65386c-63de-3471-8473-985f6a102607 1 69.9 boring_system
wit-test-topic-000000001 Q0 4c8c424a-149d-342d-820e-6e5de6df6008 2 65.3 boring_system
...
wit-test-topic-000000001 Q0 a26a103e-bc5c-3f25-b620-60af7ace8257 1000 1.4 boring_system
wit-test-topic-000000002 Q0 4c8c424a-149d-342d-820e-6e5de6df6008 1 71.5 boring_system
...
```

Participants are asked to return a ranked list of at most $$k=1,000$$ documents for each query.

## Evaluation
- Tool: [trec\_eval](https://github.com/usnistgov/trec_eval)

Example Usage (MRR@10, Recall@1000, success@1000):
```bash
trec_eval -c -M 10 -m recip_rank <path-to-qrels> <path-to-runfile>
trec_eval -c -m recall.1000 success.1000 <path-to-qrels> <path-to-runfile>
```

## Development Dataset
- [AToMiC-v0.1](/annoucements/huggingface-hub-released)
