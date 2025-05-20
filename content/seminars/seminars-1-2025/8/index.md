---
title: "Fast, Flexible, and Intelligent Next-Generation Networks and Systems"
date: 2025-04-19T00:00:00-03:00
draft: true
tags: ["Data-Plane Intelligence", "High-Speed Machine Learning", "Declarative Network Programming"]
series: ["Seminars-1-2025"]
series_order: 8
seminarist: "Muhammad Shahbaz"
date_to_display: "2025-05-29"
---

## Abstract

Maintaining strict security and performance objectives in next-generation cloud and edge networks demands that compute-intensive management and control decisions are made on the current state of the entire network (e.g., topology, queue sizes, and link and server loads), and applied per-packet at line-rate, in a fast-and-intelligent way. Unfortunately, the dominant solutions available today are either fast-yet-dumb or slow-but-intelligent. Data-plane devices (e.g., switches and NICs) can react in nanoseconds to network conditions; however, they are designed for routing packets and have a constrained programming model (e.g., match-action tables or MATs). Conversely, control-plane servers can make complicated data-driven (AI-based) decisions, yet the round trip between the controller and the device fundamentally limits their reaction speed. 

In this talk, I will show how my research helps bridge this gap between speed, flexibility, and intelligence. I will present a new data-plane architecture (Taurus) and a declarative programming framework (Homunculus) that, for the first time, allows network operators to execute per-packet data-driven decisions directly within the data-plane device at line rate. I will first focus on the design of Taurus and the accompanying parallel-patterns abstraction (MapReduce), which supports data parallelism to efficiently execute common ML models (e.g., DNNs and SVMs). I will then demonstrate how, using training data, objectives, and constraints as inputs, Homunculus automatically converts the operator’s high-level policies into an efficient ML model to execute on the underlying data-plane device (e.g., Taurus). I will conclude with an overview of my broader research vision and future plans for realizing the full potential of fast, flexible, and intelligent next-generation networks (and systems).

## Bio

<img alt="Alireza Shirmarz" src="/seminars/seminars-1-2025/999/muhammad-shahbaz.png" style="width: 40%; height: 160x;">

Muhammad Shahbaz is an Assistant Professor of Computer Science at the University of Michigan. His research focuses on the design and development of domain-specific (performance) abstractions, compilers, and architectures for emerging workloads (including machine learning, self-driving networks, serverless/edge compute, and 5G). Shahbaz completed his postdoctoral research at Stanford University. He earned his Ph.D. and M.A. in Computer Science from Princeton University and his B.E. in Computer Engineering from the National University of Sciences and Technology (NUST). Before joining Michigan, Shahbaz was a Kevin C. and Suzanne L. Kahn New Frontiers Assistant Professor in Computer Science at Purdue University. He also worked as a Research Assistant at Georgia Tech and the University of Cambridge. Shahbaz has built open-source systems, including Taurus, Pisces, SDX, and NetFPGA-10G, that are widely used in industry and academia. He received the NSF CAREER Award; Facebook, Google, and Intel Research Awards; IETF/IRTF ANRP Prize; ACM SOSR Systems Award; APNet Best Paper Award; Best of CAL Paper Award; Internet2 Innovation Award; and Outstanding Graduate Teaching Assistant Award.


## Contact
E-mail: msbaz@umich.edu

[Google Scholar](https://scholar.google.com/citations?user=UhWjpNMAAAAJ&hl=en)

[GitLab](https://mshahbaz.gitlab.io/)



## Resources and Materials

[FEEC UNICAMP streams](https://www.youtube.com/@feec-unicamp/streams)

<!--
<iframe width="560" height="315" src="https://www.youtube.com/embed/lMptr7rmdco" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
-->

--- 
**Save the date:**  May, 29th, 2025.