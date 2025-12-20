---
name: ascii-art
description: Generates branded ASCII art illustrations for Laterally blog posts. Minimal line-drawing aesthetic using box-drawing and simple characters.
---

# ASCII Art Skill

Generate abstract ASCII art illustrations for Laterally blog posts. Text-based art that renders in code blocks, matching the technical, minimal brand aesthetic.

---

## Brand Alignment

ASCII art should feel like:
- A diagram sketched in a terminal
- Something a developer might draw to explain a concept
- Technical, intentional, sparse
- Part of the same visual system as the SVG headers

---

## Character Palette

### Primary Characters (use most)

```
Box Drawing:
─  │  ┌  ┐  └  ┘  ├  ┤  ┬  ┴  ┼

Rounded Corners:
╭  ╮  ╰  ╯

Arrows:
→  ←  ↑  ↓  ⟶  ⟵

Dots/Nodes:
●  ○  •  ·

Dashes:
╌  ╎  ┄  ┆  - - -
```

### Secondary Characters (use sparingly)

```
Double Lines:
═  ║  ╔  ╗  ╚  ╝

Brackets:
[ ]  < >  { }  ( )

Simple ASCII:
|  -  +  *  /  \  _
```

---

## Composition Rules

### Canvas
- Width: 60-80 characters max (fits code blocks on mobile)
- Height: 15-30 lines typical
- Generous whitespace - don't fill the canvas

### Layout
- Center primary elements
- Maintain 2-4 character margins
- Use blank lines to create vertical breathing room
- Left-to-right flow for processes

### Visual Weight
- Box-drawing characters for structure
- Simple ASCII (`-`, `|`) for secondary elements
- Dots for nodes and emphasis
- Arrows for direction/flow

---

## Abstract Representation Guide

| Concept | ASCII Form |
|---------|------------|
| **Device** | Rounded box `╭──╮` `│  │` `╰──╯` |
| **Terminal/Code** | Brackets with lines `[────]` |
| **Data** | Stacked short lines |
| **Connection** | `───→` or `─ ─ ─→` (dashed) |
| **Server** | Rectangle with internal lines |
| **Flow** | `──→──→──→` or dots `● ─ ● ─ ●` |
| **Node** | `●` or `○` or `(●)` |
| **Async/Wireless** | Dashed `─ ─ ─` or `· · ·` |
| **Branching** | `├──` `│` `└──` |
| **Container** | `┌─────┐` box |

---

## Templates

### Simple Flow (left to right)

```
    ╭─────╮          ┌───────┐          ╭─────╮
    │     │   ───→   │       │   ───→   │     │
    ╰─────╯          └───────┘          ╰─────╯
     input            process           output
```

### Connection with Nodes

```
         ┌─────────────────────────────┐
         │                             │
    ●────┼────●────────●────────●────┼────●
         │                             │
         └─────────────────────────────┘
```

### Branching Process

```
                    ┌───────┐
                ┌───│   A   │───┐
                │   └───────┘   │
                ▼               ▼
           ┌───────┐       ┌───────┐
           │   B   │       │   C   │
           └───────┘       └───────┘
                │               │
                └───────┬───────┘
                        ▼
                   ┌───────┐
                   │   D   │
                   └───────┘
```

### Device to Server

```
    ╭──────╮                         ┌──────────┐
    │      │                         │ ──────── │
    │      │  ─ ─ ─ ─ ─ ─ ─ ─ ─ ─→  │ ──────── │
    │      │                         │ ──────── │
    ╰──────╯                         └──────────┘
     phone                              server
```

### Terminal Window

```
    ┌─────────────────────────────────────┐
    │  $ command                          │
    │  ────────────────────               │
    │  ──────────────                     │
    │  ────────────────────────           │
    │  ──────────                         │
    │  █                                  │
    └─────────────────────────────────────┘
```

### Network/Nodes

```
                         ○
                        /│\
                       / │ \
                      ○  ○  ○
                       \ │ /
                        \│/
                         ●
```

---

## Example: Mobile Dev Workflow

```
    ╭──────╮                                    ┌──────────┐
    │      │                                    │ ──────── │
    │  ◉   │  ─ ─ ─ ─ ─ ●─────────────────●───→│ ──────── │
    │      │            │                 │     │ ──────── │
    ╰──────╯            │   ┌─────────┐   │     └──────────┘
     phone              └──→│ < · · > │───┘        server
                            └─────────┘
                              tmux
```

---

## Usage in Posts

Wrap in triple backticks (no language specified for plain rendering):

````markdown
Here's how the system connects:

```
    ╭──────╮         ┌──────────┐
    │      │  ────→  │          │
    ╰──────╯         └──────────┘
```

The phone connects directly to...
````

Or use `text` language hint if syntax highlighting causes issues:

````markdown
```text
    ╭──────╮         ┌──────────┐
    │      │  ────→  │          │
    ╰──────╯         └──────────┘
```
````

---

## Generation Process

### 1. Identify Core Elements
What 2-4 things need to be represented?

### 2. Choose Relationships
- Sequential flow → horizontal arrows
- Hierarchy → vertical branching
- Network → centered node pattern
- Container → boxes within boxes

### 3. Sketch Layout
- Place primary element left or center
- Add connections
- Add secondary elements
- Ensure whitespace balance

### 4. Refine Characters
- Use rounded corners `╭╮╰╯` for organic/device shapes
- Use square corners `┌┐└┘` for technical/system shapes
- Use dashed lines for wireless/async
- Add labels below if needed (lowercase, minimal)

---

## Quality Checklist

- [ ] Fits within 70 characters wide
- [ ] Has breathing room (not cramped)
- [ ] Uses consistent character style throughout
- [ ] Abstract, not literal illustration
- [ ] Would make sense in a terminal/code context
- [ ] Relates to topic without labeling everything
- [ ] Renders correctly in monospace font

---

## Do Not Include

- Literal drawings (no ASCII faces, detailed objects)
- Color codes or ANSI escapes
- More than 3-4 distinct elements
- Labels for everything (let the diagram speak)
- Decorative borders or frames around the whole thing
- Complex curves or diagonal lines (hard to render cleanly)

---

## When to Use ASCII vs SVG

| Use ASCII | Use SVG |
|-----------|---------|
| Inline in blog post body | Header/hero image |
| Explaining a specific concept | General topic representation |
| Code-heavy technical posts | All blog posts (standard) |
| Quick diagram in the flow of text | Social media preview |

Both can be used in the same post—SVG header at top, ASCII diagrams inline where helpful.
