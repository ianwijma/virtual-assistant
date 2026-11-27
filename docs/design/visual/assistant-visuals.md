# Assistant visuals

How an assistant appears and reacts to speech. Part of
[the visual design](README.md). What an assistant is, is in
[assistants](../technical/voice/assistants.md).

Status: started. A character is an illustrated figure. Its style is not
chosen yet.

## Design

- **Each assistant is a character with its own look,** the same on every
  device that shows it.
- **A character is an illustrated figure.** Each assistant has its own
  drawn figure, with eyes and a head, so that it can wink, roll its eyes,
  nod and shake its head.
- **The examples and mockups show a placeholder,** a simple shape with
  two eyes, until the figures are drawn.
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

- In which style are the figures drawn: flat and simple, soft and
  three-dimensional, or hand-drawn? Examples of each are to be made
  before this is answered.
- Who draws the figures, and how many are there in the first release?
- How does a person give their own assistant a look: by choosing from a
  set of figures, by adjusting parts such as colour and clothing, or by
  supplying their own drawing?
- How playful is the default household assistant: cute, friendly, or
  calm?
- How large is the character on each screen: the whole screen on the
  tablet, a small part of the launcher on the desktop?
- Does a figure have a colour of its own, apart from the
  [accent](colour.md)?

To research:

- How each character is animated so that it runs in Slint, Jetpack
  Compose, SwiftUI and a browser from one source.
