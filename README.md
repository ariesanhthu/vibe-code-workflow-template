# Vibe Code Template

---

## 1. Overview

This repo is a **Next.js-based template** designed for **AI-assisted development with strong documentation discipline**.

It combines:

- structured **application code**
- **Markdown documentation as source of truth**
- a **visual documentation workspace**
- **AI agent rules and skills**

This ensures **code, docs, and AI guidance stay synchronized**.

---

## System Overview

```mermaid
flowchart LR

Dev[Developer]
Agent[AI Agent]

Docs[Markdown Docs]
Graph[Visual Graph\nReact Flow]
Code[Application Code]

Dev --> Docs
Dev --> Graph

Agent --> Docs
Agent --> Code

Docs --> Graph
Graph --> Docs

Docs --> Code
Code --> Docs
````

Markdown docs remain the **source of truth**, while the graph provides a **visual navigation layer**.

---

# 2. Requirements

* Node.js 18+
* pnpm / npm / yarn
* Git
* Cursor (recommended) or VS Code

---

# 3. Getting Started

```bash
git clone <this-repo-url> my-app
cd my-app

pnpm install
pnpm dev
```

If the app lives inside a subfolder (for example `client/`):

```bash
cd client
pnpm install
pnpm dev
```

---

# 4. Project Structure

High-level repository structure:

```text
.
├─ docs/                     # Documentation (source of truth)
│  ├─ Project-Description/   # Product architecture & feature specs
│  └─ visual/                # React Flow visual documentation
│
├─ .cursor/                  # Cursor AI rules and skills
│  ├─ rules/
│  └─ skills/
│
└─ app source code           # Next.js application
```

### Architecture Relationship

```mermaid
flowchart TD

Docs[docs/]
Visual[docs/visual/]
Cursor[.cursor/]
Code[Application Code]

Docs --> Visual
Docs --> Code
Cursor --> Code
Cursor --> Docs
```

Before editing any folder, check its **`structure.md`** if present.

---

# 5. Documentation System (`docs/`)

All product and architecture documentation lives in **Markdown under `docs/`**.

These documents act as the **single source of truth**.

### Product Design Documentation

```mermaid
flowchart TD

A[product-design-01-summary]
B[product-design-02-assumptions-scope]
C[product-design-03-features-spec]
D[product-design-04-nextjs-frontend-architecture]
E[product-design-05-api-design]
F[product-design-06-database-schema]
G[product-design-07-nextjs-examples]
H[product-design-08-dev-checklist-timeline-tradeoffs]

A --> B
B --> C
C --> D
D --> E
E --> F
F --> G
G --> H
```

### Documentation Rules

Whenever code changes:

1. Update relevant docs under `docs/`
2. Update `structure.md` if folder structure changes
3. Sync `docs/visual/graph.json` if visual graph is used

---

# 6. Visual Docs Workspace (`docs/visual/`)

The **visual workspace** provides a **React Flow graph editor** for exploring project structure.

The visualization hierarchy:

```mermaid
flowchart TD

Feature --> Workflow
Workflow --> File
```

Example:

```mermaid
flowchart TD

AuthFeature[Feature: Auth]

LoginWorkflow[Workflow: Login Flow]
RegisterWorkflow[Workflow: Register Flow]

LoginPage[File: login.tsx]
AuthAPI[File: auth.controller.ts]

AuthFeature --> LoginWorkflow
AuthFeature --> RegisterWorkflow

LoginWorkflow --> LoginPage
LoginWorkflow --> AuthAPI
```

---

## Running the Visual Workspace

```bash
cd docs/visual
npm install
npm run dev
```

Then open:

```
http://localhost:5173
```

---

# Visual Graph Architecture

```mermaid
flowchart LR

GraphJSON[graph.json]

ReactFlow[React Flow UI]
MarkdownDocs[docs/*.md]

GraphJSON --> ReactFlow
ReactFlow --> GraphJSON

MarkdownDocs --> GraphJSON
GraphJSON --> MarkdownDocs
```

The graph acts as a **visual projection of documentation**.

---

# Docs ↔ Graph Workflow

### Docs → Graph

```mermaid
flowchart LR

EditDocs[Edit Markdown Docs]
ParseDocs[Agent parses docs]
UpdateGraph[Update graph.json]
RenderGraph[React Flow renders graph]

EditDocs --> ParseDocs --> UpdateGraph --> RenderGraph
```

### Graph → Docs

```mermaid
flowchart LR

EditGraph[Edit Graph UI]
ExportJSON[Export graph.json]
UpdateDocs[Update Markdown docs]

EditGraph --> ExportJSON --> UpdateDocs
```

If conflicts occur:

```
Markdown docs always win.
```

---

# 7. Cursor Rules & Skills (`.cursor/`)

The repository includes **Cursor rules and skills** to ensure AI agents behave consistently.

### Rule System

```mermaid
flowchart TD

Rules[.cursor/rules]

Identity[Agent Identity]
TaskClassify[Task Classification]
BuildMode[Build Mode]
DebugMode[Debug Mode]
OptimizeMode[Optimize Mode]
UIRules[UI Rules]

Rules --> Identity
Rules --> TaskClassify
Rules --> BuildMode
Rules --> DebugMode
Rules --> OptimizeMode
Rules --> UIRules
```

These rules enforce:

* architecture consistency
* UI standards
* documentation updates

---

### Skills

Skills extend agent capabilities.

```mermaid
flowchart TD

Skills[Cursor Skills]

DevOps[DevOps]
NextJS[Next.js]
UIUX[UI/UX Design]
CreateRule[Create Rule Skill]
CreateSkill[Create Skill]

Skills --> DevOps
Skills --> NextJS
Skills --> UIUX
Skills --> CreateRule
Skills --> CreateSkill
```

To add a new skill:

1. Copy an existing skill folder
2. Modify its `SKILL.md`
3. Commit to repository

---

# 8. Typical Workflow

### New Feature Development

```mermaid
flowchart LR

Design[Design Feature in Docs]
Graph[Optional Graph Update]
Implement[Implement Code]
SyncDocs[Update Docs]
Commit[Commit Changes]

Design --> Graph --> Implement --> SyncDocs --> Commit
```

### Refactoring

```mermaid
flowchart LR

UpdateDocs[Update Documentation]
RefactorCode[Refactor Code]
UpdateGraph[Update Visual Graph]

UpdateDocs --> RefactorCode --> UpdateGraph
```

---

# Working With AI Agents

Agents should follow this process:

```mermaid
flowchart TD

ReadStructure[Read structure.md]
ReadDocs[Read relevant docs]
UnderstandFeature[Understand Feature]
ImplementCode[Implement Code]
UpdateDocs[Update Docs]
SyncGraph[Sync graph.json]

ReadStructure --> ReadDocs --> UnderstandFeature --> ImplementCode --> UpdateDocs --> SyncGraph
```

This workflow ensures:

* consistent architecture
* synchronized docs
* predictable AI behavior

---

# Summary

This template ensures that:

* **Markdown docs define the system**
* **React Flow provides visual navigation**
* **Cursor rules guide AI agents**
* **Code stays aligned with documentation**

Result:

A **production-ready template** for teams that want **AI-assisted development without losing control of architecture or documentation**.

