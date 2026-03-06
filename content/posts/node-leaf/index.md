---
title: "Node Leaf"
date: 2026-03-06T14:56:41-05:00
author: "Nathaniel Westveer"
draft: false
---
I recently reached a major milestone in a long-term personal project: a nodal word processor built in Flutter. [Deep Writer Blog Post](https://nathanfx330.github.io/blog/posts/deep-writer/)
 Designed to integrate with the Redleaf knowledge engine, this application structures writing and research into a visual web of nodes that pipe data directly into local LLMs through Ollama. I started Node Writer to pursue a long-held dream of creating a nodal word processor, with the vision that it would naturally merge with Redleaf’s development—evolving into an assistant that grows its ability to help you work with nodes.

The driving force behind this project is the challenge of AI alignment at the interface level. Current chat interfaces are linear and restrictive. They make it difficult to group ideas, test variations, or provide an AI system with complex context beyond what exists in its training data.

Instead of encountering LLM rejection or hallucinations when introducing unfamiliar concepts, a nodal design allows us to guide the model's understanding step by step. It works by turning context retrieval into a transparent, visual pipeline:

Targeted Retrieval: Building on Redleaf’s spaCy-powered entity indexer, specific nodes can query exact entities, documents, or catalogs.

Transparent Context: A context node acts as a scratchpad where searches can be executed and previewed before being sent to the model. If the retrieved data is flawed, it can be corrected before the AI ever sees it.

Paragraph-Level Assistance: Because context is modular, LLM analysis can be injected at any point in the writing process. This allows experimentation with branches and variations without collapsing the entire context window.

This modular design encourages exploration and critical thinking rather than passive prompting.

Watching the system evolve has been remarkable. Redleaf showed promise when it existed only as a chat interface, but adding visual abstraction and integrated workflows has transformed theoretical concepts into something far more practical and powerful.

Below is a screenshot of the current workflow. Reaching this point has been incredibly rewarding. It represents the exact moment I envisioned when I first started building Redleaf nearly a year ago.

Hello world, I give you NODE LEAF:
{{< figure src="nl.png" title="Node Leaf" width="750px" >}}
