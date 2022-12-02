---
title: "AToMiC (v0.1) Dataset Released"
date: 2022-12-02T08:00:00-00:00
categories:
  - Annoucements
tags:
  - Dataset
---

AToMiC (v0.1) Dataset is avaliable on [HuggingFace Hub](https://huggingface.co/TREC-AToMiC)

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
