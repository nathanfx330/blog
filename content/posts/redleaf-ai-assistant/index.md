---
title: "Redleaf Ai Assistant"
date: 2025-10-27T06:48:25-04:00
draft: false
---

## 🔎 How the Terminal AI Assistant Works

The assistant provides a **two-step workflow**: first search and summarize, then follow-up question mode.

### 1️⃣ Search and Summarize

When you issue a query, the assistant can:

- **Find documents** by ID or filename using `find_documents()`.  
- **Perform keyword search** for pages containing specific terms via `search_document_content()`.  
- **Conduct semantic search** using embeddings via `semantic_search_document_content()`, returning conceptually relevant sections even if exact words aren’t matched.

Once relevant results are found, the assistant **summarizes each document or page**, producing concise, context-aware overviews.

> Example:  
> You ask: *“What does this collection reveal about recent research on climate change?”*  
> The assistant identifies relevant pages, extracts the text, and summarizes the findings — giving a compact overview of each document or page.

### 2️⃣ Follow-Up Question Mode

After reviewing the summaries, you can ask **detailed follow-up questions**:

- Explore specific topics or entities.  
- Request clarification or expanded context from particular pages.  
- Iterate interactively: the assistant can reason over multiple pages and documents while keeping track of what’s been seen.

This workflow ensures that **search + summarize** happens first, then conversation is informed and structured, avoiding information overload.

### 3️⃣ LLM-Agnostic Design

The assistant is **model-agnostic**:  

- Defaults to **Gemma 12B** but can work with **any Ollama-compatible model**.  
- Integrates with Redleaf’s backend to orchestrate searches, summaries, and follow-up reasoning.  
- Keeps all your data **local and private**, no external APIs required.

---

## 🛠️ Redleaf AI Assistant Commands

Use the following commands in the terminal to interact with the assistant:

| Command Syntax | Description | Example |
|----------------|------------|---------|
| `find [query]` | Find documents by path without loading them. | `find research_notes` |
| `load [doc_id|path]` | Load a specific document for focused questions. | `load 1` |
| `search: [query]` | Perform a hybrid search across documents and summarize top results. | `search: climate models` |
| `id:[id] + page:[p] + [instr]` | Run an instruction on a specific page. | `id:1 + page:3 + summarize the main points` |
| `id:[id] + page:[p-p] + [instr]` | Run an instruction on a range of pages. | `id:1 + page:1-2 + extract key findings` |
| `search: [q] + [instr] + results:[N]` | Customize the number of search results returned. | `search: example + for each + summarize + results:30` |
| `/print` | Export the current chat session to an HTML file. | `/print` |

---

### 🔄 Example Workflow

```bash
# 1. Find a document
find research_notes

# 2. Load it for discussion
load 1

# 3. Perform a hybrid search and summarize top results
search: example

# 4. Follow up with page-specific instructions
id:1 + page:1-2 + summarize the main points

# 5. Override number of results if needed
search: example + for each + summarize + results:30

# 6. Export the session for offline review
/print
````

This structured syntax ensures users can **search, summarize, and reason interactively** without ever leaving the terminal.

---

## 🧩 Summary

The Redleaf AI Assistant is a **terminal-based research companion**, not a replacement for the engine:

* Performs **document search, semantic search, and summarization**.
* Supports **follow-up questions and iterative reasoning**.
* Fully **LLM-agnostic**, works with any Ollama model, and keeps your data local.

This addition transforms Redleaf from a purely passive knowledge engine into a **side-by-side AI assistant** — helping you reason, synthesize, and interact with your own document corpus in a **personal, private, and modular way**.

```

---

✅ Changes made:

- All **diplomatic / estate references removed**.  
- Examples replaced with **neutral, research-oriented queries**.  
- Workflow and commands remain intact, fully consistent and in a single code block.  
