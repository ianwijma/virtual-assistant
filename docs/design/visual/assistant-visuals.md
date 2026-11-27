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
- **On a household tablet the character stands on a stage.** When an
  assistant is active, our own backdrop fills the screen. The whole
  figure stands on the left and can walk across the screen while nothing
  else is shown. A glass column on the right holds what was said and any
  card the assistant shows. This is "Full figure on a stage" on
  [the tablet board](examples/tablet-board.html).
- **The first figures are simple.** They are made to be easy to animate
  from the [reply tags](../technical/voice/reply-tags.md), not to be
  final. A simple three-dimensional figure is the form the owner has in
  mind, if research shows it can be drawn in every client. The figures
  are redesigned in full later.
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

- In which style are the full figures drawn, when they are redesigned
  later? Five styles are on
  [the figure style board](examples/figure-style-board.html).
- Does a figure have a mouth, or do the eyes alone carry its
  expressions?
- Who draws the figures, and how many are there in the first release?
- How does a person give their own assistant a look: by choosing from a
  set of figures, by adjusting parts such as colour and clothing, or by
  supplying their own drawing?
- How playful is the default household assistant: cute, friendly, or
  calm?
- Is the voice page arranged like the tablet, with the figure on a
  stage?
- May a card cover part of the character, or does it always sit clear
  of the head?
- Does a whole figure move across the screen only while nothing else is
  shown, and stand still once a card appears?
- What does an assistant without a figure show: a sound wave, as on the
  tablet board, or something else?
- How large is the character where the assistant is not the subject,
  such as in the desktop launcher and on the phone's home screen?
- May a person bring their own figure, such as a character they like
  from elsewhere? The project cannot ship characters that belong to
  others.
- Does a figure have a colour of its own, apart from the
  [accent](colour.md)?

To research:

- Whether a simple three-dimensional figure can be drawn and moved by
  the reply tags in Slint, Jetpack Compose, SwiftUI and a browser, on an
  old tablet as well, and from which kind of source file.
- How each character is animated so that it runs in Slint, Jetpack
  Compose, SwiftUI and a browser from one source.
