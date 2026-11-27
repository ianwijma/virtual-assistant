# Linux Desktop Productivity Hub Specification
Created: 25/11/2026, 00:06:07\
Last Updated: 25/11/2026, 09:35:58

---

### User

Desktop: <see file>

Repo: https://github.com/ianwijma/personal-voice-assistance

So I've been working on a high-level idea where there's like a desktop assistant kind of idea. And we also have the personal voice assistant.

What if we have like a kind of personal virtual assistant or something that integrates with both the existing two systems or the existing idea, which we have for the desktop assistant, but also the personal voice? What if we turn this into a kind of personal assistant that does kind of everything that personal voice assistant does, but also integrates with desktop and email and has multi-user support?

So if I have a user, I can assign my own email and stuff, and it will route it to the correct person. Of course, a bit like the personal voice assistant, we also have actual web browsers that can have multiple integrations. So here we might need to do either some voice recognition or some passcode or some redirection or something. I don't know how this would work. Kind of set up.

This allows you to have like a personal virtual assistant kind of system that has a voice but also is able to integrate with your desktops and your desktop notifications and the like. I would like to pair on this a bit a little bit of and see what existing things are out there that align up with our kind of nature of modularity and ease of change.

[desktop-assistant.md](https://upoevdcxa3.ufs.sh/f/IN4OjmY4wMHBNHxRD6qI20ogSb9QuZb2fpKtkYnmATx3rLOPdaNViQ7IlfxhazNMMY)

---

### Assistant (claude-fable-5.2)

<details>
<summary>Reasoning</summary>

I'm going to look at the repo link the user included, since the main request is to pair on merging a desktop assistant and a voice assistant into one multi-user system and find existing projects that fit a modular design.

I'm now searching for existing projects such as Home Assistant Assist, OpenVoiceOS, Rhasspy/Wyoming, Leon, and Mycroft, and looking into speaker identification for multi-user support. I'll run a single search with the URLs and queries, keeping the effort modest.


</details>

<details>
<summary>Reasoning</summary>

I'm putting together a pairing response that stays concise. The repo is TypeScript/Effect and the desktop assistant is in Rust, so I'm sketching an architecture where the PVA acts as the hub and the desktop becomes a device client, with identity based on device ownership, speaker ID, and a fallback.

I'm noting that the desktop spec is just context, and that the real ask is the pairing design. I'll ask a few clarifying questions at the end. From the README, the repo already has devices, voice nodes, presence, reminders scoped to a household or one person, and a vault, so some notion of persons exists, though I'm inferring that and don't know the details. I'll keep the answer compact.


</details>

I read the desktop brief as context and your repo's README (not the code), and looked at what already exists in this space. My short take: don't merge the two projects, make the voice assistant the household "brain" and the desktop hub one of its devices.

## Proposed shape

- **Server (your existing PVA, TypeScript/Effect):** owns users, assistants, modules, the vault and routing. It already has devices, voice nodes, multiple assistants and per-person reminders, so multi-user is an extension rather than a rewrite.
- **Desktop hub (the Rust app):** stays a fast, local-first launcher that works with no server. When paired, it acts as a device that pushes events up (notifications, email arrivals) and exposes capabilities down (window control, clipboard, show a surface).
- **Rule to keep:** nothing on the desktop's hot path (launcher, clipboard search) may depend on the server, or you lose the speed requirement.

## Multi-user identity

The "who is talking" problem resolves in layers, cheapest first:

1. **Device ownership:** a desktop or phone is paired to one user, so no recognition is needed. This covers most of the desktop and email cases.
2. **Speaker ID on shared devices:** a voice node in the kitchen embeds the utterance and matches it against enrolled voiceprints. Unknown or uncertain voices are treated as a guest.
3. **Step-up for sensitive actions:** reading email aloud or sending something needs confirmation on the user's own device, or a PIN.

Every project I found says the same thing: speaker ID is convenience, not security, because a voice can be recorded and replayed. So it should pick whose calendar to read, but never be the only gate on email.

## Existing work worth borrowing from

| Project | What to take | Caveat |
|---|---|---|
| [OpenClaw](https://hackmd.io/Z39YLHZoTxa7YLu_PmEkiA) | Gateway plus device "nodes" over one WebSocket, pairing, declarative bindings that route by account to isolated agents, per-agent tool policy | Built for one person; multi-user is added on |
| [OpenVoiceOS](https://github.com/OpenVoiceOS/architecture) | Written bus and session contracts, so parts are swappable | Its GUI layer is deprecated |
| [assist-speaker-id](https://github.com/witold-gren/home-assistant-assist-speaker-id) | Speaker ID with sherpa-onnx (which you already use), per-person threshold plus margin, a "probable speaker" tier, guided enrollment | Very new, 3 stars |
| [Renfild](https://github.com/t0mer/renfild) | A minimum role per intent (any, kid, member, owner) and an unknown-voice policy | Brand new, no users yet |
| [Yorik](https://yorik.ai/) and [LIA](https://github.com/jgouviergmail/LIA-Assistant) | Household model: per-user connectors, memory and role-gated data | Both AGPL web apps, so borrow ideas rather than code |
| [Chatter](https://github.com/NikitaCherepov/chatter) | Backend plus desktop client pairing by access key, confirmation before PC actions | Electron, early |

None of these combines a fast native desktop hub with a multi-user voice backend, so there is nothing to adopt wholesale. The closest architectural fit for your modularity goal is OpenClaw's gateway and node model, with speaker ID done the sherpa-onnx way.

## Questions that decide the design

1. Is this household-scale (a few trusted people on a LAN), or should users be isolated from each other as if they were strangers?
2. Should email credentials live on the server (so voice nodes can read mail when the desktop is off) or only on each user's desktop?
3. Are you happy with two languages joined by a protocol (TypeScript server, Rust desktop), or do you want to converge on one?
4. You mentioned web browsers with multiple integrations: do you mean one shared browser or tablet that several people use, or each person's own browser?

If you answer those, I can sketch the device protocol and the user and routing model next. The full desktop engineering spec from the brief is a separate, large piece of work; say the word and I'll do it with this pairing design folded in.


---

### User

What I want to do here is not have the two separates. I want to have one system that is called a virtual assistant, which uses the local server for multi-device management. And then the desktop client will be an extension of it that syncs over email notifications and stuff. You should also be able to configure it. For example, if I receive an email, I could also choose to get a notification on a device from PVA, personal voice assistant. Well, now personal voice assistant, right? So, yeah, I really want to have this as one system, not two separate parts.

The desktop hub could choose to be local. Also some functionality, obviously, like clipboard management stuff, we could choose to be local, but we could also make it into like an Apple kind of system where if I copy something on one device, the whole copy clipboard is being copied over to, let's say, my iPhone or something or another device or another desktop client or something. We could choose to do that as well, right? So I really want to become like a one system, not having several separate systems.

Obviously, they kind of need to work separately. For example, the desktop app potentially has some functionality that we could choose to keep separately. But I want you to keep also in mind that the server is run locally. It's not somewhere in the cloud. It is on a box locally installed. So we have a really fast connection to it. So offloading things to it doesn't require, is quick and it's local. But also we don't require internet for it because it's all on the local network. I want you to keep this in mind. 

Also, the desktop path, indeed, we want to have it depend on the server, but it's not allowed to be blocked by the server. So let's say we copy something, we first do it local and then quickly sync it to the server. Again, it's local, so it's fast, but the desktop client needs to be faster, of course. Again, think the Apple ecosystem At local and self-owned. Excluding the AI agents for now, but we could also choose to integrate with Ollama, which means everything is local.


---

### Assistant (claude-fable-5.2)

<details>
<summary>Reasoning</summary>

I'm settling on one unified system here, with a local server as the hub and the desktop app acting as a client. The user wants to work through this together, so I plan to give a concise revised design that leans on local-first sync, and I'll finish by asking the decisions still open.

I'm working out the hub-and-client split in more detail: the server holds shared state and the devices sync through a local outbox, so the server is never on the hot path. I'm also sorting data into device-local, synced, and server-owned buckets, and noting that email credentials likely belong on the server, which I'll flag as a recommendation.

I'm noting that mobile clipboard access is restricted, since iOS and recent Android versions don't allow background reads, so phone support would need a share sheet, shortcut, or keyboard route, and I should say that plainly. I'm also checking the sync model: an append-only event log with cursors over one WebSocket should cover most cases, with last-writer-wins for settings, so no CRDT is needed. On language, a single protocol schema could generate both the TypeScript and Rust types. Last, I'm weighing the security side of LAN use, with device pairing, TLS, and per-device keys, and deciding what happens when the laptop leaves home and the server becomes unreachable.


</details>

That works, and it simplifies things: one system, where the server is the hub and every client (desktop, voice node, phone, browser) is a device of it.

## What "one system" means

- **One identity model:** users, devices and pairing live on the server. A desktop is simply a device owned by a user.
- **One protocol:** every device holds a single WebSocket to the server, with one schema that generates both the TypeScript and Rust types. This is how the system stays one even with two languages.
- **One module system:** a module (email, clipboard, notifications, reminders) has a server part and optional client parts, declared together.
- **One configuration:** settings are stored on the server and editable from any client, including the desktop settings window.

## Local first, then sync

Every desktop action follows the same path, so the server is never on the hot path:

1. Write to the local store and update the UI immediately.
2. Put the change in a local outbox.
3. Sync the outbox to the server in the background, usually within milliseconds on the LAN.
4. If the server is unreachable, the outbox waits and drains when the connection returns.

For the sync itself, I'd use a per-user append-only event log with sequence numbers, where each device remembers its cursor and catches up from there. Almost all of this data is append-only (clipboard items, notifications, emails), so there are few conflicts. Settings can use last-writer-wins.

## Where each thing lives

| Data | Lives | Notes |
|---|---|---|
| Hotkeys, window control, launcher index | Desktop only | Device-specific by nature |
| Clipboard | Desktop first, synced | Newest item is pushed to your other devices; history and large blobs are fetched on demand |
| Notifications | Desktop first, synced | Dismissing on one device dismisses everywhere |
| Email | Server fetches, desktop caches | Reading and search hit the local cache |
| Users, routing rules, credentials | Server | Clients keep a read-only copy |

I recommend putting the email accounts on the server. It is always on, so your "email arrives, announce it on a voice node" case works even when the desktop is off.

## Routing

Your email example becomes a general rule engine on the server: event, then per-user rule, then target devices. For example, "email from X for Ian: notify the desktop if it is active, otherwise speak on the kitchen node". Desktop notifications feed the same engine, so they can be forwarded too.

## Two caveats

- **Phone clipboard:** iOS and Android don't let an app read the clipboard in the background. Desktop to desktop can be automatic, but on a phone it will need a share-sheet action, shortcut or keyboard.
- **Sensitive clips:** password-manager copies should be excluded from sync by default, with sync as a per-device opt-in.

## Questions still open

1. **Trust:** are household members trusted, or must the server isolate users from each other? This is still the biggest design decision.
2. **Away from home:** when a laptop leaves the LAN, is it offline-only until it returns, or should it reach the server over a VPN such as WireGuard or Tailscale?
3. **Languages:** are you fine with a TypeScript server and Rust desktop joined by the shared schema?
4. **Phone:** is a phone client in scope now, or is it desktops and voice nodes first?

Once you answer these, I can draft the device protocol and the event log schema.


---

### User

Notifications, I don't think, needs to be desktop-first because, if we have as much of stuff on the server, a notification can just simply be pushed to a desktop or a node or a phone app in the future. You know, like, think, think, think local-first. Um, again, server is local and fast.


---

### Assistant (claude-fable-5.2)

<details>
<summary>Reasoning</summary>

I'm weighing the user's correction that notifications should be server-first, since that's a fair point. The one thing I want to keep distinct is where a notification starts: ones from local desktop apps necessarily begin on the desktop, while email, reminders, and calendar alerts begin on the server and get pushed out. Desktop captures get forwarded to the server, which acts as the single store, so

I'm noting that the desktop still shows its own app popups right away, since it has to act as the notification daemon, while the server holds the record of truth. I'll treat the server as the default source, keeping the desktop for things that need it directly like clipboard capture, launcher search, and hotkeys. Offline, local notifications still appear and server-side ones wait in the queue. Trust, being away from home, languages, and the phone still need answers.


</details>

Agreed: the server is the notification centre, and the desktop is just one of the places it delivers to.

## Notifications, server-first

- **One store:** every notification lives on the server, per user, with its state (unread, dismissed, replied).
- **One delivery path:** the routing rules decide which devices get it: a desktop popup, a voice node announcement, or a phone push later.
- **State is shared:** dismissing or replying on any device updates the server, and every other device follows.
- **Server-side sources** (email, reminders, calendar, the assistant itself) never touch the desktop until they are delivered.

One case starts on the desktop by nature: notifications from local apps (Slack, a browser, a finished build) arrive over the desktop's own notification bus. The desktop is then a *source*: it shows the popup immediately, because it is the notification daemon and can't wait, and forwards the notification to the server. From there it is treated like any other, so it can be routed to other devices and kept in history.

If the server is unreachable, local app notifications still pop up and queue for upload, and server-originated ones wait on the server until the desktop reconnects.

## The rule this gives us

The server is the default home for everything. Something lives on the desktop only if it is physically tied to that machine or needs to respond within a frame.

| Data | Lives | Why |
|---|---|---|
| Users, rules, credentials, settings | Server | Shared by all devices |
| Notifications | Server | Desktop is a source and a display |
| Email | Server | Desktop keeps a cache for instant reading and search |
| Clipboard | Captured on desktop, stored on server | Capture and paste must be instant; the desktop keeps a local index for search |
| Launcher index, hotkeys, window control | Desktop | Tied to the machine |

The desktop's cache of server data means the hub still opens and searches instantly, and keeps working in read-only mode if the server is down.

## Still open

1. **Trust:** are household members trusted, or must the server isolate users from each other?
2. **Away from home:** is a laptop offline-only off the LAN, or does it reach the server over a VPN?
3. **Languages:** are you fine with a TypeScript server and a Rust desktop joined by a shared schema?
4. **Phone:** is a phone client in scope now, or later?

The first and third shape the protocol most. With those answered, I can draft the device protocol and the event log schema.


---

### User

I'm not answering the still open question. Trust. Are household members trusted? What do we mean by trusted? In my opinion, you should be able to configure which household members are like adults and which are, or maybe admins, I think is a better way, and which ones are not. Isolated users, it depends on how the connection is.

For example, me and my partner, I am okay with sharing most of my emails, but potentially also not in case I buy a birthday present. So I might choose to keep my email separate, but I might choose to keep some other things together. 

Open question: away from home, a laptop is offline. Only server with a VPN. This is a great question. We could potentially do something with Tailscale. I think having Tailscale set up on the devices, if they want to be able to reach their private stuff outside of the network, they could install Tailscale. But by default, it's home only. Keep stuff in house if they choose. So we can go outside of it, but it requires them to use Tailscale. Or maybe we can provide—I don't know if Tailscale has an SDK—we could potentially integrate this as well, which means we can own the also connectedness with external devices. But yeah, by default, local only. But we could provide Tailscale as a solution to reach the server outside of it. 

Open question: two languages. You find with TypeScript server and a Rust desktop, joined by a shared schema. I kind of want to have a mono repo with one language. Currently, we indeed have a TypeScript server and a Rust desktop client. This focus is gonna be a unified angle, so we can choose to go with one language, which could be Rust, which I think we should aim for. This also allows us to create smaller binaries. And also allow us to target a broader target. Like we can have a small device with low amount of storage. Yeah. 

Open question for phone. Is a phone client in scope now or later? I think it's quite similar to the desktop client. I think it's good to have a phone client as well. But if we could, I do think it should be part of the initial scope. 

So kind of the scope we will have is desktop, phone, and web. And this will allow us, well, phones should also be tablets, because my idea of nodes would be a second-hand tablet, either an iPad or a Samsung tablet, which you could set up as a node, and you can activate it using a voice, let's say, hey, blah, and you activate it that way.


---

### Assistant (claude-fable-5.2)

<details>
<summary>Reasoning</summary>

I've got the user's answers to the open questions, so I'll turn them into design updates on the trust model (roles and sharing) and the Tailscale integration. Since Tailscale's embedding options have changed over time, I want to check whether there's a usable SDK, such as tsnet for Go or a Rust binding, before settling on anything. I also need to weigh how a single Rust codebase covers desktop, phone, web, and tablet, since that shapes the UI toolkit choice, and how wake-word detection would work on tablets in the browser or app.

I'm going to look up whether Tailscale's embedding options and any Rust mobile UI toolkits have changed recently, so I can check the current state before settling on those choices.


</details>

<details>
<summary>Reasoning</summary>

I'm pulling together the key facts now. Tailscale's official tailscale-rs is BSD-3 licensed, at v0.7.1 as of 2026-11-06, still pre-1.0 with no iOS or Android support, no MagicDNS, and no compatibility guarantees, though its ts_tunnel cryptography got a security audit at 0.6.0. For self-hosted control I'm considering Headscale at v0.29.7, so I'm working out how to answer whether Tailscale has

I'm weighing whether to rely on the Tailscale app on devices for v1, with tsnet, libtailscale, and tailscale-rs as SDK options for later embedding. Phones can't embed tailscale-rs yet, so they'd use the app there. Headscale stays optional, though it would need to be publicly reachable, which sits awkwardly with a home-hosted box.

I'm weighing Slint as the leading toolkit candidate since it's the only native option with documented desktop, Android, iOS, and web paths, with Dioxus as a fallback, but I'd need to prototype its iOS and web maturity and how it handles a 100k-item list before committing.

I'm checking Slint's documented mobile and web paths against the tablet requirements, and I'm noting that the mobile claims are documentation rather than measured results. Next I'm looking at how wake-word detection could run on tablets: Android can keep a foreground service listening, iOS gives less room in the background, and a browser-based version would need the page visible and a secure context, which is awkward on a LAN.

I'm thinking about the tablet side now: old second-hand iPads can't run current iOS, though Android 8 and later should be fine, and a browser fallback for older devices would need HTTPS for the microphone, which means the server needs its own certificate setup. For access control, I'm considering roles like admin, member, and child or guest, with every resource owned by a user or the household, personal items like email private by default, and shared items like the shopping list shared by default. I also need to face the fact that the box's admin could read everything unless data is encrypted per user.

I'm weighing how the admin role should be limited: it can manage users and devices, but the UI won't expose their data. Truly blocking an admin who has root on the box would need per-user encryption keys, which would break server-side features like announcing mail when that user isn't present, so I'd enforce this at the policy level with an audit log and not promise cryptographic isolation in v1. I also need to ask whether that tradeoff is acceptable. On shared voice devices, the kitchen node shouldn't read private email aloud, so delivery there should only cover household-shared items or a generic "you have new email" notice. Finally, the language choice means a Rust monorepo, so the existing TypeScript/Effect server would have to be ported, which I'm flagging as a real cost since I've only read the README.

I'm settling the remaining details: how sherpa-onnx's Rust API keeps the voice stack portable, a Cargo workspace layout, and a shared protocol crate built from serde types instead of generated schemas.

I'm noting that Headscale means exposing a port or a small VPS for the coordination server, while Tailscale's hosted control is cloud coordination only, with traffic end-to-end encrypted over peer-to-peer links or DERP relays.


</details>

Your answers settle the shape: one Rust monorepo, with a household server and desktop, phone, tablet and web clients. I checked Tailscale, cross-platform Rust UI toolkits and tablet wake words; the phone and web scope reopens the UI toolkit choice.

## Trust: roles plus sharing

- **Roles:** admin (manages users, devices and modules), member, and a restricted role for children and guests.
- **Ownership:** everything belongs to one user or to the household. Personal connectors such as email start private, and household items such as timers and shopping lists start shared.
- **Grants:** you share a whole source with a person, for example "my inbox to my partner", with exceptions by rule or per item. The birthday present is a "keep private" rule on a sender, or a flag on one email.
- **Shared devices:** a kitchen node only speaks content that everyone in the household may hear. Otherwise it says "Ian, you have a new email" and the content stays on your own devices.

An admin has root on the box, so privacy from the admin is policy plus an audit log, not cryptography. Per-user encryption would stop the server from reading mail to announce it, so I would not promise it in v1.

## Away from home: Tailscale

Tailscale does have an SDK, and now a Rust one:

- **[tailscale-rs](https://github.com/tailscale/tailscale-rs/):** the official Rust library, which embeds a Tailscale node in your program. It is at 0.7.1 (6 November 2026) and pre-1.0 with no compatibility guarantees.
- **Platforms:** Linux, macOS and Windows only. Android and iOS are not supported, and neither is MagicDNS.
- **[Headscale](https://github.com/juanfont/headscale/):** a self-hosted control server, if you want to own coordination too. It normally needs a publicly reachable address, so it is not purely in-house.

I recommend three steps:

1. **Default:** LAN only.
2. **Opt-in, v1:** the user installs the normal Tailscale app, and the server also listens on the tailnet address. This needs no code from us beyond pairing by address, and it works on phones.
3. **Later:** embed tailscale-rs in the server and desktop so remote access is a toggle in settings. Phones keep using the app until the library supports them.

With Tailscale's hosted service, coordination goes through their cloud. Your data stays end-to-end encrypted between your devices.

## One language: Rust

The shared schema becomes a plain Rust crate that every binary imports, so there is no code generation. The cost is porting the existing TypeScript server. I have only read its README, so I can't size that yet. sherpa-onnx has a Rust API and runs on Android and iOS, so the voice stack carries over.

```text
crates/
  protocol/   # events, device messages, shared types
  core/       # users, grants, routing rules, event log
  modules/    # email, clipboard, notifications, reminders
  voice/      # wake word, speaker ID, STT, TTS (sherpa-onnx)
  ui/         # shared screens and A2UI renderer
apps/
  server/  desktop/  mobile/  web/  node/
```

## Clients: the toolkit question reopens

Desktop, phone, tablet and web from one Rust codebase narrows the options:

| Toolkit | Covers | Problem |
|---|---|---|
| Slint | Desktop, Android, iOS, web, embedded | Own markup language; GPL, royalty-free with attribution, or paid licence |
| Dioxus | Web, desktop, mobile | Desktop and mobile run in a webview; its native renderer is pre-alpha |
| Tauri | Desktop, Android, iOS | Webview, and the UI is written in web tech, not Rust |
| egui | Desktop, web, Android | No official iOS |
| GPUI | Desktop | No mobile or web |

Slint is my leading candidate, because it is the only native one with a documented path to every target. This is not proven: the [comparison I found](https://goldstrikearch.github.io/rust-gui-desktop-ecosystem-state/) measured desktop only, so mobile and web support are upstream claims. It needs a prototype of the hardest screen (the 100,000-item clipboard list) on desktop, one phone and the web before we commit.

## Tablets as voice nodes

- **Android:** a native app can listen for the wake word continuously, even with the screen off. Existing apps such as [DashVoice](https://github.com/ecohash-co/dash-voice/blob/25bf2637/README.md) already do this on second-hand tablets.
- **iPad:** listening works while the app is open or in background audio mode, but not after a force-quit. In practice it is a kiosk app kept in the foreground.
- **Browser:** in-page wake word detection works, but only while the page is visible. Browsers also require HTTPS for the microphone, so the server would need a local certificate.

A tablet node should therefore be the native app in a kiosk mode, with the browser as a fallback for devices too old for the app.

## Decisions I need from you

1. **Admin privacy:** is policy plus an audit log enough, or do you need data the admin cannot read at all?
2. **Web client:** is it a full client, or a lighter one for settings, reading and a fallback node? A lighter one makes the toolkit choice much easier.
3. **Toolkit prototype:** shall I write the plan for the Slint prototype, with Dioxus as the fallback?

With those answered, I can draft the device protocol, the event log and the grants model.


---

### User

I am going over the document right now from top to bottom:

Looking at trust, I think by default we should do the opposite. We should not share whole sources by default. We should be private by default and share what we want to share. 

Share devices to catch a note on the speak. I like that it says you have a new email and Nothing else. 

Tillscale RS, is that a Tillscale node? Is that like a client? Because let's say if we could build our, if there's no SDK for Android and iOS, could we build our phone apps using Rust and using the Tillscale RS library to kind of still enable Rust support on a device? Or does this library really depend on the desktop clients?

I think indeed by default we support LAN only, but I think what I want to have for now is have Tillskill support from day one, at least on the server and desktop, and on phones if you can use the Tillskill RS library also on the phone by using the Tillskill by building our apps, phone apps using Rust, that will be great as well.

Like we want to have ideally from day one a great experience in home or potentially out of home. Default LAN only is a good way to do because by default we want to be secure. 

One language: Rust. I like it. Let's go for it. Though for the web, if you could use Rust as well, that would be great. But I also understand for an admin UI, we could use Rust as well, ideally. But if we need to use some web technologies, that's also fine. 

Client toolkits, good question. We might want to do some experimentation on this. I see there are some cross-platform toolkits like Schlint that works on all devices that we want to possibly target, which is great.

Potentially that is our choice, but I'm happy to discuss this further. 

Tablets as voice notes. Oh, I did not know we have in-page voice wake word detection in browsers. So I think for at least Android and iPads, we would have the devices with the app running 24-7.

But we could implement our own where it turns the screen black in the app so we at least save some power using the app while it's still running. Maybe we could introduce a low power mode for it, but we're kind of banking on the fact that if we turn the screen black or kind of off and dim it while we're like still listening for, while the app is still running, that will be the way to go for browsers.

Yeah, it's PS for microphone, that's fine. I think for browsers, we will have a, I don't know, URL where you can host it on. I'm not sure how we want to do deployment. Ideally, people can deploy this easily themselves, or maybe you could.

But yeah, we will expect people to have this thing running on some sort of HTTPS enabled web page. So we need to have certificates set up for this. 

Decisions made for you. Number one: admin policy, policy plus an audit log. Enough, or do we need to have some data the admin cannot read at all? In my opinion, if you're an admin, you can read all data. But I can understand that we want to keep some data private. I think this should be a setting. In my opinion, it should be public by default, so the person who deploys this kind of owns the network and everything it goes through. So in my opinion, they should be able to read all data. For now, we could work on improving this in the future, but I think that's good to have it admin is able to be able to see everything for now. 

To web client, it's a full web client, a lighter one with settings, reading, fallback note. The web clients, I think there's multiple. We have maybe an admin panel that is a fully flashed kind of single-page application where the user is able to configure everything, everything that the server does or the whole system does, really. And there's a second one, which is the voice assistant, which is like a lighter one that just does the voice relay. It does the in-page wake word detection, which is apparently a thing. Maybe we can even make it lighter where it continuously streams to the server and the server decides when it needs to wake up. But yeah, we will basically have two web clients: an admin one and basically a voice assistant one. Yeah. 

Decisions are needed from you to get prototypes around. Small plan for the sling prototype with Doxys as fallback. This is quite tricky. I don't know what would be the best for each framework, because I also personally do notary, which is a web view. We basically want to pick whatever is best for the platform. If Slint is the best for mobile but terrible for desktop, we don't want to pick Slint. Our main focus is integration with the platform, but also speed, just so we can do everything we want to do on that platform. 

If we decide that Rust might not be our language of choice for the platform, we might be able to choose to not use Rust. For example, if we decide that Swift for iOS is much better, we might be able to use Swift instead for that platform.

But we do need to keep in mind everything needs to be in one mono repo, and we need to make sure that if we pick another language, we are certain it's the right choice to make. What I mean by this, let's say if we need to have keyboard integration, and that simply is not possible with Rust, but it is possible with Swift, for whatever reason, we pick Swift. Because we do want to make sure that we have the best integration with the platform as possible. But we want to heavily lean towards Rust if possible, because in my opinion, it's the language of the future.


---

### Assistant (claude-fable-5.2)

<details>
<summary>Reasoning</summary>

I'm sorting through the user's answers on trust defaults, phone support for tailscale-rs, the web side in Rust, per-platform toolkits, tablet power modes, HTTPS deployment, admin access, and the two web clients. I'm also rechecking my earlier claim that Android and iOS aren't supported, since the user is asking whether Rust phone apps could use tailscale-rs.

I'm weighing whether to check the facts before answering, specifically whether the limit on phone support comes from tailscale-rs or from the platforms themselves. A search on tailscale-rs mobile support, Slint on iOS and Android, and LAN HTTPS certificates would settle it in one call.


</details>

<details>
<summary>Reasoning</summary>

I'm settling on a default where everything stays private, with sharing being a deliberate choice the user makes at whatever level they want, whether a single item, a rule or label, or a whole source. Admin access to everything still needs reconciling, so I'm leaning toward an logged admin override, and I'm wondering whether this should be a setting.

I'm weighing whether the Tailscale option could run inside a phone app. The tailscale-rs library embeds a node in the program itself, but it currently lists Android and iOS as unsupported, so building in Rust alone won't get us there. libtailscale, linked through FFI, looks like the route that works on phones, though it's unverified and would need a prototype, and it adds about 20 MB plus a Go runtime.

I'm weighing the Windows and macOS options: tailscale-rs covers Windows x86_64 and macOS on ARM64, while phones would need libtailscale. I'm also noting that tailscale-rs is still experimental and upstream lacks MagicDNS and HTTPS certs, so for day one on the server and desktop I'm considering a `tailnet` trait with a system Tailscale backend and an embedded one.

I'm deciding on a fallback for day one: system Tailscale everywhere, plus embedded tailscale-rs on server and desktop behind a flag marked experimental, with the phone-embedded path left as a libtailscale prototype. Since MagicDNS is missing from tailscale-rs, pairing would have the server hand over its tailnet IP, and devices would store both LAN and tailnet addresses and try LAN first.

I'm working through the HTTPS question for the local setup: Tailscale can issue real certificates for tailnet names, but tailscale-rs doesn't support that, so it would need the system client. For LAN-only use I'm weighing a local CA that devices trust during pairing against a domain with DNS-01 validation, and leaning toward the latter as the proper option with the local CA as the offline default.

I'm weighing whether a streaming audio client would be simpler for the web version, with the server handling wake-word detection, since that keeps the browser light enough for older tablets. The cost is a constant audio stream on the LAN and server CPU per node, though the audio stays on hardware the user owns.

I'm settling the brightness side of the tablet mode: the app can set its own window brightness on both Android and iOS, with a keep-awake flag, and on Android it could instead keep the screen off under a foreground service, waking on the wake word or a touch. For the toolkit I'm leaning toward one shared Rust core on every platform, with the UI layer picked per platform, and departing from Rust only where a platform integration can't be done from Rust or is clearly worse, recorded in a decision note.

I'm going through how the mobile shells would be split: on iOS and Android the platform-specific extensions and services are mostly Swift and Kotlin anyway, so the shell would sit on a shared Rust core via UniFFI. The A2UI renderers for SwiftUI and Compose mean only desktop would need a Rust UI, and I'm planning to prototype that path first.

I'm planning a prototype pass that puts the hardest screen and the hardest integration on each platform under test: a 100k-item list and hotkey on desktop, and share-sheet, background notifications and a wake-word kiosk on the phone. I'm also weighing Slint against a native shell on mobile, with a decision rule to settle it. For admin read-all, I'm keeping it on by default as a setting, with an audit log of every admin access.


</details>

Short answer on Tailscale: tailscale-rs won't work on phones today even if our apps are Rust, but another official Tailscale library should. On everything else your decisions hold together, and I've noted where each one leads.

## Trust

- **Private by default:** nothing is shared until its owner shares it, whether that is one item, a rule (a sender or label), or a whole source.
- **Admin:** can read everything by default, as a server setting that can be tightened later. I'd still log admin access to other people's data, so it is visible.
- **Shared nodes:** they say "Ian, you have a new email" and nothing more.

## Tailscale on phones

tailscale-rs is an embedded node: the app itself joins the tailnet, with no Tailscale app installed. It is not tied to desktop clients by design, but [its README](https://github.com/tailscale/tailscale-rs/) lists Android and iOS as unsupported platforms, so writing our phone app in Rust does not change that.

| Library | Platforms | State |
|---|---|---|
| tailscale-rs | Linux, macOS (ARM64), Windows | Experimental, 0.7.1; no MagicDNS or HTTPS certificates, and direct connections are still in progress |
| [libtailscale](https://github.com/tailscale/libtailscale/) | Linux, macOS, iOS, Android | Official C library around the mature Go implementation, callable from Rust |

A [Dart package](https://pub.dev/packages/libtailscale) already ships libtailscale on iOS and Android, and on iOS it needs no VPN profile. I haven't tested it from Rust, so it needs a prototype. Two costs are known:

- **Size:** it adds roughly 20 MB to the app.
- **Backgrounding:** on iOS the node stops when the app is suspended.

For day one I'd build one `tailnet` crate with three backends:

1. **System Tailscale:** if the Tailscale app is installed, we use it. This works on every platform now.
2. **Embedded tailscale-rs:** a settings toggle on the server and desktop, labelled experimental.
3. **Embedded libtailscale:** on phones, if the prototype works.

Devices store the server's LAN and tailnet addresses at pairing and try the LAN first.

## Web clients and HTTPS

- **Admin panel:** this can be Rust compiled to WebAssembly, using a Rust web framework such as Leptos or Dioxus.
- **Voice page:** I'd take your lighter idea, where the page streams audio and the server detects the wake word. The page stays tiny and works on old tablets. The cost is server CPU per node, and the audio only goes to your own box.
- **HTTPS, LAN-only:** the server runs its own certificate authority, and each browser device trusts it once. This needs no internet.
- **HTTPS, real certificate:** either your own domain, or Tailscale's [built-in certificates](https://tailscale.com/docs/how-to/set-up-https-certificates), which need the system Tailscale app on the server.

Native apps don't need HTTPS certificates, because they can pin the server's key at pairing.

## Tablet low-power mode

A black screen only saves power on OLED. On LCD tablets the backlight is the cost, so the mode should also drop the app's screen brightness to minimum, and wake on voice or touch. On Android we can go further and let the screen turn off while a background service keeps listening.

## Toolkit: best per platform

I'd split it so that Rust is always the core and the UI layer is chosen per platform:

- **Shared Rust core everywhere:** protocol, sync, storage, module logic and voice.
- **Desktop:** Rust UI, with the toolkit decided by the 100,000-item prototype.
- **Phones and tablets:** compare Slint against a thin native shell (SwiftUI, Jetpack Compose) over the Rust core, joined by Mozilla's UniFFI bindings.

Two things favour native shells on mobile:

- **Extensions:** the integrations we want (share sheet for clipboard, keyboard, notification extensions) are separate app extensions that are normally written in Swift or Kotlin.
- **A2UI:** it already has official SwiftUI and Compose renderers, so only the desktop would need our Rust renderer.

Slint does support both phones from Rust and is actively improving there ([1.19](https://slint.dev/blog/slint-1.19-released), 16 November 2026), so it stays a real candidate.

The rule for leaving Rust would be: only in the UI and platform-glue layer, only when a required integration is impossible or clearly worse from Rust, and written down as a decision record in the repo.

## Next step

I suggest two prototypes before anything else:

1. **Mobile shell:** Slint against a native shell, on one iPhone and one Android tablet. Each builds a share-sheet clipboard action, a wake-word kiosk screen, and embedded libtailscale.
2. **Desktop toolkit:** the 100,000-item list.

Shall I write those two prototype plans, or draft the device protocol and grants model first?


---

### User

I am happy to do some prototyping, but in the past I have been in Prototyping Hill where, for several days on end, we have been doing prototyping. I would like to get to an initial release with most of the functionality, if not all, With the initial release and then iterate on top of it. 

Similar to the PVA, or personal voice assistant, library, there will be a report bug or suggest feature functionality built into every app. This will create a ticket on the GitHub repository, which allows us to quickly collect feedback from our users and point agents at issues and quickly fix them and/or implement new functionality. This will be a huge way we could quickly iterate on various fixes. 

Our end goal is to have a virtual assistant or personal virtual assistant of a whole household. 

The ultimate end goal, and again this is beyond diverse release, well beyond, is to sell hardware that people can put in their homes, own their own virtual assistant and data and everything. While not compromising on functionality. 

The Assistant and desktop application and everything will also, but not everywhere, have AI or AI support. For example, if I talk to a virtual assistant, I expect an AI model or something behind it to process my request and potentially perform actions. But I want to have it in a sort of virtual assistant way, where with PVA we have several kind of characters or visuals for agents or for the assistants. And I want to have this also in the virtual assistant application that we were planning.


---

### Assistant (claude-fable-5.2)

<details>
<summary>Reasoning</summary>

The user wants to dodge prototyping hell and reach a first release, with a built-in way to report bugs and suggest features, aiming eventually at a household assistant with hardware and personas. I'll keep it brief: lock in defaults now, timebox the choices, and structure things so the toolkit can be swapped later. Then I'll cover feedback design, assistant personas, and what the hardware means, and end with the next step.

I'm weighing whether a web search is needed for the GitHub issue details, and I think my general knowledge covers it. For the feedback flow, the app shouldn't embed a GitHub token, so I'm considering routing reports through a server, either a GitHub App the project runs or a prefilled issue URL that needs no token, though households may lack GitHub accounts. Diagnostics could include private data, so a preview before sending matters.

I'm weighing Slint for desktop, since its list view should virtualize a large list, but I'll verify that with a one-day spike as the first task of the real build. For Tailscale, I'll use the system install first and treat an embedded build as a later, optional step.

Next I'm weighing the multi-user side: the assistant acts through its tools under whatever the user has granted, and on a shared household node it has to act under the permissions of whoever is speaking. Ollama covers the fully local case, but using Claude Code or Codex subscriptions on a server that serves a whole household is a terms question I haven't checked. For hardware, the server needs to run on low-power ARM64 as a single binary with simple updates and no cloud dependence. I'm also wondering whether Slint's royalty-free licence covers a device that has a screen, since I think it excludes embedded use, though I'm not certain of that. Finally, I'll write the release plan and ask a few questions.


</details>

That changes the approach: no open-ended prototyping. We decide now, build towards a release, and keep the risky choices behind boundaries so a wrong one is a contained rewrite.

## Decisions instead of prototypes

| Choice | Decision | If it turns out wrong |
|---|---|---|
| Core | Shared Rust core on every platform | Not expected to change |
| Phone and tablet UI | Native shells (SwiftUI, Jetpack Compose) over the Rust core | Low risk: extensions and A2UI renderers already exist there |
| Desktop UI | Slint | UI layer only; core and modules are untouched |
| Admin web panel | Rust compiled to WebAssembly (Leptos) | Isolated app |
| Voice web page | Tiny page, server-side wake word | Isolated app |
| Remote access | System Tailscale on day one; embedded libraries after release | Hidden behind the `tailnet` crate |

The one unverified bet is Slint with the 100,000-item list. I'd make that the first build task, limited to two days, with a written pass or fail threshold. If it fails, we switch toolkit once and move on.

## Built-in feedback

- **Flow:** every app has "Report bug" and "Suggest feature", which send the report to the household server, and the server files the GitHub issue. No app carries a GitHub credential.
- **Attached automatically:** app version, platform, device type and recent logs.
- **Privacy:** the repository is public and logs can contain email subjects or clipboard text. The user sees exactly what will be sent and can edit it first.
- **Credential:** I only read PVA's README, so I don't know how it authenticates today. The options are a token the admin configures, or a small relay we host, which is the only cloud piece and is optional.
- **Offline:** reports queue on the server until there is internet.

## Assistants as characters

An assistant is a server-side entity, the same on every device:

- **Identity:** name, wake word, voice, visual and personality.
- **Brain:** a model provider per assistant, with Ollama for fully local.
- **Abilities:** the module tools it may use (email, reminders, window control on your desktop).
- **Scope:** household-wide or personal to one user.

It always acts with the permissions of the person it is talking to. On a shared node, an unrecognised voice gets guest abilities only.

One issue to check: Claude Code and Codex subscriptions are personal. Using one from a server that answers the whole household may not be allowed by their terms. I haven't verified this. The safe design is that a subscription is linked by one user and only serves that user's requests.

## What the hardware goal means now

- **Server:** one self-contained binary that runs on low-power ARM boxes, with no cloud dependency and simple updates.
- **Setup:** pairing and first-run must work for a non-technical person.
- **Licences:** every dependency must allow commercial hardware. Slint's free licence may not cover embedded devices with a screen, so I'll check this before we commit.

## Path to the first release

I'd build in vertical slices, each working end to end:

1. **Skeleton:** server, protocol, pairing, users and roles, event log, a desktop shell and the feedback button.
2. **Desktop hub:** launcher, clipboard with sync, notifications and settings.
3. **Email and routing rules.**
4. **Voice:** assistants, the Android tablet node and the web voice page.
5. **Phone apps and Tailscale.**
6. **AI:** tools, summaries and A2UI surfaces.

From slice 1 onwards, the feedback loop is live, so you can use it daily and file issues for agents to fix.

## Next step

I can now write the full engineering specification for the unified system, replacing the desktop-only brief. Two questions first:

1. **Existing server:** do we port the PVA TypeScript server to Rust module by module, or start the Rust server fresh and use PVA as the reference?
2. **Slice order:** is the order above right, or should voice come before the desktop hub, since PVA already does it?


---

### User

One thing I do want to note down as part of this is that we want to ensure that the visual experience across all applications is the same. So part of this kind of project will be to come up with a strong visual design document that is very typical to us and that everyone can recognize as us as well. 

Looking at the next steps, I think it will be not best to port the PVA TypeScript server, but to see what we want to do with a fresh server and what it should include.

The server will be the core part of this whole project, so we probably need to start fresh, especially with new requirements added to it. Especially also, we're going to convert it to a Rust server. 

So the path to first release, I think it's first very important for us to set up the server. Protocol pairing uses roles, event logs, and the subshell and feedback button. I think getting the server protocols, pairing uses, admin panel, event logs is the very first part we want to have set up. This allows us to start configuring and start expanding upon the modular core of it: desktop shell and feedback. I think the feedback will also be part of the first step. Desktop shell less so.

I think the second part will be indeed the desktop hub, which you have listed there, but also the kind of voice assistant web frontend, because this allows us to interact already with the server itself. The desktop hub also allows us to do so. Email routing rules, in my opinion, are modules of the server and functionality of it. For example, sending notifications like, "Hey, blah, you have a new email." I want to potentially receive this on my desktop, but also on the web frontend, or maybe in the future, an iOS app, right? 

I believe we will potentially have multiple apps. One potentially could be an app with a voice assistant, and the other could be an app that is fully integrated into the whole ecosystem as a whole.

Again, we're trying to create an ecosystem here that you can install on any device, not one that you need to buy a device for, like Apple or Android. 

AI tool summaries. And I think AI should be a core part of this system, so I don't think it should be at the end. I think it should be part of maybe step one or step two, not beyond, because AI will be the core part of it. For example, if you want to summarize notifications or interact with the server, we should be able to do this via voice, not just an app. Obviously, an app is also there, but I think voice should be the first part of it. 

Additionally, this allows us to do a bunch of AI stuff. What we should support from day one AI-wise, though, should be Cloud Code or Codex subscriptions, mostly because they are allowing people to use a large amount of AI on the chip. Also Open Router, because it allows you to pick and choose your own models beyond the two big labs.

Additionally, we want to have also support for an Olama instance on the network or on the device in the server itself. Because with Ollama support, we are able to, for example, again, the long-term vision goal is to have boxes where you can run this stuff on. We could potentially have a box pre-installed with a specific model that is really good for all of this virtual assistant stuff. That we can run local, for free, and privately. But also allows support for, for example, codecs or cloud code subscriptions. 

Phone apps in TealScale, I think it would be good to have that as last. I think first having the desktop version for me has the most benefit. Phone apps will definitely be part of the first release though. 

Looking at hardware goals, I think the hardware goals would be good. It's good to check the licenses for the rest. The hardware goals section looks good to me. 

Assistant as characters. I still think having the character and assistant model that PVA has is good. But there's still some correction needed. So PVA's implementation is not perfect; it has many flaws. It for me is still sometimes a bit complicated why a assistant or a character is not being summoned, or is being summoned when I don't want it to. 

One very important part that is also mentioned before, but A2UI will be a core part of this system as well, because we want to be able to have agents be able to, or even applications be able to build dynamic UIs when needed.

Of course, we don't want to have everything to be a dynamic UI, but let's say an agent needs to have a video player with pause functionality and volume functionality. A2UI should be able to create this on the fly and potentially cache these as well.

But for example, also for common UI, again video player as example, because this is going to be potentially a very common UI across nodes but also across devices, we might be able to, we might want to integrate with the native platform or we might want to build the standard UI for this, just so we don't need to send an A2UI response every time with when we want to play a video.

We might want to just be like, hey, play this URL as a video, and it will just play it as a video. We don't need to send the A2UI format to the device every time. This will save on bandwidth and slightly a little bit on speed. I know we're local, but it's the best to do it this way, I think.


---

### Assistant (claude-fable-5.2)

<details>
<summary>Reasoning</summary>

I've got the user's latest decisions, and I'll respond briefly, acknowledging them and where they lead. A few points are still unverified, namely the Slint licence for embedded hardware and the subscription terms for Claude Code and Codex in a household setting. Since the user wants licences checked and I said I'd check before committing, I'll run one search with several queries to cover both.


</details>

<details>
<summary>Reasoning</summary>

I'm checking the licensing options for Slint: its royalty-free tier excludes embedded systems, GPLv3 works on any platform, and commercial use starts at a per-device royalty. A desktop app looks fine, while a hardware box with a Slint screen would need the paid route.

I'm weighing the Slint options: GPLv3 would mean open-sourcing the product, or else a roughly $1 per-device royalty for a hardware box with a screen, while second-hand tablets running the app count as mobile applications. On the Claude Code side, Anthropic allows end users to sign in to the unmodified binary with their own subscription, but not third parties routing requests through subscription credentials, and preinstalling it in products falls under the Commercial Terms.

I'm checking how Anthropic's rules apply to the design: we'd run the unmodified `claude` binary and let each user sign in with their own subscription, so no tokens pass through us. A shared household assistant that uses one person's subscription to answer another's requests looks disallowed, and preinstalling on sold hardware would fall under the Commercial Terms. Since the policy has shifted recently, that's a risk to keep in mind. For Codex, the Sign in with ChatGPT terms explicitly bar using one user's subscription for another user's requests, and I'm still working out how that applies if we drive the CLI directly.

I'm settling on the household setup: a shared server run by the admin doesn't count as a runtime only one user controls, so a guest's request through someone else's subscription falls outside Codex's terms. That makes subscriptions a personal option per user, while Ollama or OpenRouter (paid from the admin's key) cover the shared default. Background tasks like auto-summarising email would also need explicit consent before they run on a subscription.

I'm looking at A2UI's basic catalog, which already has Video and AudioPlayer components rendered natively with controls, so a video request could just be a small Video component with a URL. Custom catalog components like a MediaPlayer would map to the same native widgets. I'm thinking in three tiers: direct device commands that skip A2UI entirely, catalog components referenced by name, and generated surfaces that get cached as templates so only the data model is resent.

I'm checking how the design tokens would work across platforms: one source in the repo for colours, type, spacing and motion, generating the Slint, SwiftUI, Compose and CSS themes. That conflicts with the earlier brief, which had the default mimic the desktop, so I'll flag it and ask whether the app's own identity should be the default instead, with the desktop look as an optional theme. Wake and summoning come next.

I'm noting that the summoning problems need deterministic rules, so each assistant gets its own wake word, one explicit state machine governs activation, and every wake decision is logged with its reason in the admin panel. With several nodes, the nearest one wins by score, and a follow-up window keeps the conversation going. I'd like some examples of the misfires before I go further. Then the slices: first the server core, covering protocol, pairing, roles and grants, the event log, modules, the Leptos admin panel, and the AI provider layer; second, voice and desktop, covering assistants, the web voice page, the desktop hub, and the A2UI renderer.

I'm wrapping up the remaining pieces: the server modules for email, routing and reminders, plus the phone and tablet apps over Tailscale. The design doc will run alongside from the first slice, with the tokens ready before the voice UI. I'm also weighing whether the mobile work should be one codebase with a node mode and a personal mode, and I still need answers on the default design, the wake-word misfires, and whether the repo is open source.

I'm deciding which questions to ask before writing the full spec: whether the desktop look or the app's own identity should be the default, which wake-word misfires to work from, and whether the repo is open source, since that affects the GPL question for the hardware.


</details>

Your order works, and I checked the three open items: the Slint licence, the subscription terms, and how A2UI handles your video case. The subscription terms change the AI design the most.

## AI subscriptions: personal only

Both vendors allow driving their CLI from our software, but only for the person who signed in. This is my reading of the terms, not legal advice.

- **Claude Code:** [Anthropic's terms](https://code.claude.com/docs/en/legal-and-compliance) forbid routing requests through subscription credentials on behalf of other users. A user signing in to the unmodified `claude` binary with their own plan is allowed, and `claude -p` [draws from the subscription](https://support.claude.com/en/articles/15036540-use-the-claude-agent-sdk-with-your-claude-plan).
- **Codex:** [OpenAI's sign-in terms](https://openai.com/policies/sign-in-with-chatgpt-terms/) (4 November 2026) prohibit using one user's subscription for another user's requests. They also require a runtime that only that user controls, and express consent before background use. They are written for apps that integrate the sign-in directly; I'd apply them to driving the CLI too.

This leads to three rules:

1. **A subscription serves only its owner.** Each user links their own, signs in through the vendor's flow, and we never touch the tokens.
2. **Household and guest requests use Ollama or OpenRouter.** A shared kitchen assistant cannot run on your subscription when your partner is the one asking.
3. **Where the CLI runs is an open risk.** A shared server may not count as a runtime "only that user controls" for non-admin members. The fallback is to run the CLI on that user's own desktop.

For hardware, preinstalling Claude Code on a box we sell requires Anthropic's commercial terms. Ollama is the safe default brain for the box.

## Slint licence

- **Desktop, phone and web apps:** free with attribution.
- **The server box:** unaffected, because it is headless.
- **A dedicated device with a screen that we sell:** this counts as embedded. It needs either the whole product under GPLv3, or a [commercial licence](https://slint.dev/pricing) from $1 per device.

## A2UI: three tiers

Your video example maps onto what A2UI v1.0 already does, cheapest first:

1. **Commands:** "play this URL" is a plain protocol message, and the device uses its native player. No A2UI is involved.
2. **Catalog components:** common UI is built natively once per platform and referenced by name. The [basic catalog](https://a2ui.org/concepts/catalogs/) already has `Video` and `AudioPlayer`, and we add our own in a custom catalog.
3. **Generated surfaces:** the agent composes catalog components for one-off needs. A2UI separates structure from data, so the server can cache a surface as a template and send only new data next time.

## Visual identity

I'd keep one set of design tokens in the repo (colour, type, spacing, motion, assistant visuals) and generate the Slint, SwiftUI, Compose and CSS themes from it. Catalog components use the same tokens, so generated UI matches too.

This conflicts with the original brief, which said the desktop should mimic the host desktop by default. I'll assume our own identity is now the default and mimicry becomes an optional theme, unless you object.

## Assistant summoning

I haven't read PVA's code, so I can't say what causes its misfires. For the new design I'd make summoning one explicit state machine on the server. Every wake or ignore decision is logged with its reason and shown in the admin panel. When several nodes hear the same wake word, only one answers.

## Revised path

1. **Server core:** protocol, pairing, users, roles and grants, event log, module system, admin panel, feedback, and the AI provider layer.
2. **Voice and desktop:** assistants, the web voice page, the desktop hub and A2UI rendering.
3. **Server modules:** email, routing rules, and AI tools and summaries.
4. **Phone and tablet apps, then Tailscale.**

The design document starts alongside step 1, because step 2 needs the tokens. For your "multiple apps" idea, I'd build one mobile codebase with a personal mode and a node mode, and decide later whether to ship it as two apps.

## Questions before I write the spec

1. Is the project open source, and would GPLv3 be acceptable? That decides the Slint cost for hardware.
2. Can you give two or three examples of PVA waking wrongly or failing to wake? I'll design the summoning rules against them.


---

### User

Okay, with Slint requiring a license, I have a feeling it's not super open source. So, are there any alternatives to Slints we might want to explore before we do the implementation that are truly open source and cross-platform? 

Visual identity, I want to work on, because this will impact everything visually. 

This project will be open source and I want to go with the GPLA license. The way we earn money is via selling hardware in the future, something physical people can buy. I think I want to use PVA as an example, but not as an example in a way where we make decisions on, for example, the summoning rules. We might want to revisit because we also want to do voice recognition; will be part of the summoning as well. So when someone summons the agent, we want to also decide who is the person summing it, just in case they are not allowed to see or ask certain things.


---

### Assistant (claude-fable-5.2)

<details>
<summary>Reasoning</summary>

I'm weighing whether the user's "GPLA" means GPL or AGPL, since that changes the answer. Slint is offered under GPLv3, a royalty-free license, and a commercial one, so if the project is GPLv3 it's free to use even on embedded targets, and I should check that before suggesting swaps.

I'm checking whether "GPLA" means AGPL or plain GPL, since AGPLv3 can be combined with GPLv3 anyway. I'm also thinking about whether to search for the current state of alternatives like Iced, egui, Dioxus, Makepad, Xilem, GPUI and Freya, and leaning toward one search with several queries.


</details>

<details>
<summary>Reasoning</summary>

I'm checking the licensing: Slint is GPL-3.0-only, so free use for embedded works if the app is open source too. The user's worry only applies if they pick GPLv3, and I need to confirm whether they meant GPLv3 or AGPLv3. Both licenses' section 13 allow linking with GPLv3-only code, so an AGPL app could still link Slint.

Slint's GPLv3 licensing is free for embedded work as long as the app itself is open source, so the user's worry only matters if they pick GPLv3. Since they may have meant AGPLv3, I'm noting that GPLv3's section 13 lets an AGPL app link Slint, and I'll flag that as my own reading. The bigger practical issue is that GPL code in an App Store app creates friction, and external contributors' GPL changes would need a CLA or exception, though Slint only runs on desktop here, so that mostly matters for the user's own code.

I'm weighing permissive alternatives now: egui, iced, Dioxus, Makepad, Freya, GPUI, Xilem, and Tauri, each with its platform coverage and maturity. Since the project is GPL anyway, I'm leaning toward keeping Slint, and only switching to something permissive if the user specifically wants permissive dependencies.

I'm weighing the remaining options for a desktop-only launcher: egui handles 100k virtualized lists easily through show_rows but its theming is weaker, and GPUI is fast but its release has stalled. iced is the one I'd pick as a fallback, since COSMIC's launcher is built on it, though its maintainer calls it experimental and it has no accessibility support yet.

I'm noting that the user's licence question still needs a GPLv3-or-AGPLv3 clarification, since AGPL closes the network-use loophole, which matters for a server. I'm also planning to include the speaker-identification step in the summoning state machine, and to offer to start on the visual identity. The Slint version I'm citing is 1.19 from earlier, and I've confirmed the licence from LICENSE.md.


</details>

Slint is truly open source: it is offered under GPLv3, and since your project will be GPL, you can use it free on every platform, including hardware you sell. The paid licence only applies to proprietary products.

## What your GPL choice changes

[Slint's licence file](https://github.com/slint-ui/slint/blob/refs/heads/master/LICENSE.md) offers three options, and you pick one:

| Option | Cost | Covers |
|---|---|---|
| GPLv3 | Free | Open source apps on desktop, mobile, web and embedded |
| Royalty-free | Free with attribution | Proprietary apps, but not embedded |
| Commercial | Paid | Proprietary apps, including embedded |

My earlier warning about a per-device fee assumed the product might not be GPL. With a GPL project, that cost disappears.

Two consequences of GPLv3 are worth knowing:

- **Hardware:** buyers must be able to install modified software on the box. That fits "own your own assistant".
- **App Store:** Apple's terms conflict with the GPL. You can publish your own code there, but outside contributors would need to sign a contributor agreement. Slint itself is not affected, because the iOS app uses a SwiftUI shell.

## Alternatives with permissive licences

These are all MIT or Apache, checked against two current comparisons ([measured desktop study](https://goldstrikearch.github.io/rust-gui-desktop-ecosystem-state/), [feature matrix](https://areweactuallyguiyet.vercel.app/)):

| Toolkit | Platforms | Main weakness |
|---|---|---|
| egui | Desktop, web, Android, iOS | Built for tools; a distinctive brand look is hard to achieve |
| iced | Desktop, web | No accessibility; its author calls it experimental and [desktop-only](https://se-radio.net/2026/03/se-radio-713-hector-ramon-jimenez-on-building-a-gui-library-in-rust/) |
| Dioxus | Desktop, web, mobile | Stable version is a webview; the native renderer is still in [beta](https://blitz.is/roadmap) |
| Makepad | Desktop, web, Android, iOS | No accessibility; own markup language |
| Freya | Desktop, Android | One maintainer |
| GPUI | Desktop | Releases stalled; Zed has deprioritised work outside its editor |
| Xilem | Desktop | Alpha |

## Recommendation

Stay with Slint under GPLv3. It is the most mature native option, has accessibility by default, and is backed by a company whose revenue comes from the paid licences.

If you would rather have no dual-licensed dependency, iced is my fallback for the desktop. It is proven in a similar product (the COSMIC desktop and its launcher are built on it), but you give up accessibility for now. The toolkit only affects the desktop UI layer, so a later switch stays contained.

## Summoning with speaker ID

Agreed: identifying the speaker becomes a step in summoning, not something added afterwards. The sequence is wake word, then who is speaking, then what that person may ask or hear. An unrecognised voice gets guest permissions. I'll design this fresh and use PVA only as a reference for the character model.

## Two things I need

1. **Licence:** "GPLA" could mean GPLv3 or AGPLv3. AGPL also requires anyone who runs a modified server for others to publish their changes. By my reading, both work with Slint. Which one do you want?
2. **Visual identity:** shall I start the design document next? If so, give me three or four words for how it should feel, and any products whose look you admire.


---

### User

Create a technical document with the things we have discussed here and in previous documents and threads.


---

### Assistant (claude-fable-5.2)

<details>
<summary>Reasoning</summary>

I'm weighing whether to run new searches or build the document from what's already been established here, since the user wants a technical document pulling together everything we've covered. I can likely write it from the verified material without more research, though the original brief's A2UI Rust implementation questions weren't covered in depth earlier.

I'm settling on the document's scope: it will consolidate the decisions and verified points from the conversation, flag the open questions (the GPLv3 versus AGPLv3 licence choice and the visual identity wording), and note that the A2UI Rust library search hasn't happened yet. I'll also say plainly that the full engineering spec isn't done, so the document doesn't overstate what's settled.

Next I'm working out how to lay the document out, with sections covering purpose, architecture, identity, clients, licensing, and the roadmap, and marking which points are settled versus still open.

I'm noting the remaining points: the personal subscriptions are for my own use only, email reading stays inside the app while other actions go to the mail client, and the App Store's GPL terms clash with the licence choice, so the GPLv3-or-AGPL question is still open. The roadmap runs from the server core through voice and desktop, then email, routing and AI tools, and finally the phone and tablet apps before Tailscale.

I'm confirming that Tailscale support is covered: the system install will do for now, with the server listening on a tailnet address during the first two phases, and phones are included in the first release.


</details>

This document consolidates this conversation and the desktop brief. I have no access to other threads, and I have only read the PVA README, not its code. It is a decisions document rather than the full engineering specification: the research the brief asked for that we have not done yet is listed in section 20.

````markdown
# Personal Virtual Assistant: Technical Design Document

Status: draft 1, 25 November 2026 (Sydney).
Sources: the desktop hub brief and the design conversation that followed.
Where the two conflict, the later decision wins and the conflict is noted.

## 1. Vision

One self-hosted assistant ecosystem for a whole household. It runs on a
local server box and reaches every device the household already owns:
desktops, phones, tablets and browsers. It aims for Apple-ecosystem
continuity, but local and self-owned.

- **One system:** the server is the hub; every client is a device of it.
- **Local:** the server is on the LAN and needs no internet.
- **Voice and screen:** assistants are characters you can talk to, and the
  same system powers a fast desktop hub.
- **Long-term goal:** sell hardware boxes with the software preinstalled.
  This is well beyond the first release.

## 2. Principles

1. **Server is the default home.** Data lives on a device only if it is
   physically tied to that machine or must respond within a frame.
2. **Never blocked by the server.** Clients write locally first, then sync.
3. **Private by default.** Nothing is shared until its owner shares it.
4. **Rust first.** Another language is allowed only in the UI and
   platform-glue layer, when an integration is impossible or clearly worse
   from Rust, and recorded as a decision record in the repo.
5. **Modular.** Adding a module must be trivial. Extension is by forking
   and adding modules; there is no plugin system.
6. **Decide, then build.** No open-ended prototyping. Risky choices sit
   behind boundaries so a wrong one is a contained rewrite.
7. **Build on established technology.** The exceptions are A2UI and young
   Rust libraries for new technologies. Contribute to an existing library
   before creating a new one.
8. **UI for every setting.** No configuration files for users.

## 3. Architecture

### 3.1 Components

| Component | Role | Technology |
|---|---|---|
| Server | Users, devices, modules, event log, routing, assistants, AI | Rust, one self-contained binary, runs on low-power ARM |
| Desktop hub | Launcher, clipboard, notifications, email reading, window control | Rust core, Slint UI |
| Phone and tablet app | Personal mode and node (kiosk) mode | Rust core, SwiftUI and Jetpack Compose shells, UniFFI bindings |
| Admin web panel | Full configuration of the whole system | Rust compiled to WebAssembly (Leptos) |
| Voice web page | Lightweight voice relay for any browser | Tiny page; audio streams to the server |

The existing PVA TypeScript server is not ported. The Rust server starts
fresh, with PVA as a reference for the character model only.

### 3.2 Repository

One monorepo:

```text
crates/
  protocol/   # events, device messages, shared types
  core/       # users, grants, routing rules, event log
  modules/    # email, clipboard, notifications, reminders, ...
  voice/      # wake word, speaker ID, STT, TTS (sherpa-onnx)
  ai/         # provider layer
  tailnet/    # remote access backends
  ui/         # shared screens, A2UI renderer
apps/
  server/  desktop/  mobile/  web-admin/  web-voice/
design/
  tokens/     # single source for all themes
```

### 3.3 Protocol

- Every device holds one WebSocket to the server.
- Message types live in the `protocol` crate, which every Rust binary
  imports. Swift and Kotlin shells get them through UniFFI.
- Devices act as nodes: they push events up (notifications, clipboard
  items) and expose capabilities down (show a surface, window control,
  play media).

### 3.4 Modules

A module declares its server part and optional client parts together:
events, tools for assistants, settings, A2UI catalog components and
shortcut-bindable actions. Email, clipboard, notifications, reminders and
routing are all modules.

## 4. Data and sync

### 4.1 Where data lives

| Data | Lives | Notes |
|---|---|---|
| Users, roles, grants, rules, credentials, settings | Server | Clients keep a read-only copy |
| Notifications | Server | Desktop is a source and a display |
| Email | Server | Desktop keeps a cache for reading and search |
| Clipboard | Captured on device, stored on server | Device keeps a local index |
| Launcher index, hotkeys, window control | Desktop | Tied to the machine |

### 4.2 Local first, then sync

1. Write to the local store and update the UI immediately.
2. Put the change in a local outbox.
3. Sync the outbox to the server in the background.
4. If the server is unreachable, the outbox drains on reconnect.

The sync model is a per-user append-only event log with sequence numbers.
Each device stores its cursor and catches up from it. Settings use
last-writer-wins. With the server down, the desktop keeps working from its
cache in read-only mode for server data.

## 5. Identity, roles and sharing

- **Roles:** admin, member, and a restricted role for children and guests.
- **Ownership:** every item belongs to one user or to the household.
- **Sharing:** private by default. The owner shares one item, a rule (for
  example a sender or label), or a whole source.
- **Admin:** can read all data by default. This is a server setting that
  can be tightened later. Admin access to other users' data is logged.
- **Device ownership:** a desktop or phone is paired to one user. Shared
  nodes belong to the household.

Who is acting is resolved in layers:

1. Device ownership, for personal devices.
2. Speaker ID, on shared devices. It is convenience, not security.
3. Step-up confirmation on the user's own device, or a PIN, for sensitive
   actions.

## 6. Notifications and routing

- The server is the notification centre. State (unread, dismissed,
  replied) is shared across devices.
- A rule engine on the server maps event, per-user rule and target
  devices. Example: an email arrives, notify the desktop if active,
  otherwise speak on the kitchen node.
- Local app notifications arrive on the desktop's own bus. The desktop
  shows them at once and forwards them to the server, where they are
  routed like any other.
- A shared node says only "Ian, you have a new email". Content stays on
  the user's own devices.

## 7. Clipboard

- Capture and paste are local and instant; sync follows.
- The newest item is pushed to the user's other devices. History and
  large blobs are fetched on demand.
- Password-manager copies are excluded from sync by default.
- Phones cannot read the clipboard in the background. They use a share
  sheet, shortcut or keyboard extension.
- Carried over from the brief: rich representation per item, safe
  rendering of copied HTML, hundreds of thousands of items with snappy
  search, and a non-blocking restore that tells the user when it is done.

## 8. Email

- Accounts are held and fetched by the server, so routing works when the
  desktop is off.
- Clients read and search from a local cache.
- From the brief: the hub is for reading; anything more opens the user's
  email application.

## 9. Assistants

### 9.1 Character model

An assistant is a server-side entity, identical on every device:

- **Identity:** name, wake word, voice, visual and personality.
- **Brain:** a model provider per assistant.
- **Abilities:** the module tools it may use.
- **Scope:** household-wide or personal to one user.

### 9.2 Summoning

Summoning is one explicit state machine on the server, designed fresh:

1. Wake word detected.
2. Speaker identified against enrolled voiceprints (sherpa-onnx).
3. Permissions resolved: the assistant acts as that person. An
   unrecognised voice gets guest abilities.
4. If several nodes heard the wake word, exactly one answers.

Every wake or ignore decision is logged with its reason and shown in the
admin panel.

### 9.3 Voice nodes

- **Android tablet:** native app; can listen with the screen off.
- **iPad:** kiosk app kept in the foreground.
- **Browser:** the voice page streams audio and the server detects the
  wake word. This costs server CPU per node.
- **Low-power mode:** black screen plus minimum brightness; wake on voice
  or touch.

## 10. AI

AI is part of the core, built in phase 1.

| Provider | Use | Constraint |
|---|---|---|
| Claude Code CLI | Personal requests | Serves only the user who signed in |
| Codex CLI | Personal requests | Serves only the user who signed in |
| OpenRouter | Any request | API cost |
| Ollama | Any request; default for household and guests | On the server or elsewhere on the LAN |

Rules that follow from the vendors' terms (my reading, not legal advice):

1. Each user links their own subscription through the vendor's sign-in.
   We never handle the tokens.
2. Household and guest requests never use a personal subscription.
3. If a shared server does not qualify as a runtime only that user
   controls, the CLI runs on the user's own desktop instead.

Ollama is the default brain for a future hardware box. Preinstalling
Claude Code on hardware would need Anthropic's commercial terms.

## 11. A2UI

A2UI is core to the system and used in three tiers, cheapest first:

1. **Commands:** "play this URL" is a plain protocol message; the device
   uses its native player. No A2UI is sent.
2. **Catalog components:** common UI is built natively once per platform
   and referenced by name. We add a custom catalog on top of the basic
   one; modules contribute components to it.
3. **Generated surfaces:** an agent composes catalog components for
   one-off needs. The server caches surfaces as templates and sends only
   new data afterwards.

Renderers: official SwiftUI and Compose renderers on mobile, and a Rust
renderer for Slint on the desktop. The Rust renderer is the likely first
library we contribute to or create. Catalog components use the design
tokens, so generated UI matches the rest.

## 12. Clients

### 12.1 Desktop hub

Requirements carried over from the brief:

- Launcher opened by a global hotkey; clipboard manager; interactive
  notifications; email reading; control of other applications' windows.
- Speed is the key property. "Snappy" must be defined in measurable
  terms, with latency tests that prevent regressions.
- Linux first and desktop-agnostic, on X11 and Wayland, including
  pre-COSMIC Pop!_OS. macOS second; Windows an afterthought.
- User-assignable keyboard shortcuts for module actions.
- macOS-style settings window, and a light first-run setup that infers as
  much as possible from the environment.

Toolkit: Slint under GPLv3. The first build task is the 100,000-item
list, limited to two days with a written pass or fail threshold. The
fallback is iced, which lacks accessibility for now.

### 12.2 Phone and tablet

- One codebase with a personal mode and a node mode. Whether to ship two
  apps is decided later.
- Native shells, because share-sheet, keyboard and notification
  extensions are normally written in Swift or Kotlin.
- Phone apps are part of the first release, built last.

### 12.3 Web

- **Admin panel:** a full single-page app that configures everything.
- **Voice page:** voice relay only.

## 13. Visual identity

- One recognisable identity across every app, defined in a design
  document that starts alongside phase 1.
- One set of design tokens (colour, type, spacing, motion, assistant
  visuals) generates the Slint, SwiftUI, Compose and CSS themes.
- **Conflict with the brief:** the brief made mimicking the host desktop
  the default. This document assumes our own identity is the default and
  mimicry is an optional theme. This still needs confirmation.

## 14. Networking

- **Default:** LAN only.
- **Remote access:** opt-in through Tailscale, behind the `tailnet`
  crate, which has three backends:
  1. System Tailscale app: day one, all platforms.
  2. Embedded tailscale-rs: server and desktop, experimental toggle.
  3. Embedded libtailscale: phones, if it proves workable from Rust.
- Devices store the server's LAN and tailnet addresses at pairing and try
  the LAN first.
- **HTTPS for browsers:** the server runs its own certificate authority
  that each browser device trusts once. Alternatives are a real
  certificate from the user's own domain or from Tailscale.
- Native apps pin the server's key at pairing.

## 15. Feedback

- Every app has "Report bug" and "Suggest feature".
- The report goes to the household server, which files the GitHub issue.
  No app carries a GitHub credential.
- App version, platform, device type and recent logs are attached. The
  user sees and can edit everything before it is sent, because the
  repository is public.
- Reports queue on the server until there is internet.

## 16. Licensing

- The project is open source under the GPL family; GPLv3 or AGPLv3 is
  still to be chosen.
- Slint is used under its GPLv3 option, at no cost on any platform,
  including hardware.
- Hardware buyers must be able to install modified software.
- Apple's App Store terms conflict with the GPL. Publishing there needs a
  contributor agreement for outside contributions.
- Every dependency must permit commercial hardware.

## 17. Hardware goal

- The server is one binary for low-power ARM, with no cloud dependency
  and simple updates.
- Pairing and first-run must work for a non-technical person.

## 18. Roadmap to first release

Each phase is a vertical slice that works end to end.

1. **Server core:** protocol, pairing, users, roles and grants, event
   log, module system, admin panel, feedback, AI provider layer, LAN
   HTTPS, and listening on a system Tailscale address. The design
   document and tokens start here.
2. **Voice and desktop:** assistants, summoning with speaker ID, the web
   voice page, the desktop hub (launcher, clipboard with sync,
   notifications, settings) and A2UI rendering. This phase opens with the
   two-day Slint list test.
3. **Server modules:** email, routing rules, AI tools and summaries.
4. **Phone and tablet apps,** then embedded Tailscale.

The feedback loop is live from phase 1.

## 19. Verified and assumed

Checked against sources during the conversation:

- Slint's three licence options, and its phone support claims.
- tailscale-rs: version 0.7.1, experimental, no Android or iOS.
- libtailscale: official C library covering iOS and Android.
- The Claude Code and Codex terms on serving other users.
- A2UI's basic catalog includes `Video` and `AudioPlayer`, and official
  SwiftUI and Compose renderers exist.

Assumed, needing a build to confirm:

- Slint meets the speed target with 100,000 items.
- libtailscale works from a Rust core on phones.
- A server counts as a permitted runtime for a member's CLI subscription.
- Surface templates can be cached and reused with new data.
- Server-side wake word detection scales to several nodes on ARM.

## 20. Open questions and research not yet done

Decisions needed:

1. GPLv3 or AGPLv3.
2. Confirm that our own identity replaces desktop mimicry as the default.
3. Three or four words for the visual feel, and reference products.
4. How the server authenticates to GitHub for feedback: an admin token or
   an optional hosted relay.

Research from the brief still to do before the full engineering
specification:

- Whether any Rust A2UI implementation exists, and whether the A2UI
  project would accept or list one.
- A2UI for locally defined UI, and its latency cost.
- A2UI generation through each provider, including CLI subprocesses.
- The search engine for years of history.
- Safe rendering of untrusted HTML.
- Notifications, clipboard, global hotkeys and window control on X11 and
  Wayland, and on macOS and Windows.
- The measurable definition of "snappy" and the latency test suite.
- The catalog, the shortcut system and the generated-surface security
  policy.
- The list of libraries to contribute to or create.

Risks:

- The Slint list test fails and the desktop moves to iced.
- Subscription terms change, or exclude server-side use.
- The Wayland limits on window control and global hotkeys are still
  unresearched.
- The first release is large: server, desktop, two mobile platforms and
  two web clients.
````

Two things would let me finish this:

1. **Decisions:** your answers to the four questions in section 20.
2. **Research:** I can do the outstanding items next and expand this into the full engineering specification. Shall I?


---
