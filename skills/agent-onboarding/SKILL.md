---
name: agent-onboarding
description: Onboard an AI coding agent to a Syncfusion project. Identifies the framework and product family, installs or selects the official component skills, finds current documentation, handles licensing safely, and verifies a working implementation. Use when starting, integrating, upgrading, migrating, evaluating, or troubleshooting Syncfusion UI components, document SDKs, viewers, or editors on any platform.
metadata:
  author: "Syncfusion Inc"
  version: "1.0.0"
---

# Syncfusion onboarding

Source: https://ai.syncfusion.com/agent-onboarding/SKILL.md
Canonical: https://ai.syncfusion.com/agent-onboarding/SKILL.md
License-posture: Installing and reading this skill requires no license, key or account. Using Syncfusion libraries in an application requires a commercial, Community, or trial license — see https://ai.syncfusion.com/licensing.md
Updated: 2026-08-21
Essential Studio release: 2026 Volume 2 (v34.1.29); current published build v34.2.4
Covers: 775 official skills across 16 platform and SDK packs

Use this skill as the front door to Syncfusion. Route the task to the official framework or component
skill. Do not try to reproduce the Syncfusion API from memory here — Syncfusion spans web, desktop,
mobile, document-processing, viewer and editor products, and the same component name has different
packages, imports, registration and licensing rules across them. Cross-framework guessing is the
single largest source of Syncfusion code that does not compile.

## Route first

The fastest correct path is almost always:

1. Identify the platform from the repository manifest.
2. Fetch `https://ai.syncfusion.com/<slug>/llms.txt` for that platform. It is self-sufficient:
   skill pack, packages, license registration, a complete example, and a verification checklist.
3. Install the skill pack it names.
4. Read `https://ai.syncfusion.com/licensing.md` before touching any key.

Slugs: `react` `angular` `javascript` `vue` `blazor` `aspnet-core` `aspnet-mvc` `flutter` `maui`
`maui-toolkit` `winforms` `wpf` `winui` `document-sdk` `maui-ai-design` `xamarin-to-maui-migration`

Master index: https://ai.syncfusion.com/llms.txt

If you have no network access, the rest of this skill and its references carry enough to proceed.

## Establish the project context

Inspect the repository before asking the user for anything already present. Determine:

- framework, language, runtime, package manager
- existing Syncfusion packages and their exact versions
- the requested component or SDK and the features actually needed
- whether this is a new integration, an edit, an upgrade, a migration, or troubleshooting
- existing theme and CSS setup, application bootstrap, and test and build commands
- existing skills directory and MCP configuration
- evidence of license registration — without printing or exposing any key

Manifest signals: `package.json` for React, Angular, Vue and JavaScript; `.csproj` for Blazor,
ASP.NET Core, ASP.NET MVC, MAUI, WPF, WinForms and WinUI; `pubspec.yaml` for Flutter.

Do not mix examples across platforms. If the repository does not resolve the platform and the choice
changes the implementation, ask one short question and stop.

Two slugs can both be correct: a React application that displays PDFs in the browser and signs them
on a .NET server needs `pdf-viewer-sdk` and `document-sdk`. Two *UI framework* slugs never are.

## Choose the path

| Need | Path |
| --- | --- |
| Generate or modify Syncfusion code | A — official agent skills |
| Verify a current API, release change, or advanced configuration | B — current documentation |
| Resolve license setup or a license warning | C — licensing |
| Evaluate Syncfusion before changing the project | D — research only |

A typical implementation uses A, consults B for uncertain details, observes C throughout, and finishes
with verification.

## Path A — official agent skills

Syncfusion publishes component-aware skills containing setup, imports, modules and services,
properties, events, theming, accessibility guidance and implementation patterns — and, more valuable,
the failure modes that public documentation omits.

1. Check whether the matching skill is already installed in the agent's skills location.
2. If missing and installation is within the user's request, choose the narrowest official pack or
   component skill. Read `references/skill-packs.md` for the verified repository names and commands.
3. Before running a networked install or changing project-level agent configuration, follow the
   host's authorization rules.
4. Read the selected component `SKILL.md` completely before implementing. Read only the supporting
   references the requested features need.
