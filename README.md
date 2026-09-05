# DDO Layout Editor

A community open-source browser-based editor for **Dungeons \& Dragons Online** `.layout` files.

*Note:* Use at your own risk.

DDO stores three unrelated things in one settings file: where every HUD panel sits on screen, your chat shortcuts (aliases), and a large pile of game options. In game you can only change them one at a time, by hand, and hotbar alignment is close to impossible. This tool opens that file, lets you edit all three, and writes it back in exactly the form the client expects.

**Live:** [**https://longfreename.github.io/ddo-layout-editor/**](https://longfreename.github.io/ddo-layout-editor/)

Everything runs locally in your browser. Your file is never uploaded anywhere — there is no server, no account, and no analytics.

---

## Getting started

1. **Export from the game.** In DDO's chat box type `/ui layout save myui.layout`. The game reports where it saved it — normally `Documents\\Dungeons and Dragons Online\\UI\\layouts`.
2. **Open it with this layout editor.** Use **Open .layout**, or drag the file anywhere onto the page.
3. **Edit, then save back** into that same folder.
4. **Reload in game:**

```
   /alias clear
   /ui layout load myui.layout
   /alias list
   ```

   Clear first, or you may hit the fifty-shortcut limit partway through loading.

An example layout is loaded on first visit, so you can click around freely — nothing here can touch your game until you save a file and load it yourself.

---

## What it does

### Screen layout

* **Drag-and-drop HUD editor** with live preview — drag to move, pull a corner to resize, arrow keys to nudge. Positions are stored as a proportion of the screen, so the preview matches any resolution.
* **Snapping and grids** — snap to grid (20/40/80 divisions), to screen edges, or to other panels; *Line up to grid* and *Find overlaps* clean up a messy layout in one click.
* **Alignment tools** for multi-select (Ctrl-click or drag a box): align edges, stack in a neat row or column with a fixed gap, distribute with equal spacing, match widths/heights, and mirror left↔right or top↔bottom to build a symmetrical layout.
* **Hotbar arranging** — the reason this tool exists. Pick which of the 20 hotbars are in the layout, then apply a bulk arrangement: rows stacked from the bottom (centred, left or right), upright bars along either edge, or split rows-and-column, with a configurable gap.
* **Auto-arrange presets** — Classic, Raid, Caster, Minimal and Ultrawide starting layouts, all undoable.
* **Resolution rescaling** — panels are stored in pixels, so a layout built for 2560×1440 comes out wrong on 1920×1080. Rescale between any two resolutions, keeping each panel the same physical size and the same distance from its nearest edge.
* **Background screenshot** — drop in your own screenshot and lay panels out against your actual game view, with 16:9, 16:10, 21:9 and 4:3 framing.
* **Layout checks** — flags panels filed under the wrong Layout group (the game only looks for a panel in its own group), panels with no size, panels running off the edge, and hotbars saved twice. Nothing changes unless you press the fix button beside the warning.
* Full **undo/redo**.

### Chat shortcuts

* Table view of every alias in the file, with an editor for the selected row.
* **Compose without codes** — pick the destination channel (Party, Guild, Raid, Say, Emote, Shout, Advice, or whatever your chat tab is pointed at), then highlight words and click a colour. The escape codes are generated for you; *Show the code* reveals the raw text.
* **Starter and raid speech sets** for callouts, loot rules, ready checks and mechanics reminders.
* **Slot counter** against the game's hard limit of 50.
* **Shadowing check** — warns when a short alias will swallow a longer one (`;ro` eating `;roar`), and avoids the classic stray-space-before-a-coloured-word mistake entirely.

### Game settings

* **126 settings** in plain English, grouped into categories: floating combat text, combat text colours, chat channel colours, combat feedback, targeting, health and party bars, chat and social, hotbars, map and interface. Each shows its real setting key, a description of what it does, and a revert arrow.
* **Changed only** filter and **Revert all**.
* **Colour profiles** — DDO default (copied from files the game itself wrote, so a true reset), High contrast, Colour-blind friendly, Soft, Ember, Arctic, Healer's view and Neon. A profile only touches colours already present in your file and preserves each one's transparency. Save your own profiles in the browser and apply them to another character's file.
* **Tune every colour** — shift hue, saturation and brightness across all colours, chat channels only, or combat text only, with a live in-game-style preview. Slide back to zero and nothing has changed.
* Warns when several settings share the same colour, so distinct events look alike in play.

### File handling

* Open, save, **start fresh**, **copy the file text** to the clipboard, and **back up the original** before experimenting.
* **Import from…** another layout file — take just the chat shortcuts, or just the screen layout, from a file you already like.
* Save uses `%c` (character name) and `%r` (resolution) filename conventions, and updates the resolution in the filename after a rescale.

---

## Known limits (the game's, not the editor's)

* **Moving works.** Anything the game saved a position for can be put where you like.
* **Resizing is inconsistent.** Some panels resize, some enforce a minimum, some ignore it and snap back on load. Hotbars size themselves from their slot count, not from this file.
* **Some windows are never saved** — the main menu, the store, the expanded map and dialogue windows keep no position in the file, so they don't appear here.

Keep a backup of a layout you're happy with before experimenting. Saving under a second name costs nothing.

---

## Technical notes

* Single self-contained `index.html` — no build step, no dependencies, no framework.
* Runs entirely client-side; the file never leaves your machine. Saved colour profiles live in your own browser storage.
* Mobile friendly.
* Hosted on GitHub Pages from the repository root.

To run it locally, clone the repo and open `index.html` in a browser, or serve the folder with any static file server.

## 

