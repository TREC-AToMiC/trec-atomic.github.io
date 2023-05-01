---
title: "AToMiC Text Collection Update"
date: 2023-05-01T08:00:00-00:00
categories:
  - Annoucements
tags:
  - Dataset
---

- Text collection update: We have addressed the missing entity issues in our text collection and have released an updated version, `AToMiC-Texts-v0.2.1`. For those interested in participating in the TREC 2023 evaluation, please use this updated version. If you wish to reproduce the results presented in our SIGIR paper, please use `AToMiC-Texts-v0.2`. We have created a spreadsheet highlighting the differences in retrieval effectiveness between the two versions, which can be found [here](https://docs.google.com/spreadsheets/d/1wSi_79Qx3GA1WAirwvoapiWJ4m2bPRM_rtUWRZ2qRIo/edit?usp=sharing).

## Changes
- Fix missing entity issues in `AToMiC-Text-v0.2`.

A passage in `AToMiC-Texts-v0.2` 
> text_id: 
> projected-08555460-002
> context_page_description: 
> The Boeing EC-135 is a retired family of  aircraft derived from the . During the , the EC-135 was best known for being modified to perform the  mission where one EC-135 was always airborne 24 hours a day to serve as flying command post for the  in the event of nuclear war. Various other EC-135 aircraft sat on airborne and ground alert throughout the Cold War, with the last EC-135C being retired in 1998. The EC-135N variant served as the tracking aircraft for the .\n\nThe Boeing E-6B "TACAMO" replaced the EC-135C.


The same passage in `AToMiC-Texts-v0.2.1`:
> text_id: 
> projected-08555460-002
> context_page_description: 
> The Boeing EC-135 is a retired family of command and control aircraft derived from the Boeing C-135 Stratolifter. During the Cold War, the EC-135 was best known for being modified to perform the Looking Glass mission where one EC-135 was always airborne 24 hours a day to serve as flying command post for the Strategic Air Command in the event of nuclear war. Various other EC-135 aircraft sat on airborne and ground alert throughout the Cold War, with the last EC-135C being retired in 1998. The EC-135N variant served as the tracking aircraft for the Apollo program.\n\nThe Boeing E-6B "TACAMO" replaced the EC-135C. 
