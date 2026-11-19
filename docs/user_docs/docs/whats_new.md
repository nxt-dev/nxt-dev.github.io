# What's New

This page summarises what is new in the next release, which is in review
now, and in **nxt_editor 4.8**, **nxt_editor 4.7**, **nxt_editor 4.6**,
**nxt_editor 4.5**, **nxt_editor 4.4** and **nxt_core 0.21**. Each item
links to the part of the docs that explains it in full.

## Unreleased

These are in review for the next release, starting with
[nxt_editor#323](https://github.com/nxt-dev/nxt_editor/pull/323) and
[nxt#133](https://github.com/nxt-dev/nxt/pull/133), and the pull requests
merged after them. To try them now, in a Python 3.11 to 3.13 environment:

```
pip install "git+https://github.com/nxt-dev/nxt.git@next" "git+https://github.com/nxt-dev/nxt_editor.git@next"
```

### Preferences, hotkeys and looks

- **Edit > Preferences...** (`Ctrl+,`) has every preference you can set,
  with what each does, including ones that had no menu, like drag zoom
  speed and how the graph follows a run. Sections are listed on the left,
  one page each, and a search at the top looks through all of them. It
  stays open beside the editor while you work. See
  [Preferences](editor.md#preferences).
- **The Options menu is gone.** Everything it held is in Preferences: the
  error sound and the other toggles in their sections, and the AI
  Assistant, Environment Variables and Optional Components as pages of
  their own. **Layer Color View** is in the **Window** menu, and
  **Autocomplete** in the code editor's right-click menu.
- **Hotkeys are a page of Preferences**, in the same style: each action
  with what it does, its hotkey, **Clear** and **Reset**, and **Global** on
  the ones that work anywhere in the window. The search finds hotkeys by
  name or by their keys. **Window > Hotkey Editor** opens it. See
  [Hotkeys](hotkeys.md).
- **Three looks to choose from**, in **Edit > Preferences > Panels >
  Look**: Modern, Classic (how the editor looked before) and Host
  application, which looks like Maya, Blender or Unreal when the editor
  runs in them, and a **Stylesheet** of your own to lay over it. **Reopen Now** shows a new look
  straight away, with the same graphs and no restart of the host. See
  [The editor's look](editor.md#the-editors-look).
- **AI Assistant settings** open one provider at a time: each is a section
  whose header says how it is set up, the provider asked first starts open,
  and the list scrolls so everything can be reached on a small screen. See
  [Signing in](editor.md#signing-in).

### The graph

- **The graph has no edge.** Pan, frame and go to nodes as far out as you
  like; the canvas grows as you go.
- **Renaming an attribute renames the tokens that use it**, and
  **parenting a node keeps its instances pointed at it**, both undoable.
  **Update Tokens on Attr Rename** and **Update Instance Paths on Parent**,
  in **Edit > Preferences > Editing**, turn them off. See
  [Renaming an attribute](graphs.md#renaming-an-attribute) and
  [Parenting an instanced node](composition.md#parenting-an-instanced-node).
- **Sub-graphs**: **Open Sub-graph** (`Ctrl+Shift+G`) opens the graph a
  sub-graph node runs, and the Property Editor lists that graph's world
  attributes the node does not set yet. See
  [Sub-graph nodes](composition.md#sub-graph-nodes).
- **New graph from the tabs**: a **+** after the last tab, or a double
  click on the empty bar beside the tabs, makes a new graph. See
  [Tabs](editor.md#tabs).
- **Bookmarks** save a view of the graph under a name, with `Ctrl+B`, and
  `Ctrl+1` to `Ctrl+4` go back to the first four. They are saved with the
  graph. See [Moving around](editor.md#moving-around).
- **Pan with `Space`** and a left drag, for a trackpad or a mouse without a
  middle button, and a graph is **framed when it opens** (**View > Frame
  All on Open**). See [Moving around](editor.md#moving-around).
- **Layout Nodes** (`Shift+L`) lays nodes out by the order they run in. See
  [Laying out nodes](editor.md#laying-out-nodes).
- **Snapping**: a dropped line snaps to the nearest plug that can take it,
  and grid snapping goes to the nearest grid line. See
  [Lines between nodes](editor.md#lines-between-nodes).
- **Push Positions to Target Layer** gives a lower layer the layout you
  see. See
  [Pushing positions to a lower layer](editor.md#pushing-positions-to-a-lower-layer).
- The **world node** can be copied and pasted onto another graph or layer.
  See [Deleting and pasting nodes](editor.md#deleting-and-pasting-nodes).
- **Ignore Breakpoints**, in the Execute menu and on the toolbar, lets runs
  go straight through breakpoints without removing them. While it is on,
  breakpoints are drawn as a red outline in the graph, the Outliner and the
  Build View. See [Running nodes](editor.md#running-nodes).
- When a build fails, the editor **dings and flashes** in the taskbar or
  Dock if it is behind another window. See
  [Running nodes](editor.md#running-nodes).

### Layers and files

- **Layer toggles are icons** with tooltips: display layer, mute, solo,
  lock and the new eye. See [Layer toggles](editor.md#layer-toggles).
- **Hide a layer in the graph** with the eye, or **Hide In Graph** on its
  menu. Its nodes, lines and backdrops leave the graph a node at a time,
  while the layer still composites and runs. See
  [Hiding a layer in the graph](editor.md#hiding-a-layer-in-the-graph).
- Shift click a layer's arrow to open or close every layer under it. See
  [Layer Manager](editor.md#layer-manager).
- **Files changed on disk**: saving over a file something else changed
  asks first, and coming back to the editor offers to reload. See
  [Files changed on disk](editor.md#files-changed-on-disk).
- **References that cannot be found** are listed in a notice with **Edit
  References...**, and a graph saved by a **newer nxt** asks before it
  opens. See [Reference Editor](editor.md#reference-editor).
- **Env files** set environment variables as nxt starts, in the editor, in
  a host and in a headless run, and **Edit > Preferences > Environment
  Variables** edits them. See [Env files](extensions.md#env-files).
- A file you pick under one of your `NXT_FILE_ROOTS` is stored relative to
  that root, and one in a folder an env file variable names is stored from
  that variable. See
  [How references are found](composition.md#how-references-are-found).
- **Any language**: graphs, logs and every other file nxt reads or writes
  are UTF-8, so names, comments and code can be in any language on any
  system. See [NXT file spec](file_format.md#nxt-file-spec).

### Outliner, Build View and Property Editor

- **Drag rows in the Outliner** to parent their nodes. See
  [Outliner](editor.md#outliner).
- In the **Build View**, a selected node's name stays readable when its
  breakpoint is set. See [Build View](editor.md#build-view).
- The Property Editor can **filter attributes**, **copy and paste
  attributes** between nodes, **complete node paths and tokens** as you
  type, and shows where **running changed an attribute's type**. The
  **Position** fields move every selected node. See
  [Filtering attributes](editor.md#filtering-attributes),
  [Copying and pasting attributes](editor.md#copying-and-pasting-attributes),
  [Completing paths and tokens](editor.md#completing-paths-and-tokens),
  [Types changed by running](editor.md#types-changed-by-running) and
  [Position](editor.md#position).
- Typing in the Property Editor's table jumps to the row starting with
  what you typed. See [Hotkeys](hotkeys.md).

### Code Editor and completion

- **Fold** indented blocks from the gutter or with `Ctrl+Shift+[` and
  `Ctrl+Shift+]`. See [Folding](editor.md#folding).
- **Drop files** into the code to write a `${contents::}` token for them.
  See [Dropping files](editor.md#dropping-files).
- **Completion keeps up with typing**, offers a node's inherited and
  instanced attributes after `self.`, and after a build completes
  `STAGE.` and `self.` on what the build left there. See
  [Completion](editor.md#completion) and
  [STAGE and self after a build](editor.md#stage-and-self-after-a-build).
- **Optional Components** (**Edit > Preferences > Optional Components**) installs Qt
  and jedi in any host, with no restart. See
  [Optional Components](optional_components.md).
- A `#` inside a string is no longer coloured as a comment, the Code Editor
  keeps its scroll when the same node is shown again, and the Output Log
  keeps following new text, with a **Wrap Lines** option. See
  [Highlighting](editor.md#highlighting) and
  [Property Editor, History View, Output Log and Workflow Tools](editor.md#property-editor-history-view-output-log-and-workflow-tools).

### Hosts

- `NXT_NO_MENU=1` leaves nxt's own menu out of Maya, Blender and Unreal.
  See [Leaving the nxt menu out](install.md#leaving-the-nxt-menu-out).
- The Maya module ships jedi, so Python Analysis works from the zip.
- **Run a graph headless** in Maya, Blender or Unreal, from a shell or a
  farm, with one runner for each host that takes the same arguments, or
  from a graph with the builtin sub-graph nodes that start the host. See
  [Running Graphs Headless](headless.md).
- The editor's title shows the name of the Maya scene or `.blend` file its
  host has open, `nxt maya [rig_v012.ma]`, so the editors of two sessions
  of the same host can be told apart in the taskbar. See
  [Installation](install.md).

### Fixes and speed

- **Save** saves the graph you are looking at, not a layer right clicked
  earlier.
- A big value stored by a build no longer stalls the editor afterwards,
  and during a build only the nodes whose state changes are redrawn.
- The code editor's completion list opens under the line, with its names
  starting where the word being completed starts.
- Clicking into a node's code and away without typing no longer adds an
  undo step, marks the layer as unsaved, or copies inherited code onto the
  target layer.
- The mini map leaves out the backdrops of a layer hidden in the graph, as
  it does that layer's nodes.
- Two quick clicks on a Layer Manager toggle count as two: the second was
  taken for a double click and did nothing.
- The Environment Variables page shows its Name and List column titles
  whole in an empty table, and a long file path no longer makes it wide.

### nxt_core

- Graphs and the files they read are **UTF-8**, so they open in any
  language on any system. Older files that are not UTF-8 still open.
- An **instance path that loops** back to the node or its ancestors is
  logged and ignored rather than hanging the comp, and an exec chain that
  loops is stopped. See [Instancing](composition.md#instancing).
- Running a node no longer copies the world node's attributes for every
  node, so a big value on the world node no longer slows every node after
  it.
- `${/node._code}` gives a node's code as text. See
  [Tokens](graphs.md#tokens).
- Loading a file warns about a **node path written twice**. See
  [NXT file spec](file_format.md#nxt-file-spec).
- A node's enabled state shows straight away, without a recomp.
- `nxt.execute_graph` closes its session's log when the graph is done, so
  running graphs one after another no longer keeps a log file open per run
  or writes each line several times. Sessions made in the same second get
  a log file each.
- The builtin `sub_graphs.nxt` graph has nodes that run a graph headless
  in Maya, Blender or Unreal. See [Running Graphs Headless](headless.md).
- For tools: `rename_node_attr(refactor=True)` updates the tokens that use
  a renamed attribute, `retarget_instance_paths` keeps instance paths on
  nodes that were parented elsewhere, env files are read as nxt starts, and
  a file saved by a newer nxt raises `NewerFileError` unless it is opened
  inside `nxt_io.allow_newer_files()`.

## nxt_editor 4.8.0

- **Align and distribute** nodes and the points on their lines: Align
  Left, Center, Right, Top, Middle and Bottom, and Distribute
  Horizontally and Vertically, from **Align** in the right click menu, a
  new Align button on the toolbar, or `Shift+W`/`A`/`S`/`D` and
  `Alt+Shift+W`/`S`/`A`/`D`. See
  [Aligning nodes and points](editor.md#aligning-nodes-and-points).
- **Points turn with the line**: a curved line runs smoothly through each
  point in the direction it is going, instead of looping back round it.
  See [Lines between nodes](editor.md#lines-between-nodes).
- **Select All** has an icon on the toolbar, and its tooltip shows its
  shortcut.

## nxt_editor 4.7.0

- The [Instance View](editor.md#instance-view) marks the node it is drawn
  from with a target at the end of its name, the same target as on
  **Follow Selection**. It moves to whichever node you show, from the
  graph, the Outliner, **Show Selected** or a double click in the view.

## nxt_editor 4.6.1

- Only proxy nodes are striped again, as before 4.6.0: nodes made by an
  instance that have nothing of their own yet. An instance, or a node that
  overrides anything its instance gives it, looks like any other node, in
  the graph and the Outliner. See [How nodes look](editor.md#how-nodes-look).

## nxt_editor 4.6.0

### A new look, the same everywhere

The editor is drawn in neutral dark greys, so the only color on screen is
your layers'. Nodes are rounded cards in their layer's color with white
names, a selected node has an amber outline, and proxy nodes, made by an
instance and not yet changed, are striped. It ships its own fonts and colors, so it looks the same on every
platform and in every host. See [How nodes look](editor.md#how-nodes-look).

### Outliner

**Window > Outliner** lists the graph's nodes as a tree, grouped by the
start point whose build runs them. Rows show their layer colors, start,
skip and break points, and work like their nodes in the graph: hotkeys,
double click to collapse (`Shift` for everything below, or for a whole
group), `F2` to rename, and the graph's right click menu. See
[Outliner](editor.md#outliner).

### Instance View

**Window > Instance View** shows a node's instance connections and nothing
else: what it instances from and everything that instances it. It can
follow the selection, and select what you pick in it in the graph and the
Outliner. See [Instance View](editor.md#instance-view).

### Finding nodes

[Find Node](editor.md#find-node) (`/`) and the Outliner's search find
nodes by name, with `*` for anything, commas between names, and a `/` to
match the whole path. `Enter` in Find Node selects and frames every match.

### Lines and backdrops

- [Lines between nodes](editor.md#lines-between-nodes) can be curved,
  routed through points you drag, and broken with a right click.
- [Backdrops](editor.md#backdrops) (`C`) put a colored, titled box behind
  a group of nodes, and move them together.
- **Window > Stage View** hides the graph to give the space to the docks.

### Colors

- **Change Color** picks any color, and the layer keeps exactly that color.
- [Layer Color View](editor.md#layer-color-view) sets how layer colors
  are shown to you: as they are, darker where too light for white text, or
  every hue at one lightness and chroma. It is your preference only.
- **View > Options > Neutral Property Text** shows the Property Editor's
  attributes in neutral text, with each layer's color in the row header.

### Faster on big graphs

Opening a large graph takes about half as long, moving and panning are
smoother, and a hidden graph, Outliner or Instance View does no work until
it is shown again.

### Smaller changes

- The toolbar has its own buttons for [running](editor.md#running-nodes)
  the selected nodes, from them, or their hierarchy.
- The Build View outlines the selected node in amber and the hovered one in
  white, and keeps the next node to run red.
- Break and skip points work on graphs that have not been saved yet.
- The list of layers to save on close shows their colors and checkboxes.

## nxt_editor 4.5.0

- **[AI Assistant](editor.md#ai-assistant)**, an opt in panel to chat with
  Claude, OpenAI, Grok or a local model about the open graph. It looks over,
  searches, changes and runs the graph with tools, and shows each step it
  takes. Every chat is kept, to go back to, pin or delete.

  ![The AI Assistant](images/ai_assistant.png)
- **The editor looks the same in Maya as it does on its own.** The workflow
  buttons, tabs and panels lost their styling in a host.
- **Every change to a layer shows on it as it happens.** Taking something off
  a node, such as a local attribute, now marks the layer as changed in the
  Layer Manager too.
- **Stop puts the build back.** Stopping a build no longer empties the build
  list or leaves the editor looking like it is still running, and in Maya
  the next node no longer runs after Stop.
- **Saving a layer no longer fails on a damaged editor cache** ("Ran out of
  input"). The editor's prefs and cache are written whole, and one that can
  not be read is put right on the next save.

## nxt_editor 4.4.2

- **[Show in Explorer](editor.md#show-in-explorer)** on a layer's right
  click menu opens the folder it is saved in, with its file selected:
  Explorer on Windows, the Finder on a Mac, the file manager on Linux.

## nxt_editor 4.4.1

- **Maya's fonts are left alone again.** Opening the editor in Maya no
  longer changes the font of Maya's own windows, such as the node editor's
  tab search.
- **Code Editor Data State Overlay** is now under **View > Options**, and
  the editor remembers whether you turned it on or off.

![The nxt editor with the mini map in the corner of the graph](images/editor_overview.png)

## Editor

### A code editor that works like a code editor

The code editor picked up the tools you would expect from a text editor. All
of them only apply while the code editor has focus, and all of them can be
rebound in the [Hotkey Editor](hotkeys.md#code-editor).

- **Find and replace** (`Ctrl+F` / `Ctrl+H`) floats over the top right of the
  code, with a match count, next and previous (`F3` / `Shift+F3`) and toggles
  for match case, whole word and regular expressions.
- **Go to line** (`Ctrl+G`) previews the line as you type, and `Esc` puts the
  cursor back where it was.
- **Line editing**: duplicate (`Ctrl+Shift+D`), move (`Alt+Up` / `Alt+Down`)
  and delete (`Ctrl+Shift+K`) lines, and expand the selection from word to
  line to everything (`Ctrl+D`).
- **Highlighting** of every use of the word under the cursor, and of the
  bracket next to the cursor and its partner.
- **Completion** (`Ctrl+Space`) offers python builtins, names from the modules
  the compute imports, the node's attributes and `${}` tokens, and words
  already in the compute. Each source can be switched on or off under
  **Options > Autocomplete**, along with suggestions while you type.
- **Auto-pairing**: typing `(`, `[`, `{`, `"` or `'` adds the closing
  character, typing a closer that is already there steps over it, and
  typing an opener with text selected wraps the selection.
- **Syntax highlighting** colours every match on a line. Before, a line
  with two tokens or two strings only had the first one coloured.

See [Code Editor](editor.md#code-editor).

### Tokens you can hover and follow

![Hovering a token shows its value](images/code_editor_token_hover.png)

In Raw View (`Q`), hover a `${}` token in the code editor to see what it
resolves to, and `Ctrl+click` a token that reads another node's attribute to
select and frame that node in the graph. See
[Following tokens](editor.md#following-tokens).

### Completion that knows what a compute can use

![Completing another node's attributes](images/completion_node_attrs.png)

- What the world node imports completes in every node, because every
  compute can use it.
- The names nxt gives every compute complete without an import: `STAGE`,
  `self`, `w`, `execute`, `nxt_path`, `ExitNode`, `ExitGraph` and `types`.
- Inside `${/` the node paths in the graph complete, and after a node path's
  dot its attributes, each as a whole token.
- **Host Modules**, a new source: in Maya, `cmds`, `om`, `pm` and the other
  usual short names complete before any import line is written, and so do
  `unreal` in Unreal and `bpy` in Blender. Only modules the host has
  already loaded are offered, so nothing is imported to complete them.
- **Python Analysis (jedi)**, a new optional source: with
  `pip install nxt-editor[completion]`, completion after a dot knows what a
  call returns or a variable holds.

See [Completion](editor.md#completion).

### Docks

- Double click a dock's tab, where docks are tabbed together, to float it.
  Drag a floating dock back in, or double click its title bar to dock it
  again.
- **View > Reset Layout** puts every dock back where a fresh install has it.

See [Docks and layout](editor.md#docks-and-layout).

### Editing layer references

Right click a layer in the Layer Manager and choose **Edit References...** to
add, remove, retype and reorder what that layer references, without opening
the file in a text editor. Paths can be typed exactly as you want them
stored (for example with an environment variable in them), or picked with a
file browser. A **resolved** toggle shows where each reference lands on this
machine, and references that cannot be found are kept and marked rather than
dropped. See [Reference Editor](editor.md#reference-editor).

### Reload Source

Somebody else saved a file your graph is built on? **Reload Source...** (on a
layer's right click menu and in the **File** menu) re-reads that layer, and
as many of the layers it references as you choose, from disk, and
composites the graph again. It can be undone. See
[Reload Source](editor.md#reload-source).

### Mini map

A mini map in the bottom right of the graph shows the whole graph and where
the view is inside it. Click or drag in it to move the view. Toggle it with
**View > Toggle Mini Map** or `Ctrl+M`. See [Stage](editor.md#stage-view).

### Build view

- A **find** button next to the play button scrolls the build to the node
  selected in the graph, and tells you when the selected node is not part of
  the build.
- The build stays current as the graph changes: disabling, deleting,
  renaming, re-parenting or reconnecting a node updates it straight away.

See [Build View](editor.md#build-view).

### Smaller changes

- Deleting a node no longer leaves a "ghost" of it in the graph and the
  build view.
- Pasting several nodes is a single undo.
- Nodes no longer animate open by default, which makes opening a node with
  many children noticeably faster. The **Animate Nodes** action turns the
  animation back on (see [Stage](editor.md#stage-view)).
- A graph is only composited and drawn when its tab is first selected, so
  opening many files at once is faster.
- Renaming a node no longer rebuilds the whole graph when it does not need
  to, and a renamed node keeps its position.
- When a build is set up, a cached runtime that no longer matches the graph
  is rebuilt automatically instead of stopping the build part way through.
- An uncaught error from nxt only opens a dialog when an editor window is
  visible. In batch or headless sessions it is printed instead, so a host
  running a graph in the background never stops on a dialog nobody can see.
- The editor no longer needs `pyside6-rcc` (or any other compiled step) to
  build its icons and styles, so the same release works on every platform
  and host.

## Host integrations

- **Maya**: Maya 2025, 2026 and 2027 are supported. The `nxt_ui` command
  takes `-path` to open graphs, `-close` and `-reload`, and reuses the editor
  that is already open. Graphs can be run in Maya standalone from the
  command line with `run_maya_graph.py`, including a start node and
  parameters, and the builtin `_maya_standalone_graph` node now passes its
  `_start_node` on. See [Maya](install.md#maya).
- **Unreal**: a plugin for Unreal 5.4 to 5.8 that carries its own copy of nxt,
  nxt_editor and Qt.py, with an **nxt** menu and a one click
  **Install Qt (PySide6)**. See [Unreal](install.md#unreal).
- **Blender**: an add-on for Blender 4.2 and newer with an **NXT** menu:
  Open Editor, Close Editor, Run Graph, Run Last Graph, Reload Code and
  Install Qt. See [Blender](install.md#blender).
- Hosts that do not ship Qt install PySide6 once into `~/nxt/deps`, or into a
  shared folder named by `NXT_QT_DEPS`. See
  [Qt for Blender and Unreal](install.md#qt-for-blender-and-unreal).

## Python versions

| Package | Python |
| :------ | :----- |
| nxt-core | 3.7 to 3.14 |
| nxt-editor | 3.9 to 3.14 (PySide6 6.x, below 6.12) |

PySide6 is held below 6.12 until the editor has been tested on it.

## Core (nxt_core 0.21)

- **Faster compositing and execution.** Large graphs composite and build
  substantially faster, with identical results.
- **One order for finding a reference, everywhere.** A reference written
  as an absolute path is used as it is. Any other reference is looked for
  under the folders in `NXT_FILE_ROOTS` first, and then relative to the
  layer that holds it, never relative to wherever the editor was started.
  A file under a root therefore wins over a file of the same name beside
  the layer, which is what lets a working copy listed in `NXT_FILE_ROOTS`
  stand in for the published one. Adding a reference in the editor now
  finds the same file that opening the graph does. See
  [How references are found](composition.md#how-references-are-found).
- **References that cannot be resolved are kept.** Previously a reference to
  a file that could not be found was dropped from the layer, and saving the
  layer wrote it out without the reference. Now it is kept exactly as
  written, so a graph opened on a machine that cannot see a share no longer
  loses its references when saved.
- **Reloading layers from disk** (`Stage.reload_layers`), which is what
  [Reload Source](editor.md#reload-source) is built on. A reference added,
  removed or reordered in the file since the graph was opened is picked up.
- **Removing a layer removes everything it brought in**, including all of its
  references, and only the reference that pointed at it.
- **Targeted renames**: renaming a node that nothing else composites against
  updates it in place instead of recompositing the stage.
- Graph parameters can enable or disable nodes for a run, for example
  `{"/node._enabled": false}`. See
  [Running a graph in Maya standalone](install.md#running-a-graph-in-maya-standalone).
