---
layout: post
author: Xinyu Zhang
tags: [AI4Health, Unsupervised Learning]
---

[Click here to view the Poster](../assets/pdf/Poster_spatial.pdf)


### Decoding Post-Hurricane Mobility: A Deep Learning Approach Using Spatial Graphs and LLMs

In the chaotic aftermath of a natural disaster like a hurricane, understanding where people are going is crucial for an effective emergency response. Are they seeking medical care, searching for supplies, or evacuating to safety? Answering these questions helps officials allocate resources and save lives. However, the raw data from sources like cellphones is often sparse and irregular, making it difficult to see clear patterns.

In a recent project, my colleagues and I developed a novel, fully unsupervised machine learning framework to make sense of this complex data. We analyzed mobility patterns in Florida during the first 144 hours after Hurricane Ian made landfall. Our goal was to automatically identify distinct behavioral groups without any pre-existing labels.

#### Our Approach: Fusing "Where" with "Why"

Our method integrates two powerful sources of information to understand each person's trajectory.

1.  **Spatial Connectivity (The "Where"):** We first divided the entire region into a grid of small hexagons. To understand the physical road network and how these locations connect, we used a graph embedding technique called **Node2Vec**. This creates a vector for each hexagon that captures its relationship to its neighbors, essentially encoding the travel network.

2.  **Semantic Meaning (The "Why"):** A location is more than just a point on a map; it has a purpose. To capture this, we used a **Large Language Model (LLM)** to analyze the Points of Interest (POIs)—like restaurants, hospitals, or gas stations—within each hexagon. This gave us a rich "semantic embedding" that describes the function and character of each area.

By combining these two embeddings, we created a unique 128-dimensional "fingerprint" for each location visited over time, capturing both its geographic context and its real-world purpose.

#### Learning Trajectory Patterns with a Transformer Autoencoder

With our rich feature set, we then needed a model that could learn patterns from long, incomplete sequences of movements. We used an **attention-based transformer autoencoder**, a state-of-the-art deep learning architecture perfectly suited for handling sparse time-series data.

The autoencoder learns to compress each 144-hour trajectory into a low-dimensional latent representation—a compact summary that captures the essence of the entire journey. Trajectories with similar underlying behaviors will have similar latent representations.

#### Key Results: Discovering Interpretable Behaviors

By applying k-Means clustering to these learned representations, our model successfully identified five distinct mobility patterns from the unlabeled data. Using a method we developed called a "POI-deviation profile," we could interpret what each cluster represented. We discovered clear, behaviorally distinct groups, including:

* **Restaurant-Centric Activity:** A group showing sustained, above-average visits to restaurants and eating places.
* **Retail & Service Reopening:** A pattern characterized by a broad reopening of services, with significant activity at real estate offices, clothing stores, and urban transit systems.
* **Reduced Medical Visits:** A cluster that showed a significant drop in visits to dentists' offices, possibly indicating deferred healthcare appointments.

These findings demonstrate that our unsupervised approach can successfully uncover and interpret meaningful, real-world behaviors from complex mobility data.

#### Why This Matters

This project offers a powerful and transferable pipeline for making sense of human mobility in crisis situations. For disaster response agencies, this can provide rapid situational awareness, highlighting areas with high demand for medical services, food, or transit.

From a technical standpoint, this work showcases a strong command of end-to-end machine learning development, including:
* **Feature Engineering:** Fusing graph-based network data with LLM-derived semantic features.
* **Deep Learning:** Applying transformer-based models to learn representations from sparse, irregular time-series data.
* **Unsupervised Learning:** Using clustering techniques to discover hidden structure in high-dimensional, unlabeled datasets.
* **Interpretability:** Developing methods to translate complex model outputs into actionable, human-understandable insights.
