---
layout: post
title: Creative Final Project for Fall 2020 Cloud Computing
---

- [My info & Paper selection](#my-info--paper-selection)
- [How each of selected papers relate to each other in big picture](#how-each-of-selected-papers-relate-to-each-other-in-big-picture)
- [Problems of the papers](#problems-of-the-papers)
- [Methods & Evaulation of the papers](#methods--evaulation-of-the-papers)
- [How each of paper is complementary to each other in detail](#how-each-of-paper-is-complementary-to-each-other-in-detail)

## My info & Paper selection

My name is **Zhaoqi Zhang**. I am writing this blog for the creative project for Comp 118 at Tufts Univesity in Fall 2020.

Since I submit the URL to this blog, which obviously means that **I am doing `Option 1: Explain research to a general audience` for the creative project.**

I am interested in **debugging tools for Cloud Computing**. I want to discuss how distributed tracing (workflow-centric tracing) fits in cloud computing, tracing origin, and how it is affected by cloud development, especially IaaS.

Thus, I selected the following paper:

1. [Lamport'78](https://dl.acm.org/doi/10.1145/359545.359563): `Time, clocks, and the ordering of events in a distributed system`, which is the math base of distributed tracing.
2. [Barham'03](https://dl.acm.org/citation.cfm?id=945462): `Xen and the art of virtualization`, the VM paper. I want to discuss how Xen affect distributed tracing as the key enabler of cloud.
3. [Sambasivan16](https://dl.acm.org/doi/10.1145/2987550.2987568): `Principled workflow-centric tracing of distributed systems` describes the workflow-centric tracing as debugging tool.

For the sake of simplicity, I will use **Lamport Clock**, **Xen**, and **Tracing** to refer these three resepctively in the following sections of this blog.

## How each of selected papers relate to each other in big picture

As I mentioned above, the topic of my blog writing is debugging tools. This blog's overall goal is to connect distributed tracing with its math origin and its major influencer.

To organize my writing,

- I want to start with the math of debugging tools in the cloud and discuss a little bit about how it help in tracing.
- Then, talk about Xen and IaaS since Xen was introduced as the key enabler of cloud and how cloud affect traditional debugging.
- At last, I would introduce workflow-centric tracing as debugging tools.

## Problems of the papers

| Research Problems |   |   |
|-------------------|---|---|
| Lamport-clock     |   |   |
| Xen               |   |   |
| Tracing           |   |   |

## Methods & Evaulation of the papers

## How each of paper is complementary to each other in detail
