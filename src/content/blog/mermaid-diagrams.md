---
title: 'Mermaid Diagrams in Astro'
description: 'How to use mermaid diagrams for visualizing architecture, flows, and more'
pubDate: 'Mar 24 2026'
heroImage: '../../assets/blog-placeholder-2.jpg'
---

This blog supports [Mermaid](https://mermaid.js.org/) diagrams rendered client-side via the `astro-mermaid` integration. You can embed diagrams directly in Markdown using fenced code blocks with the `mermaid` language tag.

## Deployment Flow

Here's a simple diagram showing how this blog is built and deployed:

```mermaid
flowchart TD
    A[Push to main] --> B[GitHub Actions triggered]
    B --> C[Checkout repo]
    C --> D[withastro/action builds site]
    D --> E[Upload artifact]
    E --> F[Deploy to GitHub Pages]
    F --> G[Site live at slimslenderslacks.github.io]
```

## Architecture Overview

```mermaid
graph LR
    Author -->|writes Markdown / MDX| Repo[(Git Repo)]
    Repo -->|CI/CD| GHA[GitHub Actions]
    GHA -->|astro build| Pages[GitHub Pages]
    Pages -->|serves| Visitor
```

## Content Pipeline

```mermaid
sequenceDiagram
    participant Dev as Developer
    participant GH as GitHub
    participant GHA as Actions
    participant CDN as GitHub Pages

    Dev->>GH: git push origin main
    GH->>GHA: trigger workflow
    GHA->>GHA: npm install & astro build
    GHA->>CDN: deploy-pages action
    CDN-->>Dev: ✓ Site updated
```

## Supported Diagram Types

Mermaid supports many diagram types out of the box:

- **Flowcharts** – decision trees, pipelines
- **Sequence diagrams** – service interactions
- **Class diagrams** – OOP structures
- **Gantt charts** – project timelines
- **Entity relationship diagrams** – data models
- **State diagrams** – finite state machines

```mermaid
stateDiagram-v2
    [*] --> Draft
    Draft --> Review : submit
    Review --> Published : approve
    Review --> Draft : request changes
    Published --> [*]
```
