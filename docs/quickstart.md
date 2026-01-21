# PM Speckit Quickstart Guide

> Get started with PM Speckit in 5 minutes.

---

## What is PM Speckit?

PM Speckit is a specification-driven toolkit for Product Managers. It helps you:

- Create structured, consistent PRDs
- Iterate with stakeholder feedback
- Generate Azure DevOps work items
- Produce supporting content (docs, blogs, demos)

It works with any AI coding assistant (GitHub Copilot, Claude, Cursor, etc.).

---

## Installation

### Option 1: Clone the Repository

```bash
git clone https://github.com/[your-org]/pm-speckit.git
cd pm-speckit
```

### Option 2: Copy to Your Project

Copy the entire `PM-Speckit` folder into your project workspace.

### Option 3: Use as a Template

1. Download/clone this repository
2. Copy to your working directory
3. Customize templates as needed

---

## Setup for Your AI Assistant

PM Speckit works by providing context to your AI coding assistant. Choose your setup:

### GitHub Copilot (VS Code)

1. Open the `PM-Speckit` folder in VS Code
2. Open Copilot Chat (Ctrl+Shift+I or Cmd+Shift+I)
3. Reference the command template when asking:
   ```
   @workspace Using the template in templates/commands/specify.md, 
   help me create a feature overview for [your feature]
   ```

**Tip**: Add PM Speckit as a workspace folder alongside your project.

### GitHub Copilot with Custom Instructions

1. Create `.github/copilot-instructions.md` in your repo:
   ```markdown
   # PM Speckit Instructions
   
   When I use /pm.* commands, follow the templates in the PM-Speckit folder:
   - /pm.specify → Use templates/commands/specify.md
   - /pm.prd → Use templates/commands/prd.md
   - /pm.clarify → Use templates/commands/clarify.md
   - /pm.tasks → Use templates/commands/tasks.md
   - /pm.analyze → Use templates/commands/analyze.md
   - /pm.docs → Use templates/commands/docs.md
   - /pm.blog → Use templates/commands/blog.md
   - /pm.demo → Use templates/commands/demo.md
   
   Always read the relevant command template before executing.
   ```

### Claude (via API or Claude.ai)

1. Include PM Speckit folder in your project
2. When starting a session, say:
   ```
   I'm using PM Speckit for PRD management. The templates are in 
   the PM-Speckit folder. When I use /pm.* commands, please follow 
   the corresponding template in templates/commands/.
   ```

### Cursor

1. Open PM Speckit folder in Cursor
2. Add to `.cursorrules`:
   ```
   When user types /pm.* commands, read and follow the matching 
   template in PM-Speckit/templates/commands/
   ```

### Other AI Assistants

The pattern is the same:
1. Include PM Speckit in your workspace
2. Tell the AI to reference `templates/commands/[command].md` when you use `/pm.[command]`

---

## Prerequisites

- An AI coding assistant that supports custom commands/prompts
- This PM Speckit folder in your workspace

---

## Your First Feature (5 Minutes)

### Step 1: Set Up Your Constitution (Optional but Recommended)

The constitution defines your product principles. Run once per product.

```
/pm.constitution
```

The AI will ask about your product vision, target users, and guardrails. It creates `memory/constitution.md`.

---

### Step 2: Create a Feature Overview

Start with a lightweight PRD for scoping:

```
/pm.specify [feature name]
```

**Example**: `/pm.specify AI-powered search`

The AI will ask about:
- The problem you're solving
- Your proposed solution
- Scope boundaries

It creates: `prds/001-[feature-name]/feature-overview.md`

---

### Step 3: Resolve Clarifications

If there are open questions marked with `[NEEDS CLARIFICATION]`:

```
/pm.clarify [feature number or name]
```

**Example**: `/pm.clarify 001`

The AI walks through each question, records answers, and updates the document.

---

### Step 4: Create Full PRD