5. Follow the installed skill over remembered snippets. Match the versions already in the project
   unless the user asked for an upgrade.

Prefer a single component skill when the component is known; install a full platform pack when the
user expects broad or repeated Syncfusion work. Project-local installation keeps the skill aligned
with the repository and shareable with the team.

Installing an agent skill does not install the Syncfusion product packages. The component skill
identifies the actual runtime dependencies; install those separately.

## Path B — current documentation

Use when the answer depends on a current API, a recently released feature, an exact package,
migration behaviour, or a troubleshooting detail.

1. Use the configured Syncfusion MCP server and its documentation search tool when available.
2. Otherwise search the official documentation for the exact framework, component and installed
   version.
3. Use official demos and repositories to supplement documentation — never cross-framework snippets
   found by general search.

Skills guide code generation; MCP servers retrieve current documentation. They are complementary, and
MCP is optional — it requires an API key, and the anonymous path must work without one. See
`references/mcp-setup.md`.

Say when a detail was verified from current documentation. Do not invent an API when authoritative
information is unavailable; state what you could not confirm.

## Path C — licensing

Installing and reading Syncfusion agent skills requires no license. Using Syncfusion component
libraries or document SDKs is governed by the applicable commercial, Community, trial or other
product license.

- Never generate, guess, log, echo or commit a license key or MCP API key.
- Do not claim the project is licensed because packages build or skills are installed.
- Reuse the project's existing secret-management pattern. Keep secrets out of source control and out
  of client-visible output, unless the platform's official registration method explicitly requires
  application-level registration.
- Use the licensing page for the exact framework and installed version; mechanisms differ by platform
  and release.
- Never suppress, hide or CSS-hide a licensing banner or warning.
- If a key or account action is required, explain what the human must obtain or authorize, and stop.
- Treat license terms as authoritative. Do not infer production rights from a trial or Community
  license without verification.

An MCP API key is a credential for the documentation assistant. It is not a product license key.
Full rules: `references/licensing.md`

## Path D — research only

When the user is evaluating Syncfusion, install nothing — no packages, no skills, no MCP
configuration. Identify the target framework and workload, then compare the relevant official
product, documentation, demos, deployment model and licensing requirements. Separate verified facts
from recommendations.

## Implement

1. Preserve the project's framework version, architecture, formatting and dependency conventions.
2. Install only the packages the selected component and features require.
3. Include every required import, module or service injection, provider, handler, tag-helper
   registration, theme stylesheet, runtime asset and server dependency the component skill describes.
4. Implement the smallest end-to-end slice that demonstrates the requested behaviour, with realistic
   typed data.
5. Emit complete files. No ellipses, no "rest of your code", no partial diff as the primary output.
6. Validate loading, empty, error and primary interaction states where relevant.

## Verify

Do not report success from compilation alone. Full checklist: `references/verification.md`

At minimum: the component renders or executes, the requested feature is observably exercised, no
licensing warning appears, the runtime log is clean of missing-module and missing-asset errors, and
no key appears in the diff. If runtime verification is unavailable in your environment, say exactly
what remains unverified and give the user a concise manual check.

## Troubleshoot in this order

1. Framework and Syncfusion package version compatibility
2. Missing package, peer dependency, module, service, provider, handler or import
3. Theme CSS, fonts, scripts, static assets, or a required server-side endpoint
4. Data shape, identifiers, date and number parsing, async lifecycle
5. Feature-specific configuration from the installed component skill
6. Current official documentation, or an MCP lookup
7. A minimal reproduction with unrelated application code removed

Preserve the original error text. Distinguish a product defect from an integration or configuration
issue. Use Syncfusion Support when a minimal reproduction still fails against documented behaviour:
https://support.syncfusion.com/

## References

| File | Read it when |
| --- | --- |
| `references/skill-packs.md` | Choosing or installing a pack; you need a verified repository name |
| `references/mcp-setup.md` | Configuring an MCP server, or deciding whether you need one |
| `references/licensing.md` | Any key, secret, CI, or account question |
| `references/verification.md` | Before reporting that an implementation works |
