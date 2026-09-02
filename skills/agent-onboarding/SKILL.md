---
name: agent-onboarding
description: Onboard an AI coding agent to a Syncfusion project. Identifies the framework and product family, installs or selects the official component skills, finds current documentation, handles licensing safely, and verifies a working implementation. Use when starting, integrating, upgrading, migrating, evaluating, or troubleshooting Syncfusion UI components, document SDKs, viewers, or editors on any platform.
metadata:
  author: "Syncfusion Inc"
  version: "1.0.0"
---

# Syncfusion onboarding

Use this skill as the front door to Syncfusion. Route the task to the official framework or component
skill. Do not try to reproduce the Syncfusion API from memory here — Syncfusion spans web, desktop,
mobile, document-processing, viewer and editor products, and the same component name has different
packages, imports, registration and licensing rules across them. Cross-framework guessing is the
single largest source of Syncfusion code that does not compile. The second is same-platform name
collision: the word the user typed matches one component while the behavior they asked for belongs
to another — resolve it by comparing inventory descriptions against the required behavior, never by
name alone.

## Hard rule — read the inventory before naming any skill

You MUST have read the platform inventory at `https://ai.syncfusion.com/<platform-slug>/inventory.txt`
in this session **before** you name, install, or write code against any Syncfusion component skill.
If you have not read it in this session, fetch it now and do not continue.

When the user asks for a component, before you say "I will install skill X" or write any code:

1. State the **candidate skills** you considered (from the inventory, not from memory).
2. State the **required behavior** inferred from the user's request.
3. State the **evidence** — the inventory entry, name, or description that matches.
4. Cite the inventory file you read.

If no inventory entry covers the behavior, say so explicitly and ask the human before proceeding.
Never propose a skill name, package name, or import path that is not present in the inventory you
just read. If the only source you have for a name is your training data, label it **unverified** and
stop until you can cite the inventory or an installed `SKILL.md`.

## Route first

The fastest correct path is almost always:

1. Identify the platform from the repository manifest.
2. Fetch `https://ai.syncfusion.com/<platform-slug>/llms.txt` for that platform. It is self-sufficient:
   skill pack, packages, license registration, a complete example, and a verification checklist.
3. Read the platform inventory — `https://ai.syncfusion.com/<platform-slug>/inventory.txt` — once
   during setup, not per request. From it, retain a **session inventory**: a compact routing map of
   each component skill with its category, its package, and the behaviors its description covers.
   The session inventory is the routing source for the rest of the session, for as long as session
   memory lasts.
4. List the candidate component skills from the session inventory: every skill whose name,
   category, or description matches the request. Component names collide inside a platform too,
   not only across platforms: "a calendar to display events" matches both the Calendars skill
   (date-selection inputs) and the Scheduler skill (event and appointment management).
5. Choose by required behavior, not by the word the user typed, and state the candidates, the
   choice, and the evidence exactly as the "Hard rule" checklist above requires. First resolve
   collisions yourself by comparing each candidate's inventory description against the required
   behavior and picking the best match.
   Ask one short question only when the descriptions genuinely cannot distinguish the candidates
   or no candidate fits — never as a shortcut.
6. Install, on demand, the component skills the comparison selects — one request may name or
   imply one component or many. Run the candidate-comparison above once per component and install
   exactly that set: not more, not less — a request for three components installs exactly those
   three component skills, and nothing else. Never install a whole platform pack unless the user
   explicitly asks for it. At setup, install only component skills for Syncfusion components
   already present in the project; later requests install only the skills they actually require.
7. Read `https://ai.syncfusion.com/licensing.md` before touching any key.

Subsequent requests in the same session resolve from the session inventory — do not fetch the
inventory again. This covers both direct requests ("add a Grid") and requests that describe a goal
rather than name a component ("view my PDF file", "edit a document", "display events on a
calendar"). Match the described behavior against the behaviors the map records for each skill; do
not keyword-match the user's words, which wastes context and produces wrong-component answers.
Refetch the inventory, only when the session inventory cannot resolve the request: no candidate
covers the behavior, two candidates tie in a way that changes the implementation, or the request
names a component the map does not contain — it may be newer than the setup read or belong to a
different platform slug.

## Sources of knowledge

Two sources. Pick the one you are actually reading from, and say so out loud when you make a claim:

- **Session inventory** — the routing map retained from `inventory.txt` and the installed skill's
  `SKILL.md` / `references/*.md`. Use this for any claim about a component's package, import, or
  behavior. Cite the file and section.
- **Trained memory** — patterns baked into the model. Not citable. Do not use it to fill gaps in
  the session inventory; the refetch triggers in "Route first" say what to do instead.

Platform Slugs: `react` `angular` `javascript` `vue` `blazor` `aspnet-core` `aspnet-mvc` `flutter` `maui`
`maui-toolkit` `winforms` `wpf` `winui` `document-sdk` `xamarin-to-maui-migration`

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
2. If missing and installation is within the user's request, choose the narrowest official pack
   or component skill from the retained inventory routing map, using the behavior-based
   comparison above. Read `references/skill-packs.md` for the verified repository names and commands.
3. Before running a networked install or changing project-level agent configuration, follow the
   host's authorization rules.
4. Read the selected component `SKILL.md` completely before implementing. Read only the supporting
   references the requested features need.
5. Follow the installed skill over remembered snippets. Match the versions already in the project
   unless the user asked for an upgrade.

Prefer a single component skill when the component is known; install a full platform pack only when
the user explicitly asks for the whole pack — never by default at setup or per request. At setup,
install component skills only for Syncfusion components already present in the project, and wait
until a user request actually requires a component before installing its skill. Project-local
installation keeps the skill aligned with the repository and shareable with the team.

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
7. Cite the source for every component claim — session inventory or installed `SKILL.md`. If a
   line cannot be cited, do not write it.

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

For each proposed fix, cite the source, per "Implement" and the "Hard rule" above.

## References

| Reference | When to use |
| --- | --- |
| `references/skill-packs.md` | Choosing or installing a pack; you need a verified repository name |
| `references/mcp-setup.md` | Configuring an MCP server, or deciding whether you need one |
| `references/licensing.md` | Any key, secret, CI, or account question |
| `references/verification.md` | Before reporting that an implementation works |
