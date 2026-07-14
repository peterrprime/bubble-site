# Bubble Layout Editor

An interactive, metaball-rendered node graph — built as the navigation layer for a portfolio site, and as a tool for a design method I'd been doing by hand.

**[Live demo →](https://peterrprime.github.io/bubble-site/)**

![screenshot](docs/metaballs.png)

## What it is

Six nodes on an adjacency graph, rendered as glossy 3D metaballs in a WebGL2 fragment shader — circle SDFs blended with an exponential smooth-min, so near nodes join with thin liquid necks, plus a cursor droplet that merges into the field as you move. Hover a node and its sub-nodes bloom out on an auto-computed radial layout. Everything is editable live (append `?edit=1`) and exports to JSON.

No frameworks, no dependencies, no build step. One HTML file — vanilla JS, one shader, and an SVG line layer.

## Why it exists

My architecture thesis (GreenArc Biscayne) used a **bubble-adjacency algorithm** to generate building massing: take a space-program spreadsheet, overlap the programs by adjacency, scale each by square footage, and let circulation fall out of the result. I did the early passes of that by hand, in Rhino and Grasshopper.

This is that method, rebuilt as a piece of software you can actually manipulate — and then pointed at a different problem (site navigation) to see if the abstraction held.

It did. The layout engine doesn't know or care whether a node is a building program or a portfolio section.

## Features

- **Metaball field rendering** — WebGL2 fragment shader: exponential smooth-min over circle SDFs, sphere-exact fake normals, Blinn-Phong + fresnel for the glossy look; falls back to solid circles without WebGL2
- **Interactive field** — a cursor droplet (with trail) joins the field and necks into nearby spheres; idle micro-spheres drift through the composition
- **Adjacency graph** — SVG connector layer, recomputed on drag
- **Sub-node expansion** — hover a node (click in edit mode), children bloom out on a computed radial layout; siblings dim
- **Direct manipulation** — drag to move, scroll-wheel to resize
- **Persistence** — panel position persists to `localStorage`; full graph exports as JSON (`Copy main JSON` / `Download ALL JSON`)
- **Live parameter editing** — every node's `x`, `y`, `r`, `label`, `href` and per-node metaball settings are editable in-panel

## Stack

Vanilla JS. WebGL2 (raw — no Three.js). SVG. Zero dependencies.

## Status

Layout engine, editor, renderer, and routing are complete — clicking a bubble navigates to its section (Work / About / Contact pages).

---

*Peter Dravgalis — M.Arch, Florida International University*
