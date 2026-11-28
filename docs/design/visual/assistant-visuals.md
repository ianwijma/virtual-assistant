# Assistant visuals

How an assistant appears and reacts to speech. Part of
[the visual design](README.md). What an assistant is, is in
[assistants](../technical/voice/assistants.md).

Status: started. A character is an illustrated figure. Its style is not
chosen yet.

## Design

- **Each assistant is a character with its own look,** the same on every
  device that shows it. "Character" is the word for it; "figure" is used
  for its drawn body.
- **A character has its own configuration.** Its colour is set there,
  with what else belongs to its look.
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
- **The figure in the examples and mockups is the figure for now:** a
  simple shape with two eyes, drawn flat with a little depth, that can
  look around. It stays until the figures are designed.
- **The figures are designed in a thread of their own,** not as part of
  this work. Ideas for it: a rendered three-dimensional figure that
  looks around, arms, a gesture for thinking such as a hand at the
  mouth, and a mouth that moves when it talks.
- **On a wider screen the figure gets more of the room.** It is larger
  there than on the stage and call board, and the column beside it is
  narrower.
- **Layouts leave room for a larger figure.** A later figure may need
  more space than the one for now, with arms or a whole body, so no
  screen is fitted tightly around the present shape.
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
- **The voice page follows the one folding design:** the call on a narrow
  screen and the stage on a wide one.
- **A card never covers the character's head.**
- **A figure moves across the screen only while nothing else is shown,**
  and stands still once a card appears.
- **An assistant without a figure shows a sound wave.**
- **Where the assistant is not the subject, the character is a small
  head,** the size of an icon in a row, as in the launcher and on the
  phone's Overview.

## The routes for the first figures

Research found three routes that fit the licence. None is chosen.

| Route | Gains | Costs |
|---|---|---|
| Drawn parts in layers, moved by our own code in the shared core | No licence risk, the cheapest, anyone can make a figure with free tools | We write the rigging ourselves, and it looks basic |
| A three-dimensional model in the VRM format, drawn by a small renderer of our own in the core | Ready-made expressions and mouth shapes, a free tool to make figures, one file | Graphics work in four clients, more power used on a tablet that is always on, each model's licence must be checked |
| dotLottie animations with their state machines | A free runtime on every platform, one file | The tools to make them are not open, and moving the mouth with speech is clumsy |

Live2D and Spine are ruled out: their licences do not fit GPLv3 and
hardware that is sold. Rive's runtimes fit, but its editor is closed
and paid, so a person could not make their own figure freely.

## Verified and assumed

Verified on 28 November 2026, from each project's own pages:

- The Rive runtimes, dotlottie-rs and ThorVG are under the MIT licence.
  Filament and SceneView are under Apache 2.0. wgpu and three-vrm are
  under MIT or Apache 2.0.
- Live2D needs a signed release licence, and Spine needs every user of
  the product to hold an editor licence.
- VRM 1.0 has presets for moods, for five mouth shapes, for blinking and
  for where the eyes look.
- About 7% of Android devices have no Vulkan.

Assumed:

- A renderer of our own for a model with blend shapes is a few thousand
  lines, and Slint can show its output. Slint's interface for this is
  marked unstable.

## Open questions

- In which style are the full figures drawn, when they are redesigned
  later? Five styles are on
  [the figure style board](examples/figure-style-board.html).
- Does a figure have a mouth that moves when it talks, and arms? Both
  are ideas for the thread on the figures.
- Is the figure of the first release a rendered three-dimensional one,
  or the flat one for now?
- How much more room does a screen keep for a later figure: how much
  wider and taller than the figure for now?
- Who draws the figures, and how many are there in the first release?
- How does a person give their own assistant a look: by choosing from a
  set of figures, by adjusting parts such as colour and clothing, or by
  supplying their own drawing?
- How playful is the default household assistant: cute, friendly, or
  calm?
- May a person bring their own figure, such as a character they like
  from elsewhere? The project cannot ship characters that belong to
  others.

- From the research: which of the three routes above do the first
  figures take?

To research:

- How much power a three-dimensional figure uses on an old tablet that
  is on all day. No figures were found.
