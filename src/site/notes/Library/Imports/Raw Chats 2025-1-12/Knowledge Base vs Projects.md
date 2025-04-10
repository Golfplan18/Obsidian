---
{"dg-publish":true,"permalink":"/library/imports/raw-chats-2025-1-12/knowledge-base-vs-projects/"}
---

# Knowledge Base Vs Projects

## Overview
- **Title:** Knowledge Base vs Projects
- **Url:** [https://chatgpt.com/c/6781e648-3900-8000-984e-47093f46978e](https://chatgpt.com/c/6781e648-3900-8000-984e-47093f46978e)
- **ID:** 6781e648-3900-8000-984e-47093f46978e
- **Created:** 1/10/2025, 7:32:24 PM
- **Last Updated:** 1/10/2025, 7:32:35 PM
- **Total Messages:** 2

## Conversation
👉 - Indicates the current conversation path

<i>[1/10/2025, 7:32:24 PM]</i> 👉 <b>👤 User</b>: 

in an obsidian second brain setup, there are notes that are intended to work like encyclopedia entries that you would refer back to for information over and over again. There are also notes that aren't intended as long-term documentation of knowledge, but instead they were useful for a specific purpose to solve a problem or further a project. I don't want to try to keep a pure knowledge base, and I don't want to waste or forget knowledge I acquired when working on a specific project, so the system must accommodate both.

How do I keep these two kinds of notes? It is as simple as tagging the knowledge base notes as part of the knowledge base and let the others be filterable links?
<br>

<i>[1/10/2025, 7:32:34 PM]</i> 👉 <b>🤖 Assistant</b>: 

Your approach of tagging knowledge base notes and leaving project-specific notes filterable is solid, but there are ways to refine it for better functionality and clarity. Here's a system that accommodates both types of notes within an Obsidian second brain setup:

---

### 1. **Differentiate By Note Purpose**
Use two broad categories to organize notes:
- **Knowledge Base Notes**: Timeless, evergreen information intended for repeated reference. These are like encyclopedia entries.
- **Project/Contextual Notes**: Temporary or context-specific information tied to a particular task, project, or period.

---

### 2. **Tagging And Metadata**
Tags and frontmatter metadata make it easy to distinguish between these types:
- **Knowledge Base Notes**: Use a tag like `#knowledge` or `#evergreen`. Include metadata in the YAML frontmatter, e.g.:
  ```yaml
  type: knowledge
  last_updated: YYYY-MM-DD
  ```
- **Project/Contextual Notes**: Use tags like `#project` or `#contextual` to indicate purpose. Add metadata, e.g.:
  ```yaml
  type: project
  project: "ProjectName"
  ```

---

### 3. **Folders Or Indexes**
- **Knowledge Base Notes**: Store these in a dedicated folder like `Knowledge` or `Encyclopedia`. This makes the notes easily searchable and maintainable.
- **Project Notes**: Keep these in a `Projects` folder or subfolders for active and archived projects.

---

### 4. **Linking For Cross-Referencing**
- **Knowledge Base Notes**: Treat these as centralized nodes in your graph. Link related notes and provide "See Also" sections within them.
- **Project Notes**: Link project notes to relevant knowledge base entries to leverage existing information, and link between related project notes for context.

---

### 5. **Filters And Queries**
Use Obsidian’s search and Dataview plugin for dynamic organization:
- **Knowledge Notes**:
  | File | last_updated |
| ---- | ------------ |

{ .block-language-dataview}
- **Project Notes**:
  | project | project |
| ------- | ------- |

{ .block-language-dataview}

---

### 6. **Lifespan Of Project Notes**
Instead of letting project notes fade into obscurity:
1. **Review After Completion**: Once a project is finished, scan its notes for reusable insights.
2. **Promote to Knowledge Base**: Convert relevant insights to evergreen notes and link back to the original project for context.

---

### 7. **Example Workflow**
1. While researching for a project, create notes in the `Projects` folder and tag them `#contextual`.
2. Link to related knowledge base notes tagged `#knowledge`.
3. On project completion, review and extract any reusable insights. Promote them to the `Knowledge` folder and tag them appropriately.

---

This system preserves project-specific insights while ensuring your knowledge base remains a living, growing repository. It avoids redundancy and supports both short-term utility and long-term growth.<br>

---

<div align="center">

### Made with Echoes by R2bits

<a href="https://echoes.r2bits.com">
  <img src="https://images.squarespace-cdn.com/content/v1/6493af4741c13939d335f0b8/18b27467-2da2-43b7-8d44-234bccf4f462/MINI_ECHOES_LOGO_NORMAL_WHITE_TEXT_SMALL-05-14+%281%29.png?format=300w" alt="Echoes Logo" width="200"/>
</a>

</div>

---

<div style="display: flex; justify-content: space-between;">
  <span>This conversation was exported on 2024-07-11T17:48:25.983Z using <a href="https://echoes.r2bits.com">Echoes</a> by R2bits.</span>
  <span>Export Format Version: 1.0</span>
</div>
