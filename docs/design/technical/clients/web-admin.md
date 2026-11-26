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
- The AI providers and the speech providers.
- A page for each feature of the system, including the
  [feedback](../server/feedback.md) reports.
- Which [modules](../modules/README.md) each assistant has.
- Each person's notification routing, which an admin can view and change.
- The log of summoning decisions, with the reason for each.
- The log of admin access to other people's data.

## Who uses it

- **Every member can sign in** and manage their own settings and their
  own things.
- **An admin** manages their own, and also the household and the server.
- **At first it is the one place for a person's settings.** The phone
  app and the desktop client have a quick link that opens the admin panel
  already signed in, using the app's own sign-in, so nobody signs in
  twice. Settings that belong to one device, such as its keyboard
  shortcuts, stay on that device.

A person signs in with their email address and a one-time code sent to
it. The admin panel also holds
the settings of devices that have no settings screen of their own, such as
whether a tablet in kiosk mode listens for a wake word.

## First-run setup

A new server is set up here. Opening the server's address in a browser
starts the setup. It creates the first admin, names the household, and
sets the mail account for sign-in codes, the AI provider and speech.

The mail account is set first. The first admin then confirms their email
address with a code sent to it, like everyone else, which also proves the
mail account works.

## How it is built

Rust compiled to WebAssembly, using Leptos.

Browsers need HTTPS. See [networking](../server/networking.md).

## Open questions

None at the moment.
