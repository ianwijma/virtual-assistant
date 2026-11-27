I'm planning a new desktop application and need you to research it and write an engineering specification for it. The requirements below are everything I've decided so far. Where they leave a technical choice open, research the options and recommend one, with your reasoning.

## What I'm building

I want to change how the Linux desktop works through a single application that acts as the central hub of the computer. I'm deliberately leaving the exact shape open, but the experience I'm after is what I get on my iPhone or Pixel. For example, when an email or notification arrives containing a login code, the system notices and offers to copy the code so I can paste it straight away.

The application is part launcher, part notification centre, and more:

- **Launcher:** like Raycast or Alfred. I open it with a hotkey, launch applications, and reach everything else from it.
- **Clipboard manager:** built in, as in many launchers.
- **Notifications:** it is reactive. When a notification arrives, I can interact with it from the hub: reply, archive, and so on. It is fine if the hub replaces the current notification daemon, but ideally it builds on top of the existing one.
- **Email:** I want to read emails inside the application. For anything beyond reading, it should open my email application.
- **Window control:** it should be able to control the windows of other applications.
- **AI:** baked in, for things like summarizing emails. I want to use my Claude Code and Codex CLI subscriptions rather than pay API costs. Ollama and OpenRouter must also be supported from day one, so that all major models are covered.

## Hard requirements

### Speed
Speed is the key property of this application; it is for power users. It must start fast, and everything we control must feel snappy. Only AI calls, asynchronous work, and anything that depends on something external may take longer. The spec should define what "snappy" means in measurable terms, and it should include speed and latency tests that stop the application from getting slower over time.

### Scale
The UI must handle hundreds of thousands of items, such as months or years of clipboard history, while search stays snappy. I know this is tricky, so treat it as a central design problem.

### Rich clipboard items
Each clipboard item should have a rich representation of what was copied. If I copy HTML, it should ideally be rendered, in a secure way.

### Clipboard restore
From my experience, restoring the clipboard is not instant. It must never block the source application, and the user must be told when the clipboard has been restored. State how you interpret "restore" and design for it.

### Platforms
- It must run on Linux. macOS is ideal as a second platform, and Windows is an afterthought.
- On Linux it must be desktop-agnostic and run on most desktops.
- My own machine runs an older Pop!_OS, the version before the COSMIC desktop. Don't assume COSMIC.

### Language
Rust, for speed.

