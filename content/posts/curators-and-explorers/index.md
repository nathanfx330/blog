---
title: "Curators and Explorers"
date: 2025-09-28T04:14:29-04:00
draft: false
---
Today marks a major milestone for the Redleaf Engine. I’m thrilled to announce a new set of features that transform Redleaf from a personal knowledge tool into a powerful platform for **distributing curated datasets and enabling team collaboration**.

The core idea is simple but powerful: what if you could do all the heavy lifting of processing hundreds of documents and then package the entire, fully-analyzed knowledge base into a single, portable unit? What if you could send that “knowledge package” to a colleague, a research team, or even publish it for the world to explore?

Now you can. This is made possible by two new, distinct workflows: the **Curator** and the **Explorer**.

---

## 🔄 The Git-Powered Workflow

At its heart, this new model uses Git as the distribution backbone. The entire collaborative process can be visualized like this:

🏛️ The Curator: Building the Exhibit

Think of a museum curator. They meticulously gather artifacts, conduct research, and arrange everything into a coherent exhibit. The Redleaf Curator does the same with digital documents.

The Curator uses Redleaf in its full, standard mode. They have access to the entire processing workflow: discovering documents, running the NLP pipeline, and building the knowledge graph. They are the gatekeepers of the canonical dataset.

When the "exhibit" is ready, the Curator runs:
code Bash

    
python bulk_manage.py export-precomputed-state


This command does two crucial things:

- 🔒 **Sanitizes the Database** – First warns the Curator, then wipes all private, user-specific data (like user accounts and private notes) from the local database. Ensures no private information is included in the public release.

- 📦 **Packages the Knowledge** – Exports the entire public knowledge graph (all documents, entities, relationships, and tags) into a single `initial_state.sql` file. Also creates a `precomputed.marker` file, which acts as the "seal" on the package.




The Curator then commits these files, along with the source documents/ folder, to a Git repository to publish the new version.
code Bash

    
# Add the newly exported state files and any new documents
git add instance/initial_state.sql instance/precomputed.marker
git add documents/

# Commit the changes with a clear message
git commit -m "Release v1.1 of the knowledge base"

# Push to the remote repository
git push

  

🔎 The Explorer: Unpacking and Discovering

An Explorer is anyone who receives this precomputed knowledge package. Their experience is designed to be effortless:

    Clone & Run – The Explorer clones the Curator’s repository from GitHub and runs the application:

code Bash

    
git clone https://github.com/curator/their-redleaf-project.git
cd their-redleaf-project

# Now, install the environment and run...
python run.py

  

    Automatic Setup – Redleaf detects the precomputed.marker and automatically builds the entire knowledge base from the provided .sql file. No processing is needed.

    Welcome Aboard – On their first visit, the Explorer is greeted by a special welcome screen to create their own private, local account.

Once logged in, the Explorer has access to the complete, fully-featured knowledge graph. They can search, browse entities, and explore relationships instantly.

{{< figure src="dashboard_explorer.jpg" title="The Redleaf dashboard in Explorer Mode. Note that the processing buttons are disabled." width="750px" >}}

The processing buttons on the dashboard are intentionally disabled, or "braced for transit," keeping the interface clean and focused on discovery.

---

## 🔄 Closing the Loop: The Collaboration Model

This isn't just a one-way street. Explorers can also contribute back to the main project.

To share their annotations:

```bash
python bulk_manage.py export-contributions <their-username>
```

This creates a small, lightweight `.json` file containing only their new annotations. They can send this file to the Curator, who can then use the **Import Contributions** panel in the Settings page to review and selectively merge these suggestions into the main knowledge base.

This transforms Redleaf into a **true collaborative tool**, allowing teams to work together to enrich a central dataset.

---

## 🌟 What This Means for Redleaf

This update fundamentally expands what Redleaf is for. It’s now a platform for:

* Researchers to share fully processed datasets with colleagues.
* Archivists to publish digital collections that are immediately explorable.
* Teams to collaborate asynchronously on a shared body of knowledge.

I’m incredibly excited about the new possibilities this unlocks and can’t wait to see what you build with it.