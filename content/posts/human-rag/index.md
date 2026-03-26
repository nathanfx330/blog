---
title: "Human RAG: The Forgotten Half of Retrieval"
date: 2026-03-25T02:35:06-04:00
draft: false
---

The AI industry is currently fixated on RAG (Retrieval-Augmented Generation). The premise is straightforward: an LLM is only as effective as the context it receives, so we augment prompts with relevant information retrieved from vector databases.

This approach works well, for machines.

But it quietly overlooks something critical: the human in the loop.

Before RAG became a buzzword, we called this process something much simpler, *search*. But search has fundamentally degraded for humans. We’ve watched the death of powerful, standalone search utilities (like the old Google Search Appliance hardware) in favor of walled-garden cloud storage like Google Drive, where finding a specific document feels like a roll of the dice. 

Search has become worse for humans, but paradoxically, better for AI. We’ve engineered incredibly sophisticated pipelines to retrieve and feed context into language models, while leaving the human user with almost none of that context themselves. 

This is the gap I set out to address with the Redleaf Knowledge Engine and its visual counterpart, Node Leaf. 

I think of it as **Symmetrical RAG**. 

It is a system where retrieval serves the human mind just as powerfully as it serves the algorithmic one.

{{< figure src="rome1.png" title="Redleaf surfaces connections to the human first." width="750px" >}}
{{< figure src="rome2.png" title="Redleaf surfaces connections to the human first." width="750px" >}}


In Redleaf, retrieval is transparent. When a document is processed, it doesn’t disappear into a vector store for later use. It is analyzed, decomposed, and surfaced. People, organizations, and relationships are extracted and presented directly in the Discovery interface. You can trace the exact sentences where entities intersect. The system gives *you* context before anything is ever passed to a model.

Node Leaf extends this idea into a spatial environment.

Instead of interacting with a hidden retrieval pipeline through a chat window, you construct it directly. Document nodes, search nodes, and entity nodes can be arranged, connected, and evaluated in real time. You curate the context yourself. You inspect it. You refine it.

Only after that process, the Human RAG layer is complete do you pass the result into an LLM, such as through an Ollama output node.

This changes the role of AI from an opaque generator into a final step in a visible reasoning process.

When retrieval is hidden, users become dependent on the system and vulnerable to hallucination. When retrieval is exposed—when it becomes visual, spatial, and symmetrical—users remain in control. They think more critically. They engage more deeply.

As I noted in the release of Deep Writer, the goal is not automation.

It is amplification.