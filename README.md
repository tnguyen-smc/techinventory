# Office tech inventory (2D carousel)

Three zoom levels, one file:

1. **Room**: a top-down plan of your shelves. Hover a shelf for a mini front view (click any box in it to jump straight there). Click a shelf to zoom in. Drag shelves to rearrange; they snap to walls and to each other, with a small tip showing the distances.
2. **Shelf carousel**: each shelf shown front-on and centred. Use the arrow buttons, ← →, swipe, or the shelf chips to cycle. Neighbouring shelves peek in at the sides.
3. **Box**: click a box and it zooms to the centre, the lid opens, items pop out and a list panel slides in.

Zoom out with the mouse wheel, the − button, `Esc`, or the breadcrumbs (Room › Shelf › Box).

## Changing a shelf's layout
Right-click any compartment (or a box) on a shelf:

- Add row above / below (splits the row you clicked)
- Add column here (splits that compartment)
- Split row into N columns, Make row open (no columns), Remove column, Remove row
- Name this row, Shelf settings (size in inches, color, side of the room), Duplicate, Delete, reorder in the carousel

Rows can have different numbers of columns, and a row with no dividers is one open space.

**Edit shelf layout** (context menu or the button under the shelf) shows a blank version of the shelf. Drag the lines:
- Row lines change the heights of the two rows they sit between.
- Column lines change the widths of the two compartments beside them, per row.
- The bottom and right edges change the shelf's overall size.
- A small tip shows the new sizes and the change (for example "+2 in") with a size bar. Lines snap to other rows' dividers (a yellow guide appears), to matching row heights, or to half inches.
- `Undo` (or Ctrl/Cmd+Z) reverts any layout change.

Boxes keep their spot when you split, merge or move lines. If you remove a row or column, its boxes move into the neighbour.

## Boxes
- Drag a box to another compartment, including onto a neighbouring shelf. Hold it near the screen edge to flip the carousel.
- Right-click the floor in the room view to add a shelf, or use the **Add shelf** button.
- Search (press `/`) shows shelf, side of the room, row from the top and column from the left, then flies there and opens the box.
- On touch screens, long-press for the right-click menu. Use the + / − buttons to zoom.

## Google Sheets
1. Create a Google Sheet, then **Extensions > Apps Script** and paste `Code.gs` (replace the old version).
2. Change `TOKEN` to your own secret.
3. **Deploy > New deployment > Web app**, Execute as **Me**, Who has access **Anyone**. If you deployed v1 before, use Manage deployments > Edit > New version instead.
4. In the app, click the grey **Local only** button, paste the Web app URL and token, then **Save and connect**.

Tabs: `Room`, `Units` (each shelf's rows and columns are stored as JSON in the `layout` column), `Containers` (with a readable Location column) and `Items`. `Containers.row` and `.col` are 1-based (row 1 is the top, column 1 the left within that row).
The app saves 1.5 seconds after each change. After hand-editing the Sheet, press **Load from sheet** in the settings. The URL and token stay in your browser only.

Note: this version replaced the earlier 3D one. Its sheet layout differs, so the first sync with the new script rewrites the tabs.

## Deploy on GitHub Pages
Put `index.html` in a repo, then **Settings > Pages > Deploy from a branch > main / root**. There is no build step and no external scripts.
