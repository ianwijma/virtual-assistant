# Assistant visuals

How an assistant appears and reacts to speech. Part of
[the visual design](README.md). What an assistant is, is in
[assistants](../technical/voice/assistants.md).

Status: started. What a character looks like is not chosen yet.

## Design

- **Each assistant is a character with its own look,** the same on every
  device that shows it.
- **A character shows expressions.** They are driven by the
  [reply tags](../technical/voice/reply-tags.md): smile, laugh, think,
  surprised, sad, wink, eye roll, nod and shake.
- **A character shows the state of the conversation:**

| State | When |
|---|---|
| Idle | Nobody is talking to it |
| Listening | It was summoned and hears the person |
| Thinking | The answer is being made |
| Speaking | It talks |
| Muted | The microphone is off for it |
| Waiting | The server cannot be reached |
| Not recognised | It heard a voice it does not know and will not answer it |

## Open questions

- What is a character: an abstract shape such as an orb or a wave, a
  simple face, or a full illustrated figure? The reply tags include a
  wink, an eye roll, a nod and a shake of the head, which need eyes and a
  head.
- How do two assistants differ: by colour only, by shape, or as fully
  different characters?
- How does a person give their own assistant a look: by choosing from a
  set, by adjusting parts such as colour and eyes, or by supplying an
  image?
- How playful is the default household assistant: cute, friendly, or
  calm and abstract?
- How large is the character on each screen: the whole screen on the
  tablet, a small part of the launcher on the desktop?

To research:

- How each character is animated so that it runs in Slint, Jetpack
  Compose, SwiftUI and a browser from one source.
