---
title: "AToMiC (v0.1) Dataset Released"
date: 2022-12-02T08:00:00-00:00
categories:
  - Annoucements
tags:
  - Dataset
---

AToMiC (v0.1) Dataset is avaliable on [HuggingFace Hub](https://huggingface.co/TREC-AToMiC)

## Purpose

Multimedia retrieval evaluation and tool developement

## Dataset descriptions

| split      | # Texts   | # Images  | # Qrels   |
|------------|----------:|----------:|----------:|
| Training   | 5,030,748 | 3,723,512 | 5,030,748 |
| Validation | 38,859    | 30,365    | 38,859    |
| Test       | 30,938    | 20,732    | 30,938    |
| Total      | 5,100,545 | 3,774,609 | 5,100,545 |

- Format: Texts (parquet), Images (parquet with embedded images), Qrels (space separated TREC 6-column format)
- Source: Image--Text tuples from [WIT](https://github.com/google-research-datasets/wit) and images from Wikimedia
- Language: English

## Requirements
- [HuggingFace Datasets](https://github.com/huggingface/datasets)


## Code snippets:
```python
from datasets import load_dataset

dataset = load_dataset(
		"TREC-AToMiC/AToMiC-Images-v0.1",
		split='train'
	  )
print(dataset)
```
Other processing usages, see [HuggingFace Datasets usage](https://huggingface.co/docs/datasets/main/en/process)
