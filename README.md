# KnowledgeBaseSA

Survival Analysis knowledge base for article review and generating research ideas in Obsidian.

## Description
--------

The system is designed to organize the work of a research group on scientific materials. It allows you to: 
* Store and organize scientific articles 
* Conduct a collective review of materials 
* Generate and develop new ideas 
* Create plans for future research

## Structure
-----------------

```plaintext
vault/
├── Publications/
│   ├── Articles/
│   ├── Code/
│   ├── Data/
│   ├── Repository/
├── Thesaurus/
│   ├── Survival Analysis/
│   ├── Tasks/
│   ├── Methods/
│   ├── Feature space/
├── Thoughts/
│   ├── Problems/
├── Summary/
│   ├── Datasets
│   ├── Need to review
│   ├── Reviewed articles
├── src/
└── ResearchPlans/
    ├── drafts/
    └── outlines/
```

## Requirements
------------

* [Obsidian](https://obsidian.md/)
* [TagFolder](https://github.com/vrtmrz/obsidian-tagfolder) - for convenient tag organization 
* [Canvas](https://github.com/obsidian-canvas/obsidian-canvas) - for visualizing connections 
* [Dataview](https://github.com/blacksmithgu/obsidian-dataview) - for automatic updating of lists
* [Git](https://github.com/Vinzent03/obsidian-git) - for synchronization and collaborative work

## Setup
------------

1. Install Obsidian
2. Clone repository
3. Install plugins

## Use cases
--------------

### Papers review

1. Create new file in `Publications/`
2. Add header from template "Article":
```markdown
---
Title: 
Link: "[]()"
Year: 
Direction:
  - ""
Code: 
Type: 
Overview:
Datasets: 
Metrics:
  - 
Reviewer:
Source:
---
```

### Idea development

1. Open the Canvas for the current theme
2. Create a visual map of the connections 
3. Save the result to `Thoughts/`

## Collaborative work
------------------

### Article review rules

1. Each article should have fields: "Title", "Link", "Year", "Direction", "Code", "Novelty", "Overview", "Datasets", "Metrics", "Source" (Journal or Site).
2. Use markdown

## Сontribution
----------

Join the development! 
You can: 
1. Create a pull request with improvements 
2. Report problems found 
3. Offer new features 

Successful work! 🚀

### Sources
------------------

1. [Obsidian+Github вместо Notion: синхронизация, бекап и версионность (3-в-1)](https://habr.com/ru/articles/843288/)
2. [Управление личными делами в Obsidian (прототип)](https://habr.com/ru/articles/833654/)
3. [Organizing Academic Projects with Obsidian Tags and Mind Maps](https://effortlessacademic.com/organizing-academic-projects-with-obsidian-tags-and-mind-maps/)
4. [Obsidian + Dataview: Таблицы](https://habr.com/ru/articles/710356/)
5. [Dataview in Obsidian: A Beginner’s Guide](https://obsidian.rocks/dataview-in-obsidian-a-beginners-guide/#built-in-data)