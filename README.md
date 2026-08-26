# agent-onboarding

Front-door skill for onboarding an AI coding agent to any Syncfusion project. Identifies the
framework and product family, installs or selects the right official component skill, fetches
current documentation, licenses safely, and verifies a working implementation — across web,
desktop, mobile, viewer, editor and document-processing products.

## Quick Start

### Option 1: Using npx (Recommended)

If your assistant supports npx-based skill installation:

```bash
npx skills add https://github.com/syncfusion/agent-onboarding-skill
```

This will automatically add the skill to your workspace.

If your repository URL is different, replace the URL in the command.

### Option 2: Manual Workspace Setup

**1. Clone this repository**

```bash
git clone https://github.com/syncfusion/agent-onboarding-skill.git
```

**2. Add it to your VS Code workspace**

Open your `.code-workspace` file (or create one) and add this repo as a second root folder:

Example workspace file:

````json
{
  "folders": [
    { "path": "/path/to/your-app" },
    { "path": "/path/to/agent-onboarding" }
  ]
}
````

## Workspace Setup Recommendation

For onboarding, keep the skill and the target project in the same Code Studio workspace:

- Target project (any platform: React, Angular, Vue, Blazor, ASP.NET Core, ASP.NET MVC, MAUI,
  Flutter, WinForms, WPF, WinUI, or a document/viewer SDK)
- this skill folder

This lets the AI assistant inspect the repository manifest (`package.json`, `.csproj`,
`pubspec.yaml`) against the skill's routing rules and pick the correct platform slug and
component skill on the first pass.

Example folder layout:

```text
/workspace/
  MyApp/
  agent-onboarding/
```

You can open the parent folder as one workspace, or add both as folders in a
`.code-workspace` file.

## Prerequisites

- An AI coding assistant that supports workspace skills and reference files.
- The target project's framework SDK installed (Node, .NET SDK, Flutter SDK etc., matching
  the platform you are onboarding).
- A Syncfusion license (commercial, Community, or trial) **only if** you intend to run the
  resulting application. Reading and following this skill requires no license, no key and no
  account — see [licensing.md](references/licensing.md).

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

## Repository Structure

```text
README.md
SKILL.md
references/
  licensing.md
  mcp-setup.md
  skill-packs.md
  verification.md
```

## What This Skill Covers

| Topic | Where to look |
| --- | --- |
| Platform slugs and `llms.txt` entries (React, Angular, Blazor, .NET MAUI, Flutter, …) | `SKILL.md` → Route first |
| Official skill-pack names and `npx skills add` commands | [skill-packs.md](references/skill-packs.md) |
| When and how to set up a Syncfusion MCP server | [mcp-setup.md](references/mcp-setup.md) |
| License-key handling, MCP API key handling, agent trust boundaries | [licensing.md](references/licensing.md) |
| Pre-completion verification checklist | [verification.md](references/verification.md) |

## Decision Paths

This skill routes the task into one of four paths. Pick before writing code.

| Need | Path | Reference |
| --- | --- | --- |
| Generate or modify Syncfusion code | A — official agent skills | [skill-packs.md](references/skill-packs.md) |
| Verify a current API, release change, or advanced configuration | B — current documentation | [mcp-setup.md](references/mcp-setup.md) |
| Resolve license setup or a license warning | C — licensing | [licensing.md](references/licensing.md) |
| Evaluate Syncfusion before changing the project | D — research only | `SKILL.md` → Path D |

A typical implementation uses Path A, consults Path B for uncertain details, observes Path C
throughout, and finishes with the [verification checklist](references/verification.md).

## Example Prompts

- Onboard this React project to Syncfusion and tell me which component skill and packages to install.
- I'm starting a new Blazor Server app with the Syncfusion Grid. What do I need before I write code?
- Help me migrate an existing Angular app from Syncfusion v27 to the current Essential Studio release.
- I have a Flutter app needing a PDF viewer and a Signature Pad — which slugs and skills do I use?
- Evaluate whether Syncfusion Document SDK is the right choice for our server-side PDF workflow.
- I'm seeing a Syncfusion license-warning banner after install — diagnose and remediate without rotating the key.
- Set up the Syncfusion MCP server for my editor and verify the API key works without exposing it.

## License Posture

Installing and reading this skill requires no license, key or account. Using Syncfusion
libraries or document SDKs in an application requires a commercial, Community, or trial
license. See [licensing.md](references/licensing.md) for the agent trust boundaries around
keys, MCP credentials, and CI usage.

Canonical source of this skill: <https://ai.syncfusion.com/agent-onboarding/SKILL.md>