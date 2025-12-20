---
name: header-art
description: Generates branded abstract SVG header illustrations for Laterally blog posts. White line art on black, minimal and technical aesthetic.
---

# Header Art Skill

Generate abstract SVG header illustrations for Laterally blog posts. Every header should feel like part of a cohesive visual system—minimal, technical, intentional.

---

## Brand Specifications

### Canvas
- **Dimensions:** 1200 x 630 (OG image ratio)
- **Background:** #111111 (near-black)
- **Stroke color:** #e5e5e5 (off-white)
- **Stroke only** — no fills except background and small node dots

### Stroke Weights
| Element | Weight |
|---------|--------|
| Primary shapes | 2px |
| Default lines | 1.5px |
| Subtle/secondary | 1px |
| Background guides | 0.1 opacity |

---

## Visual Language

### Core Principles

1. **Abstract, never literal** — Suggest concepts through geometry, don't illustrate them
2. **Sparse composition** — Embrace negative space; every line must earn its place
3. **Technical aesthetic** — Evokes engineering, precision, systems thinking
4. **Horizontal narrative** — Left-to-right flow when depicting process or connection

### Composition Rules

- Primary elements centered vertically (y: 280-380)
- Maintain 80-120px margins on all edges
- Create rhythm through repetition with variation
- Use opacity (0.3-0.6) for secondary elements
- Subtle grid lines at 0.1 opacity for structure (optional)

### Line Vocabulary

| Technique | Meaning | SVG Example |
|-----------|---------|-------------|
| Straight lines | Structure, stability, code, data | `<line x1="0" y1="100" x2="200" y2="100"/>` |
| Quadratic curves | Flow, connection, movement | `<path d="M 0 100 Q 100 50, 200 100"/>` |
| Dashed lines | Wireless, async, tentative | `stroke-dasharray="8 4"` |
| Rounded rectangles | Containers, devices, boundaries | `<rect rx="12"/>` |
| Small filled circles | Nodes, connection points | `<circle r="4" fill="#e5e5e5"/>` |

---

## Abstract Representation Guide

When visualizing concepts, use these patterns:

| Concept | Abstract Form |
|---------|---------------|
| **Device (phone/laptop)** | Rounded rectangle, minimal internal lines |
| **Code/Terminal** | Bracket pairs `< >` or `[ ]` with horizontal lines between |
| **Data/Information** | Horizontal lines of varying length, stacked |
| **Connection** | Curved or straight paths between elements |
| **Server/Cloud** | Rectangle with subtle horizontal lines inside |
| **Flow/Process** | Arrow-like paths, sequential dots |
| **AI/Intelligence** | Interconnected nodes, branching paths, feedback loops |
| **Time/Async** | Dashed lines, multiple parallel paths |
| **Security/Auth** | Abstract lock shape (rectangle + circle), boundary lines |
| **Database** | Stacked horizontal lines, vertical connectors |
| **API** | Bracket groups with bidirectional paths between |

---

## SVG Template

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 630" fill="none" stroke="#e5e5e5" stroke-width="1.5">
  <rect width="1200" height="630" fill="#111"/>

  <!-- Primary elements here -->

  <!-- Connection lines -->

  <!-- Secondary/decorative elements -->

  <!-- Optional: subtle grid lines at 0.1 opacity -->
</svg>
```

---

## Generation Process

### 1. Analyze the Topic

Read the blog post and identify:
- Core concept (what is this about?)
- Key elements (what 2-4 things are involved?)
- Relationship/flow (how do they connect?)

### 2. Map to Visual Elements

Using the Abstract Representation Guide, translate:
- Topic → 2-4 abstract shapes
- Relationships → connection lines
- Process → left-to-right flow

### 3. Compose

- Place primary element(s) at center-left
- Add secondary elements right of center
- Connect with appropriate line styles
- Add nodes at connection points
- Optional: subtle grid lines for structure

### 4. Validate

Run through checklist:
- [ ] Background exactly #111111
- [ ] Strokes #e5e5e5 only
- [ ] No fills except background and node dots
- [ ] Clear negative space (not cluttered)
- [ ] Works at small sizes (mobile preview)
- [ ] Relates to topic abstractly, not literally
- [ ] Feels intentional, not decorative

---

## Example Abstractions

### Mobile Dev Workflow
**Elements:** phone, connection, terminal, server
```
[phone outline] ---(dashed curves)---> [< code lines >] ---> [server box]
```

### AI Agents
**Elements:** central node, connections, sub-nodes, feedback
```
                    [node]
                   /  |  \
            [node]  [node]  [node]
                   \  |  /
                   [center]
```

### Database Design
**Elements:** tables (stacked lines), relationships (vertical connectors)
```
[====]     [====]
[====] --- [====]
[====]  |  [====]
        |
      [====]
      [====]
```

### Authentication Flow
**Elements:** boundary, lock abstraction, protected area
```
[user] ---> [|O|] ---> | protected area |
```

---

## File Conventions

### Naming
`{post-slug}-header.svg`

Example: `mobile-dev-workflow-header.svg`

### Location
`public/images/blog/`

### Usage in Posts
First line after frontmatter:
```markdown
![](/images/blog/{post-slug}-header.svg)
```

CSS automatically styles first-child images as full-bleed headers.

---

## Quality Standards

**Good headers:**
- Feel like a system diagram someone might sketch on a whiteboard
- Could belong to any post in the series (visual consistency)
- Add visual interest without demanding attention
- Work in both light and dark contexts (it's white-on-black)

**Bad headers:**
- Literal illustrations (actual phone drawings, etc.)
- Decorative flourishes or ornaments
- Cluttered compositions
- Generic geometric patterns with no topic connection
- Anything that could be clip art

---

## Do Not Include

- Text or numbers
- Literal illustrations of objects
- Gradients, shadows, or effects
- Colors other than #111111 and #e5e5e5
- Fills (except background and node dots)
- Decorative elements that don't serve the concept
- Logos or icons
