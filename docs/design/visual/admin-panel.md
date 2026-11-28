# Admin panel

How the look applies to the admin panel. Part of
[the visual design](README.md). What the panel does is in
[the technical design](../technical/clients/web-admin.md).

Status: started. The principle and the layout are set.

## Design

- **The layout follows Apple's Settings, in three columns.** The first is
  a narrow glass side bar with the search field and the destinations,
  each with an icon. The second is a plain list of what the chosen
  destination holds, such as the assistants, with a way to add one at
  its bottom. The third is the page of the chosen item, with its path
  above it. Every step stays in view. This is "Three columns, calmer" on
  [the third admin layout board](examples/admin-layout-board-3.html).
- **On a narrower screen fewer columns are in view.** See
  [the visual design](README.md).
- **Before an item is chosen, the third column is quiet:** it shows a
  short summary of the destination.
- **Little is shown at once.** A page shows the high-level things first.
  Detail is one step further in. Every setting can be reached, and none
  is hidden for good, but a person is not shown everything at once.
- **Settings can be searched.** A search field finds any setting by its
  name and leads to it.
- **The page of an assistant shows the character beside its settings,**
  as in "Preview and form" on
  [the admin form board](examples/admin-form-board.html).
- **The list of requests shows a small strip in each row,** made of the
  steps of that request, so that a slow request stands out in the list.
- **The page of one request shows each step as a bar,** placed where it
  fell in time. Steps can run at the same time, and bars show that. These
  are the list of "One strip" and the page of "Bars" on
  [the admin log board](examples/admin-log-board.html).
- **The first-run setup follows Apple's first setup of a device.** It
  opens with a welcome in which the assistant's figure says "Hello". Around
  the figure the greeting is shown in several languages. These are "Hello, with the figure" and
  "Hello, in the household's languages" on
  [the welcome board](examples/welcome-board.html), together. Each step is then one calm
  pane, centred on the backdrop: a round symbol, a large title, a short
  sentence, the few fields or choices, a quiet link for the alternative,
  and one wide Continue button at the bottom. Five dots across the top
  show the steps, with a back arrow at the top left. This is "Apple
  pane, dots on top" on
  [the second setup board](examples/setup-board-2.html).
- **The setup of a new device is the same design.** A phone, a tablet or
  a desktop that joins the household is set up with the same panes, in
  the density of that device.
- It uses the compact density. See
  [shape and spacing](shape-and-spacing.md).

## Open questions

- Which figure greets in the welcome, before the household has chosen or
  named an assistant?
- Which languages does the welcome show, and in which is the setup
  offered at first?
- Is the language chosen on the welcome itself, as the board shows, or
  in a step after it?
- What does a destination with no list of items show, such as Speech or
  Feedback: two columns, or a second column of its sections?
- Where do search results appear in three columns?
- Which accent does the admin panel show: that of the person signed in,
  or the household's?
