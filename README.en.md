# Mapgineer

*A place-and-link map editor in a single HTML file.*

[Version française](README.md) · [User guide](user-guide.md) · [License](LICENSE.md)

---

## Why this project

I needed to draw and edit maps: drop places, connect them, attach a cost to every route, and be
able to reopen the whole thing later and change it. I found nothing online that answered that
need — existing map editors draw scenery but no network, graph tools draw networks but look
nothing like maps, and almost none of them let you decide for yourself what a place or a path
even is.

So I built it. And since it exists, it may as well be available: if the need was mine, it is
probably somebody else's too.

![An example map made with Mapgineer](exemple-carte.png)

---

## The idea

A map, here, is a **dressed-up graph**: places, links between those places, and parameters
attached to either.

The principle everything else follows from: **nothing is predefined**. On first run the map is
blank and no type exists. You create them as you go, and the name you give an appearance
*becomes* a type — "Free city", "Salt road", "Closed pass". Each type carries its visual, its
label style and the list of parameters it offers. The legend builds itself along the way, with a
count of the elements using each type.

In practice:

- **Click the background** to drop a place; **click a place** to start a link to another.
- **Twelve place symbols** and **twelve line styles**, each in eight hues — or your own images
  as icons.
- **Free-form parameters**: as many name/value pairs as you want, remembered on the type so the
  next element offers them straight away.
- **A backdrop image** you align at the scale and opacity you want, to trace over an existing
  map.
- **Labels under control**: typeface, bold, italic, underline, letter and outline colours, and a
  placement that swings freely around its element — or settles itself so nothing overlaps.
- **Splittable links**: click one and a place drops at the intersection, then the cost of each
  half is asked.
- **Light or dark theme**, interface in French or English.
- **Three exports**: a flattened PNG, JSON data with an adjacency matrix, or the full map with
  its backdrop. Everything re-imports identically.

It all fits in one HTML file: no install, no server, no account. Open it in a browser and draw.

---

## Getting started

1. Download `mapgineer.html`.
2. Open it in a recent browser (Chrome, Firefox, Edge, Safari).
3. Click anywhere on the map: the first place, and its first type, are created in one go.

The current map is saved automatically in the browser. For lasting work, export to JSON — that
is the format that restores everything, imported icons included.

---

## What's in the repository

| File | Purpose |
|---|---|
| `mapgineer.html` | the whole application |
| `user-guide.md` | the full guide, in English, with how to add a locale |
| `guide-utilisateur.md` | the same in French |
| `LICENSE.md` | the license and the rights it grants, in detail |
| `exemple-carte.png` | the example above, made with the tool |

---

## Contributing

Translations are welcome, and they are the easiest contribution: every piece of interface text
goes through a dictionary, so a new language is one entry and one block of keys. The procedure
is at the end of the guide. Missing keys fall back to French, so a partial translation already
works.

---

## License

<a href="https://github.com/ZeroAbsolu/mapgineer">Mapgineer</a> © 2026 by
<a href="https://github.com/ZeroAbsolu">Kevin NIVA</a> is licensed under
<a href="https://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY-NC-SA 4.0</a>.

Share it, modify it, translate it: credit the author, state your changes, make no commercial use
of it, and release your versions under the same license. The maps you produce are yours. The
details are in [`LICENSE.md`](LICENSE.md).