### A2UI for building UI
I want to use A2UI (https://a2ui.org/) as part of this project, for two purposes:

- **Building UI quickly:** we describe the application's own UIs with A2UI instead of hand-writing each screen, so that new screens and modules are fast to build.
- **AI-created UI:** the built-in AI can create UIs on the fly, for example a custom view that answers a request, rendered natively in the application.

Design how A2UI fits into the application, and say where it should and should not be used. In particular, resolve these points:

- **Speed:** UI that we build ourselves with A2UI must still meet the speed and scale requirements, including lists with hundreds of thousands of items. AI-created UI may take longer to arrive, but must render smoothly once it does.
- **Catalog:** A2UI restricts an agent to a catalog of registered components. Define the catalog for this application, and how a module adds its own components and functions to it.
- **Themes:** A2UI surfaces must follow the selected design language, like the rest of the UI.
- **Shortcuts:** actions inside A2UI surfaces must work with the keyboard shortcut system.
- **Security:** AI-created UI can be influenced by untrusted content such as emails and notifications. Define what a generated surface is allowed to do.
- **All AI providers:** UI generation must work with Claude Code, Codex, Ollama and OpenRouter, or the spec must say which providers can do it and why the others can't.

### Modularity
- Adding a new module, with its functionality, must be trivial.
- People extend the application by forking the repository and adding their own modules.
- I don't want to build a plugin system unless it is easy to do. An internal module system is what I want.

### Keyboard shortcuts
Users must be able to assign keyboard shortcuts flexibly to the functionality inside modules.

### Flexible, themeable UI
- All the UI, including the launcher, should be as flexible as possible.
- By default the design should mimic the desktop it runs on.
- The user can pick a different design language, for example the macOS or Windows style while on Linux.

### No configuration hell
- There must be UI for every setting.
- I want a macOS-style settings window: groups of settings on the left, and a clean UI for the selected group on the right.

### First-run setup
- The first run needs a light setup.
- It should cover only the options that really benefit from a setup phase, not all of them.
- As much as possible should be inferred from the environment the application is running in.

### Build on existing technology
At every step, build on existing technologies as much as possible, but only well-established ones. There are two exceptions to the "well-established" test:

- **A2UI itself**, which is a deliberate choice of mine.
- **Rust libraries for brand-new technologies.** When a technology is new, as A2UI is, its Rust libraries will be new too. A young library for such a technology is acceptable, under the rule below.

### Contributing to and creating Rust libraries
Where a library we need is missing or incomplete, we do the work ourselves, in this order of preference:

1. **Contribute to an existing library.** If a Rust library already exists for the need, we use it and contribute what is missing. This includes brand-new, immature libraries. For example, if someone has already started a Rust library for A2UI, I want us to contribute to it, not write a competing one.
2. **Create a new library.** This is allowed only when no Rust library exists for the need, or when the existing one can't realistically be contributed to (for example, it is abandoned, its maintainers reject the changes, or its design conflicts with our requirements). The spec must give that reason.

A2UI is the likely first case, since I don't think it has a Rust library yet.

For every library the spec proposes to contribute to or create, it should state:

- what search was done, and what existing libraries it found, including young ones;
- for an existing library: its state (maintainers, activity, licence, completeness), what we would contribute, and what we do if the contributions are not accepted;
- for a new library: why contributing to something existing is not possible;
- the scope of the library, kept separate from the application so that others can use it;
- the extra effort it adds, and which phase it belongs to.

## What to research

Check the current state of anything that changes over time rather than relying on memory. In particular:

- **A2UI in a Rust application.** As of November 2026, the A2UI site lists v1.0 as the current specification. It lists official renderers for React, Lit, Angular, Flutter, SwiftUI and Jetpack Compose, and official core and agent SDKs in TypeScript, Python, Dart, Swift and Kotlin. I found no Rust core, agent SDK or renderer listed there, official or community. The site says a new-language implementation should follow the specifications in `blueprints/modules` and verify against the `conformance` suites in the A2UI repository. Verify all of this, and search thoroughly (crates.io, GitHub, the A2UI repository's issues and pull requests) for any Rust implementation, however early. Then compare the realistic options, such as:
  - contributing to an existing Rust implementation, if one is found;
  - writing a Rust core and a renderer for the chosen Rust UI toolkit, as a reusable library;
  - embedding an existing renderer, for example a web renderer in a webview.

  Weigh each option against the speed, scale, theming and desktop-agnostic requirements. Also find out whether the A2UI project would accept a Rust implementation as a contribution or list it as a community implementation.
- **A2UI for local, non-agent UI.** A2UI is designed for an agent streaming UI to a renderer. Work out whether it suits UI that our own code defines locally, how that would work, and what it costs in latency.
- **A2UI generation through each AI provider.** Check which inference formats and agent SDK features (for example A2UI Express, catalog-driven prompt generation and output validation) we can use from Rust, and how they work when the model is reached through a CLI subprocess rather than an API.
- **Rust UI toolkits.** Which ones can meet the speed, scale, theming and desktop-agnostic requirements, and which is the best base for an A2UI renderer.
- **Missing and incomplete libraries.** For each part of the design, check whether a suitable Rust library exists, including new ones. List the gaps, and for each one apply the rule in "Contributing to and creating Rust libraries".
- **AI CLIs.** How the Claude Code and Codex CLIs can be driven non-interactively by another program, and whether their subscription terms allow that kind of use.
- **Desktop integration.** How notifications, clipboard access, global hotkeys and window control work across Linux desktops, on both X11 and Wayland, and what is possible on macOS and Windows.
- **Search.** How to keep search fast over years of history.
- **HTML.** How to render untrusted HTML safely.

Say which claims you verified and which are assumptions that still need a prototype to confirm.

## What to deliver

Write the specification as a principal engineer would. Senior and regular engineers should be able to build the whole application from start to finish using this document alone. It should include:

- the architecture and the main technical decisions, with reasons;
- how A2UI is integrated, including the catalog and the boundary between A2UI surfaces and hand-built UI;
- the list of Rust libraries to contribute to and new ones to create, with the details asked for above;
- the high-level tasks, organised into execution phases, with what needs to be done in each;
- the risks and open questions.

Return the whole specification as a single Markdown document inside one Markdown code block.
