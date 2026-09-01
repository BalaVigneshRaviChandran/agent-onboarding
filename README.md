# syncfusion-onboarding

Front-door skill for onboarding an AI coding agent to any Syncfusion project. Identifies the
framework and product family, installs or selects the right official component skill, fetches
current documentation, licenses safely, and verifies a working implementation — across web,
desktop, mobile, viewer, editor and document-processing products.

## Quick Start

### Using npx

This following command will install the skill to your workspace.

```bash
npx skills add https://github.com/syncfusion/agent-onboarding-skill
```

## The Onboarding Site — ai.syncfusion.com

This skill enforces **[Syncfusion for AI coding agents](https://ai.syncfusion.com)**, the
official Syncfusion onboarding site as the source of truth. All routing, inventory, license,
and verification rules come from that site — never from the model's training memory.

## How This Skill Works

The skill folder contains:

- `SKILL.md`: Intent, routing rules, paths, and constraints.
- `references/`: Supporting guidance used for deeper onboarding tasks.

When a prompt matches the skill's intent — starting, integrating, upgrading, migrating,
evaluating, or troubleshooting a Syncfusion UI component, document SDK, viewer, or editor on
any platform — the assistant applies this skill to identify the framework, route to the
correct official component skill, and produce guidance and action items.

This is a **meta-skill**. It does not generate component code itself; it routes to the
official framework or component skill that does. Do not try to reproduce the Syncfusion API
from memory here — same component name can have different packages, imports, registration
and licensing rules across platforms.

## What This Skill Covers

| Topic | Where to look |
| --- | --- |
| Platform slugs and `llms.txt` entries (React, Angular, Blazor, .NET MAUI, Flutter, …) | `SKILL.md` → Route first |
| Official skill-pack names and `npx skills add` commands | [skill-packs.md](references/skill-packs.md) |
| When and how to set up a Syncfusion MCP server | [mcp-setup.md](references/mcp-setup.md) |
| License-key handling, MCP API key handling, agent trust boundaries | [licensing.md](references/licensing.md) |
| Pre-completion verification checklist | [verification.md](references/verification.md) |


## License

These skills are provided as educational resources for working with Syncfusion components. Syncfusion components require a valid license key. To acquire a license, you can quote a purchase at https://www.syncfusion.com/sales/pricing.