# Atlas — user guide

A node-and-link map editor in a single HTML file. Open `editeur-carte.html` in a browser: no
install, no server.

---

## 1. The principle: nothing is predefined

On first run the map is blank and **no type exists**. You create your types as you go, and the
legend builds itself along the way. A type is a name bound to an appearance:

- **Place type** — a symbol (one of twelve) or an imported image, a colour, a size, a label
  style, and the list of parameters offered for that type.
- **Link type** — a line style (one of twelve), a hue, a label style, and its own parameter list.

The name you give a visual *becomes* the type. It appears immediately in the toolbar and in the
legend, with a count of the elements using it.

---

## 2. Dropping places

- **Click the background** → the *New place* dialog: name, type, parameters, label placement.
- If no type exists yet (or if you pick **New type…**), type creation slots in first, then you
  return to the place dialog with whatever you had already typed.
- **Drag a place** to move it; its links follow.
- **Click a place** to start a link. **Click the same place again** to open its sheet and change
  its name, type or parameters. `Esc` cancels the pending link.
- **Double-click** also opens the sheet. **Right-click** or `Delete` while hovering removes the
  place and its links.

---

## 3. Drawing links

- Click a first place, then a second. While you move, a ghost line follows the cursor and shows
  the live distance.
- The *New link* dialog asks for the type, the parameters and the curvature.
- **Click a link** to select it: a brass handle appears at its apex. Drag it perpendicular to
  deepen or flip the curve; it snaps back to a straight line near zero.
- **Click an already selected link again** to **split** it at that point: a place is dropped on
  the line (you name it and give it a type), then the cost of each half is asked, prefilled from
  the original link. The original curvature is divided exactly between the two halves, and a new
  link starts from the junction. To deselect without splitting: `Esc`, or click the background.
- **Double-click** a link to open its sheet. **Right-click** or `Delete` removes it.

---

## 4. Parameters

Nothing is imposed: every place and every link carries as many **name / value** pairs as you
want — cost, duration, garrison, passable season, note. The names you type are remembered on the
type: the next element of that type offers them straight away, empty.

The value drawn on the map is the **first filled parameter**, in the type's field order. The
hover callout lists them all.

A type dialog has its own field list too, so you can set the parameters up front. A new link
offers "Cost" by default — remove it if you don't need it.

---

## 5. Link line styles

Twelve styles, each available in eight hues:

| Style | Look |
|---|---|
| Tie trail | pale band crossed by dark ties, shaky stroke |
| Wide track | same idea, heavier |
| Dotted / dashed path | round-capped dots or dashes |
| Road | solid stroke with a casing |
| Paved way | solid stroke striped with cobbles |
| Railway | thin rail and regular sleepers |
| Chain | round-capped links |
| Watercourse | wide stroke, wider wobble, with a highlight |
| Thin line | hairline |
| Barred way | dashes cut by bars |
| Arrowed way | dashes ending in a head |

The shaky look comes from an SVG turbulence filter applied to the stroke.

## 6. Place symbols

City, capital, village, hamlet, region, mountain, forest, tower, ruin, harbour, crossroads,
marker — or **your own image** (PNG, JPG, WebP), automatically downscaled to 256 px so the
exported file stays light. A slider sets the symbol size on the map, independent of zoom.

---

## 7. Labels

**Style belongs to the type** (type dialog, *Label style* section):

- seven typefaces: condensed display, roman capitals, old press, Garamond, uncial, typewriter,
  system sans;
- bold, italic, underlined, uppercase;
- letter colour and outline colour, with a *no outline* option;
- size, and a live preview.

The first swatch of both palettes, half dark and half light, means **follows the theme**: the
label then tracks the light or dark theme. An explicitly chosen colour never moves.

**Placement belongs to the element**:

- **Automatic placement** (the default): twelve orientations at three distances are tried, and
  the first that clears every other label, symbol and line wins. Places are placed before links.
- **By hand**: grab the label and swing it around its place, or around its link's apex. It
  switches to manual placement on its own. The *Orientation* and *Distance* sliders in the sheet
  do the same to the degree.
- The toolbar's **Auto placement** button puts the whole map back on automatic.
- A single click on a label opens the matching element.

---

## 8. The backdrop

- **Backdrop → Image…** loads an image; it is fitted to the screen and alignment mode opens.
- While aligning: dragging moves the image, the sliders set its **scale** (5 to 400 % of its
  true size) and its **opacity**. *Fit* reframes it, *Done* closes the mode and gives clicks back
  to place creation.
- **Grid** hides the ruling. The fine grid fades out on its own below 45 % zoom.

Backdrop scale is independent of view zoom: align once, then navigate freely without shifting
anything.

---

## 9. Navigating

| Gesture | Effect |
|---|---|
| Drag the background | pan |
| Wheel | zoom at the cursor |
| Two-finger pinch | zoom and pan |
| − / + buttons | zoom by steps |
| **Fit** | bring everything on screen, backdrop included |

Range: 10 % to 400 %.

---

## 10. Theme and language

- **Light / dark theme**: one button switches everything, ruling and map ground included.
- **Language**: flag menu, French and English. Your type names stay exactly as you wrote them.

