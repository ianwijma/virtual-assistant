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
- It uses the compact density. See
  [shape and spacing](shape-and-spacing.md).

## Open questions

- How is the timeline of a request shown? Four designs are on
  [the admin log board](examples/admin-log-board.html).
- How does the first-run setup look? Four designs are on
  [the setup board](examples/setup-board.html).
- What does a destination with no list of items show, such as Speech or
  Feedback: two columns, or a second column of its sections?
- Where do search results appear in three columns?
- Does a settings page save as you go, or with one Save button?
- At phone width, what does the list of destinations become?
- Which accent does the admin panel show: that of the person signed in,
  or the household's?
