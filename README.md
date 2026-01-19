# PM Speckit

A specification-driven toolkit for Product Managers. Create structured PRDs, iterate with stakeholders, and generate Azure DevOps work items—all powered by your AI coding assistant.

Inspired by [GitHub's spec-kit](https://github.com/github/spec-kit), adapted for PM workflows.

## Features

- 📝 **Lightweight PRDs** for quick scoping and estimation
- 📋 **Full PRDs** with requirements, user stories, and success metrics
- 🔄 **Iterative refinement** with structured clarification workflow
- 📊 **Azure DevOps integration** - generate Epics, Features, and Tasks
- ✅ **Consistency validation** - catch issues before stakeholders do
- 📚 **Supporting artifacts** - docs, blogs, and demo scripts

## Quick Start

1. Clone this repo or copy to your workspace
2. Set up your AI assistant (see [Installation](#installation))
3. Run `/pm.constitution` to set your product principles
4. Run `/pm.specify [feature-name]` to create your first PRD

## Commands

| Command | Purpose |
|---------|---------|
| `/pm.constitution` | Establish product principles and guardrails |
| `/pm.specify` | Create lightweight PRD for scoping |
| `/pm.prd` | Create full PRD with requirements |
| `/pm.clarify` | Resolve open questions via Q&A |
| `/pm.tasks` | Generate Azure DevOps work items |
| `/pm.analyze` | Validate cross-document consistency |
| `/pm.docs` | Generate user documentation |
| `/pm.blog` | Generate announcement blog post |
| `/pm.demo` | Generate demo script |

## Workflow

```
/pm.constitution (once per product)
        ↓
/pm.specify → /pm.clarify → /pm.prd → /pm.tasks → /pm.analyze
                                                       ↓
                                      /pm.docs, /pm.blog, /pm.demo
```

## Installation

### GitHub Copilot (VS Code)

1. Clone this repo to your workspace
2. Create `.github/copilot-instructions.md` in your project:

```markdown
When I use /pm.* commands, follow the templates in PM-Speckit:
- /pm.constitution → templates/commands/constitution.md
- /pm.specify → templates/commands/specify.md
- /pm.prd → templates/commands/prd.md
- /pm.clarify → templates/commands/clarify.md
- /pm.tasks → templates/commands/tasks.md
- /pm.analyze → templates/commands/analyze.md
- /pm.docs → templates/commands/docs.md
- /pm.blog → templates/commands/blog.md
- /pm.demo → templates/commands/demo.md
```

3. Use commands in Copilot Chat: `/pm.specify my-feature`

### Other AI Assistants

Works with Claude, Cursor, and other AI coding assistants. See [docs/quickstart.md](docs/quickstart.md) for setup instructions.

## Folder Structure

```
PM-Speckit/
├── memory/
│   └── constitution.md      # Product principles template
├── docs/
│   ├── requirements.md      # What PM Speckit does
│   ├── design.md            # How it works
│   └── quickstart.md        # Getting started guide
├── templates/
│   ├── feature-overview.md  # Lightweight PRD template
│   ├── prd.md               # Full PRD template
│   ├── ado-workitems.md     # Azure DevOps work items
│   ├── documentation.md     # User docs template
│   ├── blog.md              # Blog post template
│   ├── demo-script.md       # Demo script template
│   ├── commands/            # Command definitions
│   └── checklists/          # Approval & launch checklists
└── prds/                    # Your generated PRDs go here
```

## Customization

All templates are in `templates/`. Edit them directly to customize the output format for your team.

## Documentation

- [Quickstart Guide](docs/quickstart.md)
- [Requirements](docs/requirements.md) - What PM Speckit does
- [Design](docs/design.md) - Architecture and command flow

## Contributing

1. Update `docs/requirements.md` with new capability
2. Create command template in `templates/commands/`
3. Create output template in `templates/` if needed
4. Update `docs/design.md` with changes

## License

MIT