Both settings are saved with the map.

---

## 11. Resetting

The **Reset** menu offers four scopes:

1. **Clear elements** — places and links; types and backdrop kept.
2. **Reset types** — types, icons and elements: start over.
3. **Remove backdrop** — the image and its alignment.
4. **Reset everything**.

All of it stays undoable with `Ctrl+Z`.

---

## 12. Exporting and importing

The **Export** menu offers three formats:

- **PNG image** — the aligned backdrop and the elements flattened into one render, cropped to
  the content, at double resolution. Google fonts are not embedded in the rasterised SVG, so
  labels fall back to a system typeface there.
- **JSON data** — types, base64 icons, places and links with positions, curvatures, parameters
  and label placement, plus an **adjacency matrix** (`matrice.ordre` and `matrice.cellules`)
  giving the same information in tabular form. Without the backdrop.
- **Full map JSON** — the same data, with the backdrop image and its alignment.

**Import** reads all three shapes and rebuilds everything identically, custom icons included.

Data JSON structure:

```json
{
  "format": "atlas-carte", "version": 3,
  "typesLieux":   [{ "id": "nt1", "name": "Free port", "color": "#E8B04B",
                     "symbol": 9, "icon": null, "size": 56,
                     "label": { "font": "cinzel", "size": 13, "color": "auto" },
                     "fields": ["Cost"] }],
  "typesLiaisons":[{ "id": "lt1", "name": "Salt road", "trace": 0, "color": "#EADFC4" }],
  "icones":  [{ "id": "i3", "src": "data:image/png;base64,…", "w": 256, "h": 192 }],
  "lieux":   [{ "id": "n1", "typeId": "nt1", "name": "Havenport",
                "x": 320, "y": 180, "params": { "Cost": "3" },
                "label": { "auto": true } }],
  "liaisons":[{ "id": "l4", "typeId": "lt1", "a": "n1", "b": "n2",
                "curve": 0.18, "params": { "Cost": "10" } }],
  "matrice": { "ordre": ["n1", "n2"], "cellules": [[null, { "liaison": "l4" }], […]] },
  "cadre":   { "x": 0, "y": 0, "w": 1400, "h": 900 },
  "fond":    { "src": null, "x": 0, "y": 0, "scale": 1, "opacity": 0.7 }
}
```

Field names inside the file are French; they are the storage keys, not user-facing text.

---

## 13. Shortcuts

| Key | Effect |
|---|---|
| `Esc` | cancel a pending link, a selection, alignment mode or an open dialog |
| `Delete` / `Backspace` | remove the hovered element or the selected link |
| `Ctrl+Z` / `Cmd+Z` | undo (60 steps) |
| `Enter` | confirm the open dialog |
| Right-click | remove the element under the cursor |

The map is saved automatically in the browser; a backdrop heavier than 4 MB is not kept, only
its alignment is. For lasting work, export to JSON.

---

## 14. Adding a language

Every piece of interface text goes through a dictionary. Two places to edit, inside the file's
`<script>` block.

### a. Declare the language

In the `LANGS` list, add an entry: identifier, name **written in its own language**, and an SVG
flag (keep `class="flag"`).

```js
const LANGS = [
  { id:"fr", name:"Français", flag:`…` },
  { id:"en", name:"English",  flag:`…` },
  { id:"es", name:"Español",  flag:`<svg class="flag" viewBox="0 0 9 6">
      <rect width="9" height="6" fill="#AA151B"/>
      <rect y="1.5" width="9" height="3" fill="#F1BF00"/></svg>` }
];
```

The menu is built from this list: flag then name, in declaration order.

### b. Translate the keys

In the `I18N` object, add a block under the same identifier:

```js
const I18N = {
  fr: { … },
  en: { … },
  es: {
    "app.sub": "editor de mapas",
    "tb.places": "Lugares",
    …
  }
};
```

**Any missing key falls back to French automatically**, so a partial translation works: start
with the most visible keys and fill in the rest later.

### c. Key families

| Prefix | Contents |
|---|---|
| `app.` `tb.` `btn.` `menu.` | toolbar and menus |
| `hint.` `meter.` `zoom.` `calib.` | on-screen cues, counters, backdrop alignment |
| `leg.` `co.` | legend and hover callout |
| `tt.` `ti.` | tooltips and choice tiles |
| `dlg.` `pa.` | dialogs and the parameter editor |
| `ty.` `el.` `sp.` | types, elements, link splitting |
| `al.` | alerts and confirmations |
| `tr.0` … `tr.11` | names of the twelve line styles |
| `sy.0` … `sy.11` | names of the twelve symbols |
| `fo.` | names of the seven typefaces |

Two keys carry braced variables that must be kept: `el.linkSub` uses `{a}` and `{b}`,
`al.typeUsed` uses `{n}` and `{name}`.

### d. Check your work

Reload the page and pick the language from the menu: the interface re-translates without losing
the current map. The choice is stored alongside it.

To spot omissions, compare the key sets in the console:

```js
Object.keys(I18N.fr).filter(k => !(k in I18N.es));
```