Expand the feature overview into a complete PRD:

```
/pm.prd [feature number or name]
```

**Example**: `/pm.prd 001`

This creates `prd.md` with:
- User stories and acceptance criteria
- Requirements with IDs
- Success metrics
- Risks and dependencies

---

### Step 5: Generate Work Items

Create Azure DevOps-ready work items:

```
/pm.tasks [feature number or name]
```

**Example**: `/pm.tasks 001`

This creates `ado-workitems.md` with Epics, Features, and Tasks you can import.

---

### Step 6: Validate Consistency

Check for issues before stakeholder review:

```
/pm.analyze [feature number or name]
```

**Example**: `/pm.analyze 001`

This reports any:
- Constitution violations
- Unresolved clarifications
- Missing work items
- Ambiguous language

---

### Step 7: Generate Supporting Content

When ready, create documentation, blog posts, or demo scripts:

```
/pm.docs 001    # User documentation
/pm.blog 001    # Announcement blog post
/pm.demo 001    # Demo script
```

---

## Command Reference

| Command | Purpose | Creates |
|---------|---------|---------|
| `/pm.constitution` | Set product principles | `memory/constitution.md` |
| `/pm.specify` | Lightweight PRD | `feature-overview.md` |
| `/pm.prd` | Full PRD | `prd.md` |
| `/pm.clarify` | Resolve open questions | `clarifications.md` |
| `/pm.tasks` | Azure DevOps work items | `ado-workitems.md` |
| `/pm.analyze` | Consistency check | Console report |
| `/pm.docs` | User documentation | `documentation.md` |
| `/pm.blog` | Blog post | `blog.md` |
| `/pm.demo` | Demo script | `demo-script.md` |
| `/pm.learn` | Learn any concept | Interactive (no file) |

---

## Typical Workflow

```
/pm.constitution (once per product)
        ↓
/pm.specify → /pm.clarify → /pm.prd → /pm.clarify → /pm.tasks
                                                         ↓
                                                   /pm.analyze
                                                         ↓
                                    /pm.docs, /pm.blog, /pm.demo
```

---

## Folder Structure

After creating a feature, your workspace looks like:

```
PM-Speckit/
├── memory/
│   └── constitution.md           # Product principles
├── docs/
│   ├── requirements.md           # PM Speckit's own docs
│   ├── design.md
│   └── quickstart.md             # This file
├── templates/                    # Output templates
├── templates/commands/           # Command definitions
├── templates/checklists/         # Checklists
└── prds/
    └── 001-your-feature/
        ├── feature-overview.md   # Lightweight PRD
        ├── prd.md                # Full PRD
        ├── clarifications.md     # Q&A log
        ├── ado-workitems.md      # Work items
        ├── documentation.md      # User docs
        ├── blog.md               # Blog post
        └── demo-script.md        # Demo script
```

---

## Customizing Templates

All templates are in the `templates/` folder. Edit them directly to change the output format. Changes apply to all future documents.

---

## Tips

1. **Start small**: Use `/pm.specify` even for rough ideas—it helps structure your thinking.

2. **Clarify early**: Resolve `[NEEDS CLARIFICATION]` markers before expanding to full PRD.

3. **Run analyze often**: `/pm.analyze` catches issues before stakeholders do.

4. **Iterate freely**: PRDs are living documents. Update and re-run commands as needed.

5. **Use checklists**: Find stakeholder sign-off and launch readiness checklists in `templates/checklists/`.

---

## Getting Help

- See [requirements.md](requirements.md) for what PM Speckit does
- See [design.md](design.md) for how it works
- Check command templates in `templates/commands/` for detailed behavior

---

## Feedback

PM Speckit is designed to evolve. To add new capabilities:

1. Update `docs/requirements.md` with new capability
2. Create command template in `templates/commands/`
3. Create output template in `templates/` (if needed)
4. Update `docs/design.md` with architecture changes
