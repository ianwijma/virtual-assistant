# Admin panel

The web application that configures the whole system. Part of
[the clients design](README.md).

Status: draft.

## What it is

A full single-page web application, served by the server. Everything the
server and the system do can be configured here. It is the place that
fulfils "a screen for every setting".

## What it holds

- People, roles and devices.
- Assistants: their identity, brain and abilities.
- The household AI configuration and the speech providers.
- A page for each [module](../modules/README.md), including the
  [feedback](../modules/feedback.md) reports.
- Each person's notification routing, which an admin can view and change.
- The log of summoning decisions, with the reason for each.
- The log of admin access to other people's data.

## How it is built

Rust compiled to WebAssembly, using Leptos.

Browsers need HTTPS. See [networking](../server/networking.md).

## Open questions

- Is the admin panel only for admins, or does every member use it for
  their own settings?
- Is first-run setup done here, and what does it cover?
- How a person signs in to it.
- Are settings screens generated from each module's description, as in
  the earlier voice assistant?
