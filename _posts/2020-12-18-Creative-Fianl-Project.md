---
layout: post
title: Creative Final Project for Fall 2020 Cloud Computing
---

- [My info & Paper selection](#my-info--paper-selection)
- [How each of selected papers relate to each other in big picture](#how-each-of-selected-papers-relate-to-each-other-in-big-picture)
- [Problems of the papers](#problems-of-the-papers)
- [Methods & Evaulation of the papers](#methods--evaulation-of-the-papers)
  - [Lamport](#lamport)
  - [Xen](#xen)
  - [Tracing](#tracing)
- [How each of paper is complementary to each other in detail](#how-each-of-paper-is-complementary-to-each-other-in-detail)

## My info & Paper selection

My name is **Zhaoqi Zhang**. I am writing this blog for the creative project for Comp 118 at Tufts Univesity in Fall 2020.

Since I submit the URL of this blog, which obviously means that **I am doing `Option 1: Explain research to a general audience` for the creative project.**

I am interested in **debugging tools for Cloud Computing**. I want to discuss how distributed tracing (workflow-centric tracing) fits in cloud computing, tracing origin, and how it is affected by cloud development, especially IaaS.

Thus, I selected the following paper:

1. [Lamport'78](https://dl.acm.org/doi/10.1145/359545.359563): `Time, clocks, and the ordering of events in a distributed system`, which is the math base of distributed tracing.
2. [Barham'03](https://dl.acm.org/citation.cfm?id=945462): `Xen and the art of virtualization`, the VM paper. I want to discuss how Xen affect distributed tracing as the key enabler of cloud.
3. [Sambasivan16](https://dl.acm.org/doi/10.1145/2987550.2987568): `Principled workflow-centric tracing of distributed systems` describes the workflow-centric tracing as debugging tool.****

___
For the sake of simplicity, I will use **Lamport Clock**, **Xen**, and **Tracing** to refer these three resepctively in the following sections of this blog.

## How each of selected papers relate to each other in big picture

As I mentioned above, the topic of my blog writing is debugging tools. This blog's overall goal is to connect distributed tracing with its math origin and its major influencer.

To organize my writing,

- I want to start with the math of debugging tools in the cloud and discuss a little bit about how it help in tracing.
- Then, talk about Xen and IaaS since Xen was introduced as the key enabler of cloud and how cloud affect traditional debugging.
- At last, I would introduce workflow-centric tracing as debugging tools.

## Problems of the papers

| Papers        | Research Problems                                                                                                                               |                                                     |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------|
| Lamport-clock | How to define the order in which events occur in distributed system                                                                             |                                                     |
| Xen           | How to host multiple applications and servers efficiently (make configuration simpler and faster)  while maintaining security and functionality | How to isolate their performance-related resources? |
| Tracing       | How tracing infrastructures should be designed to provide maximum benefit for essential management tasks                                        |                                                     |

Even though this part is relatively simple, I still want to point out that Lamport-clock provides rigorous math definition for both Xen and Tracing. What Xen result in is cloud that provides millions of VM for different customers, which we should remember the event order is defined by Lamport-clock. As for Tracing, the corelationship between Lamport-clock is more clearer that it is defined on Lamport's happens-before relationship.

## Methods & Evaulation of the papers

### Lamport

- **Methodology**
- **Evaulation**

### Xen

In this section, I will discuss about the methodology and evaluation of `Xen and the art of virtualization`

- **Methodology**

    The authors proposed an OS-level multiplexing which brings flexibility to coexist different OS in one machine and provides performance isolation between them.

    Starting from the proven direction of previous researches, Xen used a design principle of retrofitting support for performance isolation to the operating system. However, the authors implement the same strategy at a different level—they used OS-level multiplexing instead of process-level multiplexing. With multiplexing at the granularity of an entire operating system, it naturally provides performance isolation between them and allows a range of guest OSes to gracefully coexist rather than mandating a specific application binary interface.

- **Evaulation**

    As for evaluation, the authors conducted a series of experiments about its features. They begin by benchmarking it against a number of alternative virtualization techniques. Then, they compare the total system throughput executing multiple applications concurrently on a single native operating system against running each application in its own virtual machine. Later, they evaluate the performance isolation that Xen provides between guest OSes and assess the total overhead of running large numbers of operating systems on the same hardware.

### Tracing

In this section, I will discuss about the methodology and evaluation of `Principled workflow-centric tracing of distributed systems`

- **Methodology**

    This paper investigates and analyzes the existing workflow-centric tracing solutions and methodology(design axes) to design such tracing systems. Then the author distills the design space of workflow-centric tracing and describes key design choices that help or hinder a tracing infrastructure’s utility for crucial duties. Eventually, the author offers serval guidelines based on different tracing requirements.

    Despite there is a strong interest from industry in workflow-centric tracing infrastructures, there is very little clarity about how they should be designed to provide maximum benefit. Without research into this critical question, there is a danger that future tracing implementations will not live up to expectations and that the potential of workflow-centric tracing will be squandered.Here comes very necessary and vital needs  for the following section’s analysis--to categorize essential management tasks, to set foundational component, and to analyze method of preserving causal relationship.The author indicates there are mainly six management tasks covering from anomalous workflows, distributed profiling to dynamic monitoring. The tracing infrastructure's core components are metadata and propagational tracepoints with additional tracing components like value-added tracepoints, overhead-reduction mechanism, and storage & reconstruction component. The author also gives the definition of two methods of causality preserving method—submitter causality and trigger causality.

- **Evaulation**

    However, it is not necessary to evaluate this paper since what the paper does is giving evaulation and suggetion of existing industrial tracing product. Anyway, the following part is my favorite.
    
    The remaining part of the paper is magic. Firstly, the author analyzes the different strategies of adding tracepoints for propagational tracepoints and value-added tracepoints because of different homogeneity degrees. Engineers can make use of homogeneous components of propagational tracepoints to help easing the effort of instrumentation. At the same time, value-add tracepoints do not require much and provides the rugged dynamic instrumentation. Second, the author investigates several limiting overhead approaches introduced by the tracing system, especially a significant contributor, aggregation, and stymying the overhead-reduction technique. For out-of-band execution, network overhead is not a concern such that there are three types of sampling utilized—head-based coherent sampling, tail-based sampling, and hybrid sampling. And for in-band execution, strategies like lossy compression and partial execution are used to reduce tracing overhead. At last, the authors provide a detailed study of suggested design choices for various management tasks and options made by existing tracing implementations.

## How each of paper is complementary to each other in detail
