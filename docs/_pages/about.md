---
permalink: /about/
title: "What is AToMiC?"
---

**A**uthoring **To**ols for **M**ult**i**media **C**ontent (AToMiC) Track at the Text Reterieval Conference [(TREC)](https://trec.nist.gov/) is intended to encourage research in multimedia search systems.
We aim to provide evaluation resources and toolkits for researchers from information retrieval, natural language
processing, computer vision, and multimedia communities.


# Tasks

The TREC 2023 AToMiC track is organised with two tasks of the standard *ad hoc* retrieval setup.
We assume the existence of a corpus $$\mathcal{C}$$ comprised of a collection of documents $$\{d_1, d_2 \ldots d_n\}$$.
In response to a user’s information need represented as query $$q$$.
The system’s goal is to return a top-$$k$$ ranked list of documents that maximizes some metric of quality such as nDCG or MRR.

For TREC 2023, we provide two different collections: a collection of texts $$\mathcal{C}_{T} = \{t_1, t_2 \ldots t_n\}$$ ($$t$$ stands for text) and a collection of images $$\mathcal{C}_{M} = \{m_1, m_2 \ldots m_n\}$$ ($$m$$ stands for media).

### Image Suggestion
An information need (for convenience, a *query*, denoted $$q$$, is simply a text $$t$$ drawn from $$\mathcal{C}_T$$, i.e., $$q \in \mathcal{C}_T$$.
That is, an editor of Wikipedia examines a *specific section* of an article and wishes to locate an appropriate image in the collection $$\mathcal{C}_{M}$$.

![Image Suggestion Task](/assets/images/20221118_TREC_AToMiC_intro.012.png){: .align-center}
<figcaption>An article editor seeks to find an appropriate image for the section, World Trade Center Collapse Investigation, of a Wikipedia article about the National Institute of Standards and Technology (NIST).</figcaption>

### Image Promotion
This task is the inverse of the image suggestion task.
The query $q$ is an image drawn from $$\mathcal{C}_{M}$$ and the collection to be searched is $$\mathcal{C}_{T}$$.

![Image Promotion Task](/assets/images/20221118_TREC_AToMiC_intro.021.png){: .align-center}
<figcaption>An image provider seeks to find relevant articles or contexts given the query image.</figcaption>
