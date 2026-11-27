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
- **The character gets most of the screen** wherever the assistant is the
  subject, as on a household tablet and on the voice page. It stands in
  the middle and the rest of the screen is arranged around it. The
  earlier voice assistant did this, and its arrangement is the reference;
  its look is not reused.
- **A figure can grow over time.** It may start as a head only. Later it
  can be a whole figure that moves across the screen. A plain form, such
  as a sound wave, is possible for an assistant without a figure.
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
- How is the screen arranged around the character on a tablet? Several
  designs are on [the tablet board](examples/tablet-board.html).
- How large is the character where the assistant is not the subject,
  such as in the desktop launcher and on the phone's home screen?
- May a person bring their own figure, such as a character they like
  from elsewhere? The project cannot ship characters that belong to
  others.
- Does a figure have a colour of its own, apart from the
  [accent](colour.md)?

To research:

- How each character is animated so that it runs in Slint, Jetpack
  Compose, SwiftUI and a browser from one source.
