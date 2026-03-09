# Unit 5: Advanced Topics on CSS

**Course:** Internet Technology (CMP 173)
**Program:** BCSIT, Pokhara University
**Duration:** 7 Hours

---

## Table of Contents

- [5.1 CSS Flexbox](#51-css-flexbox)
- [5.2 CSS Grid](#52-css-grid)
- [5.3 CSS Transitions and Animations](#53-css-transitions-and-animations)
- [5.4 Responsive Web Design](#54-responsive-web-design)
- [5.5 CSS Specificity and Inheritance](#55-css-specificity-and-inheritance)
- [5.6 CSS Units and Values](#56-css-units-and-values)
- [5.7 CSS Preprocessors](#57-css-preprocessors)
- [5.8 CSS Best Practices and Optimization](#58-css-best-practices-and-optimization)
- [Practice Exercises](#practice-exercises)
- [References](#references)

---

## Learning Objectives

After completing this unit, students will be able to:

- Develop advanced proficiency in CSS, covering flexbox, grid layouts, transitions, animations, responsiveness, specificity, units, preprocessors, and optimization
- Master CSS Flexbox and Grid for versatile layout control
- Apply transitions and animations using various properties and keyframes
- Create responsive designs using media queries, breakpoints, and the mobile-first approach
- Understand CSS specificity and inheritance principles for effective styling
- Utilize different CSS units and values, including relative and absolute units
- Explore CSS preprocessors, employing nesting, variables, mixins, and functions
- Implement CSS best practices, including efficient organization, vendor prefixes, and optimization techniques
- Enhance web development skills with advanced CSS techniques

---

## 5.1 CSS Flexbox

### Introduction to Flexbox

Flexbox (Flexible Box Layout) is a one-dimensional layout method for arranging items in rows or columns. It provides an efficient way to distribute space and align items in a container.

#### Key Concepts

- **Flex Container:** The parent element with `display: flex`
- **Flex Items:** Direct children of the flex container
- **Main Axis:** Primary axis along which flex items are laid out
- **Cross Axis:** Perpendicular to the main axis

#### Basic Syntax

```css
.container {
    display: flex;
}
```

---

### Flex Container Properties

#### 1. display

```css
.container {
    display: flex;       /* Block-level flex container */
    display: inline-flex; /* Inline-level flex container */
}
```

#### 2. flex-direction

Defines the main axis direction.

```css
.container {
    flex-direction: row;            /* Default: left to right */
    flex-direction: row-reverse;    /* Right to left */
    flex-direction: column;         /* Top to bottom */
    flex-direction: column-reverse; /* Bottom to top */
}
```

**Visual representation:**
```
┌─────────────────────────────────┐
│ row:      [1] [2] [3]           │
│ row-reverse: [3] [2] [1]        │
│ column:   [1]                   │
│           [2]                   │
│           [3]                   │
└─────────────────────────────────┘
```

#### 3. flex-wrap

Controls whether items wrap to new lines.

```css
.container {
    flex-wrap: nowrap;       /* Default: single line */
    flex-wrap: wrap;         /* Wrap to multiple lines */
    flex-wrap: wrap-reverse; /* Wrap in reverse direction */
}
```

#### 4. flex-flow (Shorthand)

Combines `flex-direction` and `flex-wrap`.

```css
.container {
    flex-flow: row wrap;
    flex-flow: column nowrap;
}
```

#### 5. justify-content

Aligns items along the MAIN axis.

```css
.container {
    justify-content: flex-start;    /* Default: items at start */
    justify-content: flex-end;      /* Items at end */
    justify-content: center;        /* Items at center */
    justify-content: space-between; /* Equal space between items */
    justify-content: space-around;  /* Equal space around items */
    justify-content: space-evenly;  /* Equal space everywhere */
}
```

**Visual representation (row direction):**
```
┌─────────────────────────────────────┐
│ flex-start:    [1][2][3]            │
│ flex-end:               [1][2][3]   │
│ center:           [1][2][3]         │
│ space-between: [1]    [2]    [3]    │
│ space-around:   [1]  [2]  [3]       │
│ space-evenly:   [1]   [2]   [3]     │
└─────────────────────────────────────┘
```

#### 6. align-items

Aligns items along the CROSS axis.

```css
.container {
    align-items: stretch;     /* Default: stretch to fill */
    align-items: flex-start;  /* Items at cross-start */
    align-items: flex-end;    /* Items at cross-end */
    align-items: center;      /* Items at center */
    align-items: baseline;    /* Align by text baseline */
}
```

#### 7. align-content

Aligns multiple lines of items (only works with `flex-wrap: wrap`).

```css
.container {
    align-content: flex-start;
    align-content: flex-end;
    align-content: center;
    align-content: space-between;
    align-content: space-around;
    align-content: stretch;      /* Default */
}
```

#### 8. gap, row-gap, column-gap

Sets spacing between flex items.

```css
.container {
    gap: 20px;              /* Both row and column gap */
    gap: 10px 20px;         /* row-gap column-gap */
    row-gap: 10px;          /* Gap between rows */
    column-gap: 20px;       /* Gap between columns */
}
```

---

### Flex Item Properties

#### 1. order

Controls the order of items (default: 0).

```css
.item {
    order: 0;   /* Default */
    order: 1;   /* Appears later */
    order: -1;  /* Appears earlier */
}
```

**Example:**
- HTML: [A] [B] [C]
- With order: A(2), B(1), C(3)
- Display: [B] [A] [C]

#### 2. flex-grow

Defines ability to grow if space is available (default: 0).

```css
.item {
    flex-grow: 0;  /* Default: don't grow */
    flex-grow: 1;  /* Grow equally */
    flex-grow: 2;  /* Grow twice as much */
}
```

#### 3. flex-shrink

Defines ability to shrink if necessary (default: 1).

```css
.item {
    flex-shrink: 1;  /* Default: can shrink */
    flex-shrink: 0;  /* Don't shrink */
    flex-shrink: 2;  /* Shrink twice as much */
}
```

#### 4. flex-basis

Initial size before growing/shrinking.

```css
.item {
    flex-basis: auto;   /* Default: use width/height */
    flex-basis: 200px;  /* Fixed starting size */
    flex-basis: 50%;    /* Percentage of container */
    flex-basis: 0;      /* Ignore content size */
}
```

#### 5. flex (Shorthand)

Combines `flex-grow`, `flex-shrink`, and `flex-basis`.

```css
.item {
    flex: 0 1 auto;     /* Default */
    flex: 1;            /* flex: 1 1 0 (grow equally) */
    flex: auto;         /* flex: 1 1 auto */
    flex: none;         /* flex: 0 0 auto (rigid) */
    flex: 2 1 200px;    /* grow shrink basis */
}
```

#### 6. align-self

Overrides `align-items` for individual items.

```css
.item {
    align-self: auto;       /* Default: inherit from container */
    align-self: flex-start;
    align-self: flex-end;
    align-self: center;
    align-self: baseline;
    align-self: stretch;
}
```

---

### Flexbox Practical Examples

#### Example 1: Navigation Bar

```html
<nav class="navbar">
    <div class="logo">Logo</div>
    <ul class="nav-links">
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Contact</a></li>
    </ul>
</nav>
```

```css
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background: #333;
}

.nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
}
```

#### Example 2: Card Layout

```html
<div class="card-container">
    <div class="card">Card 1</div>
    <div class="card">Card 2</div>
    <div class="card">Card 3</div>
</div>
```

```css
.card-container {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
}

.card {
    flex: 1 1 300px;  /* Grow, shrink, min-width 300px */
    max-width: 400px;
    padding: 20px;
    background: #f0f0f0;
}
```

#### Example 3: Centering Content

```css
.center-container {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}
```

#### Example 4: Holy Grail Layout

```html
<div class="holy-grail">
    <header>Header</header>
    <div class="main-content">
        <nav>Sidebar</nav>
        <main>Main Content</main>
        <aside>Aside</aside>
    </div>
    <footer>Footer</footer>
</div>
```

```css
.holy-grail {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}

.main-content {
    display: flex;
    flex: 1;
}

nav, aside {
    flex: 0 0 200px;
}

main {
    flex: 1;
}
```

---

## 5.2 CSS Grid

### Introduction to CSS Grid

CSS Grid is a two-dimensional layout system that handles both columns and rows simultaneously. It's ideal for complex layouts.

#### Key Concepts

- **Grid Container:** Element with `display: grid`
- **Grid Items:** Direct children of the grid container
- **Grid Lines:** Dividing lines that make up the grid structure
- **Grid Tracks:** Rows and columns
- **Grid Cells:** Single unit of the grid
- **Grid Areas:** Rectangular area spanning multiple cells

#### Basic Syntax

```css
.container {
    display: grid;
    grid-template-columns: 200px 200px 200px;
    grid-template-rows: 100px 100px;
}
```

---

### Grid Container Properties

#### 1. display

```css
.container {
    display: grid;        /* Block-level grid */
    display: inline-grid; /* Inline-level grid */
}
```

#### 2. grid-template-columns / grid-template-rows

Define the size of grid tracks.

```css
.container {
    /* Fixed sizes */
    grid-template-columns: 200px 200px 200px;
    grid-template-rows: 100px 100px;

    /* Mixed units */
    grid-template-columns: 200px 1fr 2fr;

    /* Repeat notation */
    grid-template-columns: repeat(3, 1fr);
    grid-template-columns: repeat(3, 200px);

    /* Auto-fill and auto-fit */
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));

    /* Min/max */
    grid-template-columns: minmax(100px, 200px) 1fr;

    /* Named lines */
    grid-template-columns: [start] 1fr [center] 1fr [end];
}
```

**The fr Unit:**
- `fr` = fraction of available space
- `1fr 2fr 1fr` = 25% 50% 25%

**auto-fill vs auto-fit:**
- `auto-fill`: Creates empty columns if space available
- `auto-fit`: Collapses empty columns, items stretch

#### 3. grid-template-areas

Define named grid areas.

```css
.container {
    grid-template-areas:
        "header header header"
        "sidebar main main"
        "footer footer footer";
}

.header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main    { grid-area: main; }
.footer  { grid-area: footer; }
```

Use `.` (dot) for empty cells:
```css
grid-template-areas:
    "header header header"
    "sidebar main ."
    "footer footer footer";
```

#### 4. grid-template (Shorthand)

Combines rows, columns, and areas.

```css
.container {
    grid-template:
        "header header header" 80px
        "sidebar main main" 1fr
        "footer footer footer" 60px
        / 200px 1fr 1fr;
}
```

#### 5. gap, row-gap, column-gap

Sets spacing between grid items.

```css
.container {
    gap: 20px;              /* Both row and column */
    gap: 10px 20px;         /* row-gap column-gap */
    row-gap: 10px;
    column-gap: 20px;

    /* Old syntax (still works) */
    grid-gap: 20px;
    grid-row-gap: 10px;
    grid-column-gap: 20px;
}
```

#### 6. justify-items

Aligns items horizontally within their cells.

```css
.container {
    justify-items: stretch;  /* Default */
    justify-items: start;
    justify-items: end;
    justify-items: center;
}
```

#### 7. align-items

Aligns items vertically within their cells.

```css
.container {
    align-items: stretch;   /* Default */
    align-items: start;
    align-items: end;
    align-items: center;
}
```

#### 8. place-items (Shorthand)

Combines `align-items` and `justify-items`.

```css
.container {
    place-items: center;          /* Both */
    place-items: center start;    /* align-items justify-items */
}
```

#### 9. justify-content

Aligns the entire grid horizontally within the container.

```css
.container {
    justify-content: start;
    justify-content: end;
    justify-content: center;
    justify-content: stretch;
    justify-content: space-between;
    justify-content: space-around;
    justify-content: space-evenly;
}
```

#### 10. align-content

Aligns the entire grid vertically within the container.

```css
.container {
    align-content: start;
    align-content: end;
    align-content: center;
    align-content: stretch;
    align-content: space-between;
    align-content: space-around;
    align-content: space-evenly;
}
```

#### 11. place-content (Shorthand)

Combines `align-content` and `justify-content`.

```css
.container {
    place-content: center;
    place-content: center start;
}
```

#### 12. grid-auto-columns / grid-auto-rows

Size of implicitly created tracks.

```css
.container {
    grid-auto-columns: 100px;
    grid-auto-rows: minmax(100px, auto);
}
```

#### 13. grid-auto-flow

How auto-placed items are inserted.

```css
.container {
    grid-auto-flow: row;         /* Default */
    grid-auto-flow: column;
    grid-auto-flow: dense;       /* Fill gaps */
    grid-auto-flow: row dense;
}
```

---

### Grid Item Properties

#### 1. grid-column-start / grid-column-end

```css
.item {
    grid-column-start: 1;
    grid-column-end: 3;

    /* Span notation */
    grid-column-start: span 2;  /* Span 2 columns */
}
```

#### 2. grid-row-start / grid-row-end

```css
.item {
    grid-row-start: 1;
    grid-row-end: 3;

    /* Span notation */
    grid-row-end: span 2;  /* Span 2 rows */
}
```

#### 3. grid-column / grid-row (Shorthand)

```css
.item {
    grid-column: 1 / 3;      /* start / end */
    grid-column: 1 / span 2; /* start / span */
    grid-column: span 2;     /* Just span */

    grid-row: 1 / 3;
    grid-row: 2 / -1;        /* -1 = last line */
}
```

#### 4. grid-area

Shorthand for row/column positions or reference to named area.

```css
.item {
    /* Named area */
    grid-area: header;

    /* row-start / column-start / row-end / column-end */
    grid-area: 1 / 1 / 3 / 4;
}
```

#### 5. justify-self

Aligns item horizontally within its cell.

```css
.item {
    justify-self: stretch;  /* Default */
    justify-self: start;
    justify-self: end;
    justify-self: center;
}
```

#### 6. align-self

Aligns item vertically within its cell.

```css
.item {
    align-self: stretch;   /* Default */
    align-self: start;
    align-self: end;
    align-self: center;
}
```

#### 7. place-self (Shorthand)

```css
.item {
    place-self: center;
    place-self: center start;
}
```

---

### Grid Practical Examples

#### Example 1: Basic 12-Column Grid

```css
.grid-12 {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    gap: 20px;
}

.col-6 { grid-column: span 6; }
.col-4 { grid-column: span 4; }
.col-3 { grid-column: span 3; }
```

#### Example 2: Responsive Card Layout

```css
.card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
}
```

#### Example 3: Dashboard Layout

```html
<div class="dashboard">
    <header class="header">Header</header>
    <nav class="sidebar">Sidebar</nav>
    <main class="main">Main Content</main>
    <aside class="widgets">Widgets</aside>
    <footer class="footer">Footer</footer>
</div>
```

```css
.dashboard {
    display: grid;
    grid-template-columns: 250px 1fr 300px;
    grid-template-rows: 80px 1fr 60px;
    grid-template-areas:
        "header header header"
        "sidebar main widgets"
        "footer footer footer";
    min-height: 100vh;
    gap: 10px;
}

.header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main    { grid-area: main; }
.widgets { grid-area: widgets; }
.footer  { grid-area: footer; }
```

#### Example 4: Image Gallery with Different Sizes

```css
.gallery {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: 200px;
    gap: 10px;
}

.gallery-item.large {
    grid-column: span 2;
    grid-row: span 2;
}

.gallery-item.wide {
    grid-column: span 2;
}

.gallery-item.tall {
    grid-row: span 2;
}
```

---

### Flexbox vs Grid

| Aspect | Flexbox | Grid |
|--------|---------|------|
| **Dimension** | One-dimensional | Two-dimensional |
| **Direction** | Row OR column | Row AND column |
| **Use Case** | Components, UI parts | Page layouts |
| **Content-first** | Yes (items dictate) | No (layout dictates) |
| **Alignment** | On single axis | On both axes |
| **Overlap** | Difficult | Easy with grid-area |

**When to Use What:**
- **Flexbox:** Navigation, card layouts, centering, toolbars
- **Grid:** Page layouts, complex grids, image galleries

---

## 5.3 CSS Transitions and Animations

### CSS Transitions

Transitions provide smooth changes between property values over a duration.

#### Transition Properties

**1. transition-property**

Specifies which CSS properties to transition.

```css
.element {
    transition-property: background-color;
    transition-property: all;
    transition-property: width, height, background-color;
    transition-property: none;
}
```

**2. transition-duration**

How long the transition takes.

```css
.element {
    transition-duration: 0.3s;
    transition-duration: 300ms;
    transition-duration: 1s, 0.5s; /* Different durations */
}
```

**3. transition-timing-function**

The speed curve of the transition.

```css
.element {
    transition-timing-function: ease;        /* Default */
    transition-timing-function: linear;      /* Constant speed */
    transition-timing-function: ease-in;     /* Slow start */
    transition-timing-function: ease-out;    /* Slow end */
    transition-timing-function: ease-in-out; /* Slow start and end */
    transition-timing-function: cubic-bezier(0.68, -0.55, 0.27, 1.55);
    transition-timing-function: steps(5, start);
}
```

**Common cubic-bezier values:**
- `ease`: cubic-bezier(0.25, 0.1, 0.25, 1)
- `ease-in`: cubic-bezier(0.42, 0, 1, 1)
- `ease-out`: cubic-bezier(0, 0, 0.58, 1)
- `ease-in-out`: cubic-bezier(0.42, 0, 0.58, 1)

**4. transition-delay**

Delay before transition starts.

```css
.element {
    transition-delay: 0s;      /* Default */
    transition-delay: 0.5s;
    transition-delay: 200ms;
}
```

**5. transition (Shorthand)**

```css
.element {
    /* property duration timing-function delay */
    transition: background-color 0.3s ease 0s;
    transition: all 0.5s ease-in-out;
    transition: width 0.3s, height 0.5s;
}
```

---

### Transition Examples

#### Example 1: Button Hover Effect

```css
.button {
    background-color: #3498db;
    color: white;
    padding: 10px 20px;
    border: none;
    transition: background-color 0.3s ease, transform 0.2s ease;
}

.button:hover {
    background-color: #2980b9;
    transform: scale(1.05);
}
```

#### Example 2: Card Hover

```css
.card {
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    transition: box-shadow 0.3s ease, transform 0.3s ease;
}

.card:hover {
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
    transform: translateY(-5px);
}
```

#### Example 3: Menu Slide

```css
.sidebar {
    width: 250px;
    transform: translateX(-100%);
    transition: transform 0.3s ease-out;
}

.sidebar.open {
    transform: translateX(0);
}
```

---

### CSS Animations

Animations allow more complex, multi-step transitions using keyframes.

#### @keyframes Rule

Define animation stages.

```css
@keyframes slidein {
    from {
        transform: translateX(-100%);
        opacity: 0;
    }
    to {
        transform: translateX(0);
        opacity: 1;
    }
}

/* Using percentages for multiple stages */
@keyframes bounce {
    0% {
        transform: translateY(0);
    }
    25% {
        transform: translateY(-30px);
    }
    50% {
        transform: translateY(0);
    }
    75% {
        transform: translateY(-15px);
    }
    100% {
        transform: translateY(0);
    }
}
```

---

#### Animation Properties

**1. animation-name**

```css
.element {
    animation-name: slidein;
    animation-name: bounce, fadeIn; /* Multiple animations */
}
```

**2. animation-duration**

```css
.element {
    animation-duration: 1s;
    animation-duration: 500ms;
}
```

**3. animation-timing-function**

```css
.element {
    animation-timing-function: ease;
    animation-timing-function: linear;
    animation-timing-function: ease-in-out;
    animation-timing-function: cubic-bezier(0.68, -0.55, 0.27, 1.55);
}
```

**4. animation-delay**

```css
.element {
    animation-delay: 0s;
    animation-delay: 2s;
    animation-delay: -0.5s; /* Start midway */
}
```

**5. animation-iteration-count**

```css
.element {
    animation-iteration-count: 1;        /* Default */
    animation-iteration-count: 3;        /* Run 3 times */
    animation-iteration-count: infinite; /* Loop forever */
}
```

**6. animation-direction**

```css
.element {
    animation-direction: normal;           /* Default: forward */
    animation-direction: reverse;          /* Backward */
    animation-direction: alternate;        /* Forward, then backward */
    animation-direction: alternate-reverse;/* Backward, then forward */
}
```

**7. animation-fill-mode**

Styles applied before/after animation.

```css
.element {
    animation-fill-mode: none;      /* Default */
    animation-fill-mode: forwards;  /* Keep end state */
    animation-fill-mode: backwards; /* Apply start state during delay */
    animation-fill-mode: both;      /* Both forwards and backwards */
}
```

**8. animation-play-state**

```css
.element {
    animation-play-state: running; /* Default */
    animation-play-state: paused;
}

/* Pause on hover */
.element:hover {
    animation-play-state: paused;
}
```

**9. animation (Shorthand)**

```css
.element {
    /* name duration timing-function delay iteration-count direction
       fill-mode play-state */
    animation: slidein 1s ease-out 0.5s infinite alternate forwards;

    /* Multiple animations */
    animation: bounce 1s infinite, fadeIn 0.5s forwards;
}
```

---

### Animation Examples

#### Example 1: Pulse Effect

```css
@keyframes pulse {
    0% {
        transform: scale(1);
    }
    50% {
        transform: scale(1.1);
    }
    100% {
        transform: scale(1);
    }
}

.pulse-button {
    animation: pulse 2s infinite;
}
```

#### Example 2: Loading Spinner

```css
@keyframes spin {
    from {
        transform: rotate(0deg);
    }
    to {
        transform: rotate(360deg);
    }
}

.spinner {
    width: 40px;
    height: 40px;
    border: 4px solid #f3f3f3;
    border-top: 4px solid #3498db;
    border-radius: 50%;
    animation: spin 1s linear infinite;
}
```

#### Example 3: Typewriter Effect

```css
@keyframes typing {
    from {
        width: 0;
    }
    to {
        width: 100%;
    }
}

@keyframes blink {
    50% {
        border-color: transparent;
    }
}

.typewriter {
    overflow: hidden;
    white-space: nowrap;
    border-right: 3px solid #333;
    animation: typing 3s steps(30) forwards,
               blink 0.7s infinite;
}
```

#### Example 4: Fade In Up

```css
@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.fade-in-up {
    animation: fadeInUp 0.6s ease-out forwards;
}

/* Staggered animation */
.item:nth-child(1) { animation-delay: 0.1s; }
.item:nth-child(2) { animation-delay: 0.2s; }
.item:nth-child(3) { animation-delay: 0.3s; }
```

#### Example 5: Shake Effect

```css
@keyframes shake {
    0%, 100% { transform: translateX(0); }
    10%, 30%, 50%, 70%, 90% { transform: translateX(-10px); }
    20%, 40%, 60%, 80% { transform: translateX(10px); }
}

.error-input {
    animation: shake 0.5s ease-in-out;
}
```

---

### Transform Property

Used with transitions and animations for visual changes.

```css
.element {
    /* Translate (move) */
    transform: translateX(100px);
    transform: translateY(50px);
    transform: translate(100px, 50px);

    /* Scale (resize) */
    transform: scaleX(1.5);
    transform: scaleY(2);
    transform: scale(1.5, 2);
    transform: scale(1.5);  /* Uniform */

    /* Rotate */
    transform: rotate(45deg);
    transform: rotateX(45deg);  /* 3D */
    transform: rotateY(45deg);  /* 3D */

    /* Skew */
    transform: skewX(10deg);
    transform: skewY(10deg);
    transform: skew(10deg, 5deg);

    /* Multiple transforms */
    transform: translateX(100px) rotate(45deg) scale(1.2);

    /* Transform origin */
    transform-origin: center;  /* Default */
    transform-origin: top left;
    transform-origin: 50% 50%;
}
```

---

## 5.4 Responsive Web Design

### Introduction to Responsive Design

Responsive Web Design (RWD) makes web pages render well on different devices and screen sizes using flexible layouts, images, and CSS media queries.

#### Key Principles

1. **Fluid Grids** - Use relative units (%, em, rem)
2. **Flexible Images** - Scale within containers
3. **Media Queries** - Apply styles based on device characteristics

---

### Viewport Meta Tag

Essential for responsive design on mobile devices.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**Viewport Properties:**
```html
width=device-width   <!-- Match device width -->
initial-scale=1.0    <!-- Initial zoom level -->
maximum-scale=1.0    <!-- Prevent zooming -->
user-scalable=no     <!-- Disable user zoom -->
```

---

### Media Queries

Apply styles based on device characteristics.

#### Basic Syntax

```css
@media media-type and (condition) {
    /* CSS rules */
}
```

#### Media Types

```css
all      /* All devices (default) */
screen   /* Screens (computers, tablets, phones) */
print    /* Print preview/printed pages */
speech   /* Screen readers */
```

#### Common Conditions

```css
/* Width-based */
@media (min-width: 768px) { }
@media (max-width: 767px) { }
@media (min-width: 768px) and (max-width: 1024px) { }

/* Height-based */
@media (min-height: 600px) { }

/* Orientation */
@media (orientation: portrait) { }
@media (orientation: landscape) { }

/* Resolution/DPI */
@media (min-resolution: 2dppx) { }  /* Retina displays */
@media (-webkit-min-device-pixel-ratio: 2) { }

/* Hover capability */
@media (hover: hover) { }  /* Device can hover */
@media (hover: none) { }   /* Touch devices */

/* Pointer precision */
@media (pointer: fine) { }   /* Mouse */
@media (pointer: coarse) { } /* Touch */

/* Prefers reduced motion */
@media (prefers-reduced-motion: reduce) {
    * { animation: none !important; }
}

/* Dark mode preference */
@media (prefers-color-scheme: dark) {
    body { background: #333; color: #fff; }
}
```

---

### Common Breakpoints

```css
/* Mobile First Approach (Recommended) */
/* Base styles for mobile */

/* Small devices (landscape phones, 576px and up) */
@media (min-width: 576px) { }

/* Medium devices (tablets, 768px and up) */
@media (min-width: 768px) { }

/* Large devices (desktops, 992px and up) */
@media (min-width: 992px) { }

/* Extra large devices (large desktops, 1200px and up) */
@media (min-width: 1200px) { }

/* Extra extra large devices (1400px and up) */
@media (min-width: 1400px) { }
```

---

### Mobile-First Approach

Start with mobile styles, then add complexity for larger screens.

```css
/* Base styles (mobile) */
.container {
    width: 100%;
    padding: 15px;
}

.card {
    width: 100%;
    margin-bottom: 20px;
}

/* Tablet and up */
@media (min-width: 768px) {
    .container {
        width: 750px;
        margin: 0 auto;
    }

    .card {
        width: 48%;
        display: inline-block;
    }
}

/* Desktop and up */
@media (min-width: 992px) {
    .container {
        width: 970px;
    }

    .card {
        width: 31%;
    }
}
```

---

### Responsive Images

#### 1. Fluid Images

```css
img {
    max-width: 100%;
    height: auto;
}
```

#### 2. Background Images

```css
.hero {
    background-image: url('hero-small.jpg');
    background-size: cover;
    background-position: center;
}

@media (min-width: 768px) {
    .hero {
        background-image: url('hero-medium.jpg');
    }
}

@media (min-width: 1200px) {
    .hero {
        background-image: url('hero-large.jpg');
    }
}
```

#### 3. HTML srcset and sizes

```html
<img src="small.jpg"
     srcset="small.jpg 300w,
             medium.jpg 600w,
             large.jpg 1200w"
     sizes="(max-width: 600px) 300px,
            (max-width: 1200px) 600px,
            1200px"
     alt="Responsive image">
```

#### 4. Picture Element

```html
<picture>
    <source media="(min-width: 1200px)" srcset="large.jpg">
    <source media="(min-width: 768px)" srcset="medium.jpg">
    <img src="small.jpg" alt="Responsive image">
</picture>
```

---

### Responsive Typography

#### 1. Fluid Typography with clamp()

```css
body {
    /* min, preferred, max */
    font-size: clamp(16px, 2vw, 24px);
}

h1 {
    font-size: clamp(24px, 5vw, 72px);
}
```

#### 2. Using rem with root size

```css
html {
    font-size: 16px;
}

@media (min-width: 768px) {
    html {
        font-size: 18px;
    }
}

body {
    font-size: 1rem;  /* Scales with html */
}
```

---

### Responsive Layout Example

```css
/* Reset */
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

/* Base (Mobile) */
.header {
    padding: 1rem;
    background: #333;
    color: white;
}

.nav {
    display: none;
}

.nav.active {
    display: flex;
    flex-direction: column;
}

.menu-toggle {
    display: block;
}

.main-content {
    padding: 1rem;
}

.sidebar {
    padding: 1rem;
    background: #f0f0f0;
}

/* Tablet */
@media (min-width: 768px) {
    .menu-toggle {
        display: none;
    }

    .nav {
        display: flex;
        flex-direction: row;
        gap: 1rem;
    }

    .content-wrapper {
        display: flex;
    }

    .main-content {
        flex: 2;
    }

    .sidebar {
        flex: 1;
    }
}

/* Desktop */
@media (min-width: 992px) {
    .container {
        max-width: 1200px;
        margin: 0 auto;
    }

    .main-content {
        flex: 3;
    }
}
```

---

## 5.5 CSS Specificity and Inheritance

### CSS Specificity

Specificity determines which CSS rule is applied when multiple rules target the same element. It's calculated as a score.

#### Specificity Hierarchy (Lowest to Highest)

1. Universal selector (*), combinators, :where()
2. Element selectors, pseudo-elements (::before)
3. Class selectors, attribute selectors, pseudo-classes (:hover)
4. ID selectors
5. Inline styles
6. !important

#### Specificity Calculation

Represented as: (Inline, IDs, Classes, Elements) or simply: (a, b, c, d)

**Examples:**

| Selector | Specificity | Score |
|----------|-------------|-------|
| * | (0,0,0,0) | 0 |
| p | (0,0,0,1) | 1 |
| div p | (0,0,0,2) | 2 |
| .class | (0,0,1,0) | 10 |
| p.class | (0,0,1,1) | 11 |
| #id | (0,1,0,0) | 100 |
| #id .class | (0,1,1,0) | 110 |
| #id .class p | (0,1,1,1) | 111 |
| style="..." | (1,0,0,0) | 1000 |
| !important | Overrides all |

---

### Specificity Examples

```css
/* Specificity: 0,0,0,1 */
p {
    color: blue;
}

/* Specificity: 0,0,1,0 - WINS */
.text {
    color: red;
}

/* Both target same element - .text wins */
/* <p class="text">This is red</p> */
```

**More Examples:**

```css
/* Specificity: 0,0,1,1 */
p.highlight { color: yellow; }

/* Specificity: 0,1,0,0 - WINS */
#special { color: green; }

/* Specificity: 0,1,1,0 - WINS over #special */
#special.active { color: purple; }
```

---

### The !important Rule

```css
p {
    color: red !important;  /* Wins over all normal rules */
}

/* Even ID selector loses to !important */
#myId {
    color: blue;  /* Loses */
}

/* Only another !important with higher specificity wins */
#myId {
    color: green !important;  /* Wins */
}
```

---

### Avoiding Specificity Wars

```css
/* Bad: High specificity, hard to override */
#header #nav ul li a.active { }

/* Good: Low, predictable specificity */
.nav-link { }
.nav-link--active { }

/* Use classes for styling, IDs for JavaScript */
```

---

### Specificity Tricks

**1. Increase specificity without ID:**

```css
/* Repeat class to increase specificity */
.button.button { }  /* 0,0,2,0 */
```

**2. :where() - Zero specificity:**

```css
/* Useful for default styles that are easy to override */
:where(.button) {
    background: blue;  /* 0,0,0,0 */
}
```

**3. :is() - Takes highest specificity of arguments:**

```css
:is(#id, .class, p) {
    /* Specificity of #id: 0,1,0,0 */
}
```

---

### CSS Inheritance

Some CSS properties are inherited from parent to child elements by default.

#### Inherited Properties (by default)

- color
- font-family, font-size, font-weight, font-style
- line-height
- letter-spacing
- text-align, text-indent, text-transform
- visibility
- cursor
- list-style

#### Non-Inherited Properties

- margin, padding
- border
- background
- width, height
- position
- display

---

### Controlling Inheritance

```css
.child {
    color: inherit;       /* Force inheritance */
    color: initial;       /* Use initial/default value */
    color: unset;         /* inherit if inheritable, else initial */
    color: revert;        /* Revert to browser default */
}

/* inherit all properties */
.child {
    all: inherit;
}

/* Reset all properties */
.child {
    all: initial;
    all: unset;
}
```

#### Example

```css
/* Parent styles */
.parent {
    color: blue;           /* Inherited */
    border: 1px solid red; /* Not inherited */
    font-size: 18px;       /* Inherited */
}

/* Child automatically gets color and font-size */
/* <div class="parent">
    <p>This text is blue and 18px</p>
</div> */

/* Force inheritance of non-inherited property */
.child {
    border: inherit;  /* Now has parent's border */
}
```

---

### Cascade

The cascade determines which styles apply when multiple rules target an element.

#### Cascade Order (Priority)

1. **Origin and Importance**
   - User agent !important
   - User !important
   - Author !important
   - Author normal
   - User normal
   - User agent normal

2. **Specificity** (higher wins)

3. **Source Order** (later wins if same specificity)

**Example:**

```css
/* Earlier in file */
p { color: blue; }

/* Later in file - WINS (same specificity) */
p { color: red; }
```

---

## 5.6 CSS Units and Values

### Absolute Units

Fixed units that don't change based on context.

```css
px   /* Pixels (1/96th of an inch) */
pt   /* Points (1/72nd of an inch) */
pc   /* Picas (1pc = 12pt) */
cm   /* Centimeters */
mm   /* Millimeters */
in   /* Inches */
```

```css
.element {
    width: 200px;
    font-size: 12pt;
    margin: 1cm;
}
```

> **Note:** `px` is the most common. `pt` is used mainly for print stylesheets.

---

### Relative Units

Scale relative to other values.

#### 1. em

Relative to the font-size of the element (or parent for font-size).

```css
.parent {
    font-size: 16px;
}

.child {
    font-size: 1.5em;    /* 24px (16 * 1.5) */
    padding: 2em;        /* 48px (24 * 2) - relative to own font-size */
}
```

**Compounding problem:**

```html
<div style="font-size: 1.2em">    <!-- 1.2x -->
    <div style="font-size: 1.2em"> <!-- 1.44x -->
        <div style="font-size: 1.2em"> <!-- 1.728x -->
        </div>
    </div>
</div>
```

#### 2. rem (Root em)

Relative to the root element's (html) font-size.

```css
html {
    font-size: 16px;  /* Base */
}

.element {
    font-size: 1.5rem;  /* 24px */
    padding: 2rem;      /* 32px */
    margin: 0.5rem;     /* 8px */
}

/* No compounding - always relative to root */
```

#### 3. % (Percentage)

Relative to parent element.

```css
.parent {
    width: 800px;
    font-size: 20px;
}

.child {
    width: 50%;       /* 400px */
    font-size: 80%;   /* 16px */
    padding: 5%;      /* Relative to parent WIDTH */
}
```

#### 4. Viewport Units

Relative to the viewport (browser window).

```css
vw   /* 1% of viewport width */
vh   /* 1% of viewport height */
vmin /* 1% of smaller dimension */
vmax /* 1% of larger dimension */
```

```css
.full-screen {
    width: 100vw;
    height: 100vh;
}

.hero {
    height: 50vh;  /* Half viewport height */
}

h1 {
    font-size: 5vw;  /* Responsive font */
}

/* Square that fits viewport */
.square {
    width: 50vmin;
    height: 50vmin;
}
```

#### 5. New Viewport Units (CSS4)

Account for dynamic browser UI (mobile address bar).

```css
svh, svw  /* Small viewport (UI visible) */
lvh, lvw  /* Large viewport (UI hidden) */
dvh, dvw  /* Dynamic viewport (changes with UI) */
```

```css
.hero {
    height: 100dvh;  /* Better for mobile */
}
```

#### 6. ch (Character)

Width of the "0" character in the current font.

```css
.readable-text {
    max-width: 70ch;  /* ~70 characters per line */
}

input {
    width: 20ch;  /* Fits ~20 characters */
}
```

#### 7. ex

Height of the lowercase "x" in the current font.

```css
.icon {
    height: 1ex;  /* Match text height */
}
```

---

### When to Use What

| Unit | Use Case |
|------|----------|
| px | Borders, shadows, fine details |
| rem | Font sizes, spacing (predictable) |
| em | Component-based sizing (relative to parent) |
| % | Widths, fluid layouts |
| vw/vh | Full-screen sections, viewport-based sizing |
| ch | Text containers, input widths |

---

### CSS Functions for Values

#### 1. calc()

Perform calculations.

```css
.sidebar {
    width: calc(100% - 300px);
}

.element {
    padding: calc(1rem + 5px);
    font-size: calc(16px + 0.5vw);
    width: calc(100vw / 3);
}
```

#### 2. min(), max(), clamp()

```css
.element {
    /* Use smaller of the two */
    width: min(100%, 800px);

    /* Use larger of the two */
    width: max(300px, 50%);

    /* Clamp between min and max */
    font-size: clamp(16px, 4vw, 32px);
    width: clamp(300px, 50%, 800px);
}
```

#### 3. var() - CSS Custom Properties

```css
:root {
    --primary-color: #3498db;
    --spacing: 1rem;
    --max-width: 1200px;
}

.element {
    color: var(--primary-color);
    padding: var(--spacing);
    max-width: var(--max-width);

    /* Fallback value */
    background: var(--undefined, #fff);
}

/* Change variables with media queries */
@media (min-width: 768px) {
    :root {
        --spacing: 2rem;
    }
}
```

---

### Color Values

```css
.element {
    /* Named colors */
    color: red;
    color: rebeccapurple;

    /* Hexadecimal */
    color: #ff0000;
    color: #f00;        /* Shorthand */
    color: #ff0000ff;   /* With alpha */

    /* RGB */
    color: rgb(255, 0, 0);
    color: rgba(255, 0, 0, 0.5);

    /* Modern syntax */
    color: rgb(255 0 0);
    color: rgb(255 0 0 / 50%);

    /* HSL (Hue, Saturation, Lightness) */
    color: hsl(0, 100%, 50%);
    color: hsla(0, 100%, 50%, 0.5);
    color: hsl(0 100% 50% / 50%);

    /* Special keywords */
    color: transparent;
    color: currentColor;  /* Inherits color property */
}
```

---

## 5.7 CSS Preprocessors

### Introduction to CSS Preprocessors

CSS preprocessors extend CSS with variables, nesting, mixins, functions, and more. The preprocessor code is compiled into standard CSS.

#### Popular Preprocessors

1. **Sass (SCSS)** - Most popular
2. **Less**
3. **Stylus**

---

### SASS/SCSS

Sass has two syntaxes:
- **SCSS (.scss)** - CSS-like syntax with braces
- **Sass (.sass)** - Indentation-based, no braces

#### 1. Variables

```scss
// SCSS
$primary-color: #3498db;
$font-stack: 'Helvetica', sans-serif;
$spacing: 16px;

.button {
    background-color: $primary-color;
    font-family: $font-stack;
    padding: $spacing;
}

// Compiled CSS
.button {
    background-color: #3498db;
    font-family: 'Helvetica', sans-serif;
    padding: 16px;
}
```

#### 2. Nesting

```scss
// SCSS
.navbar {
    background: #333;
    padding: 1rem;

    ul {
        list-style: none;
        display: flex;
    }

    li {
        margin: 0 1rem;
    }

    a {
        color: white;
        text-decoration: none;

        &:hover {
            color: #3498db;
        }
    }
}

// Compiled CSS
.navbar { background: #333; padding: 1rem; }
.navbar ul { list-style: none; display: flex; }
.navbar li { margin: 0 1rem; }
.navbar a { color: white; text-decoration: none; }
.navbar a:hover { color: #3498db; }
```

**The & (Parent Selector):**

```scss
.button {
    background: blue;

    &:hover { background: darkblue; }
    &:active { background: navy; }
    &--primary { background: green; }  // BEM: .button--primary
    &__icon { margin-right: 5px; }     // BEM: .button__icon
}
```

#### 3. Mixins

Reusable groups of CSS declarations.

```scss
// Define mixin
@mixin flex-center {
    display: flex;
    justify-content: center;
    align-items: center;
}

@mixin button-style($bg-color, $text-color: white) {
    background-color: $bg-color;
    color: $text-color;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;

    &:hover {
        background-color: darken($bg-color, 10%);
    }
}

// Use mixin
.container {
    @include flex-center;
    height: 100vh;
}

.btn-primary {
    @include button-style(#3498db);
}

.btn-danger {
    @include button-style(#e74c3c);
}
```

#### 4. Functions

```scss
// Built-in functions
.element {
    color: darken(#3498db, 20%);
    background: lighten(#333, 10%);
    border-color: mix(red, blue, 50%);
    opacity: percentage(0.5);  // 50%
}

// Custom functions
@function calculate-width($columns, $total: 12) {
    @return percentage($columns / $total);
}

.col-6 {
    width: calculate-width(6);  // 50%
}

.col-4 {
    width: calculate-width(4);  // 33.333%
}
```

#### 5. Partials and Import

Split code into multiple files.

```scss
// _variables.scss (underscore = partial, not compiled alone)
$primary-color: #3498db;
$secondary-color: #2ecc71;

// _mixins.scss
@mixin flex-center { /* ... */ }

// main.scss
@import 'variables';
@import 'mixins';

// Modern way: @use and @forward
@use 'variables' as vars;

.element {
    color: vars.$primary-color;
}
```

#### 6. Extend/Inheritance

```scss
// Base class
%button-base {
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

// Extend base
.btn-primary {
    @extend %button-base;
    background: blue;
    color: white;
}

.btn-secondary {
    @extend %button-base;
    background: gray;
    color: white;
}
```

#### 7. Control Directives

```scss
// @if
@mixin theme($dark: false) {
    @if $dark {
        background: #333;
        color: white;
    } @else {
        background: white;
        color: #333;
    }
}

// @for loop
@for $i from 1 through 12 {
    .col-#{$i} {
        width: percentage($i / 12);
    }
}

// @each loop
$colors: (primary: blue, secondary: green, danger: red);

@each $name, $color in $colors {
    .text-#{$name} {
        color: $color;
    }
}
```

---

### LESS

Similar to Sass but with JavaScript-like syntax.

```less
// Variables
@primary-color: #3498db;
@spacing: 16px;

// Nesting
.navbar {
    background: #333;

    a {
        color: white;

        &:hover {
            color: @primary-color;
        }
    }
}

// Mixins
.border-radius(@radius: 4px) {
    border-radius: @radius;
}

.button {
    .border-radius(8px);
}

// Functions
.element {
    color: darken(@primary-color, 10%);
}
```

---

### CSS Custom Properties (Native CSS Variables)

Modern CSS has native variables without preprocessors.

```css
:root {
    --primary-color: #3498db;
    --spacing: 1rem;
    --border-radius: 4px;
}

.button {
    background: var(--primary-color);
    padding: var(--spacing);
    border-radius: var(--border-radius);
}

/* Can change at runtime with JavaScript */
document.documentElement.style.setProperty('--primary-color', 'red');

/* Scope to elements */
.dark-theme {
    --primary-color: #2980b9;
    --text-color: white;
}
```

---

## 5.8 CSS Best Practices and Optimization

### Code Organization

#### 1. File Structure

```
styles/
├── base/
│   ├── _reset.scss
│   ├── _typography.scss
│   └── _variables.scss
├── components/
│   ├── _buttons.scss
│   ├── _cards.scss
│   └── _forms.scss
├── layout/
│   ├── _header.scss
│   ├── _footer.scss
│   └── _grid.scss
├── pages/
│   ├── _home.scss
│   └── _about.scss
├── utilities/
│   └── _helpers.scss
└── main.scss
```

#### 2. CSS Methodologies

**BEM (Block Element Modifier):**

```css
/* Block */
.card { }

/* Element (part of block) */
.card__title { }
.card__image { }
.card__content { }

/* Modifier (variation) */
.card--featured { }
.card__title--large { }
```

```html
<div class="card card--featured">
    <h2 class="card__title card__title--large">Title</h2>
    <img class="card__image" src="..." alt="...">
    <p class="card__content">Content</p>
</div>
```

**OOCSS (Object-Oriented CSS):**

```css
/* Separate structure from skin */
.box {
    padding: 20px;
    margin: 10px;
}

.box-primary {
    background: blue;
    color: white;
}

.box-secondary {
    background: gray;
    color: black;
}
```

**SMACSS (Scalable and Modular Architecture):**

```css
/* Base */
html, body { }

/* Layout */
.l-header { }
.l-sidebar { }

/* Module */
.card { }
.button { }

/* State */
.is-active { }
.is-hidden { }

/* Theme */
.theme-dark { }
```

---

### Naming Conventions

```css
/* Use meaningful names */
.navigation { }        /* Good */
.nav { }              /* Acceptable */
.n { }                /* Bad */

/* Use lowercase and hyphens */
.main-navigation { }   /* Good */
.mainNavigation { }    /* Avoid (camelCase) */
.main_navigation { }   /* Avoid (underscores) */

/* Be specific but not too specific */
.button-primary { }    /* Good */
.blue-button-with-rounded-corners { } /* Too specific */
```

---

### Performance Optimization

#### 1. Minimize CSS

```css
/* Before */
.element {
    margin-top: 10px;
    margin-right: 20px;
    margin-bottom: 10px;
    margin-left: 20px;
}

/* After (shorthand) */
.element {
    margin: 10px 20px;
}
```

#### 2. Reduce Specificity

```css
/* Bad: High specificity, hard to override */
#header .nav ul li a { }

/* Good: Low specificity */
.nav-link { }
```

#### 3. Avoid Expensive Selectors

```css
/* Expensive (browser reads right to left) */
div * { }
[class^="icon-"] { }

/* Better */
.icon { }
```

#### 4. Minimize Repaints and Reflows

```css
/* Bad: Triggers layout */
.animate {
    left: 100px;      /* Triggers layout */
    width: 200px;     /* Triggers layout */
}

/* Good: Only triggers composite */
.animate {
    transform: translateX(100px);
    opacity: 0.5;
}
```

#### 5. Use will-change Sparingly

```css
.animated-element {
    will-change: transform, opacity;
}

/* Remove when animation ends */
```

---

### Vendor Prefixes

For browser compatibility with newer features.

```css
.element {
    -webkit-transform: rotate(45deg);  /* Chrome, Safari */
    -moz-transform: rotate(45deg);     /* Firefox */
    -ms-transform: rotate(45deg);      /* IE */
    -o-transform: rotate(45deg);       /* Opera */
    transform: rotate(45deg);          /* Standard */
}

/* Use Autoprefixer tool instead of manual prefixes */
```

---

### CSS Reset vs Normalize

**CSS Reset (Eric Meyer's Reset):**

```css
/* Removes all default browser styles */
html, body, div, span, h1, h2, h3, p, a, img {
    margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font: inherit;
    vertical-align: baseline;
}
```

**Normalize.css:**
- Preserves useful defaults, fixes bugs
- More gentle, maintains consistency

**Modern Reset:**

```css
*, *::before, *::after {
    box-sizing: border-box;
}

* {
    margin: 0;
    padding: 0;
}

html {
    font-size: 62.5%;  /* 1rem = 10px */
}

body {
    font-size: 1.6rem; /* 16px */
    line-height: 1.5;
}

img, picture, video, canvas, svg {
    display: block;
    max-width: 100%;
}

input, button, textarea, select {
    font: inherit;
}
```

---

### Accessibility Best Practices

```css
/* Focus styles */
:focus {
    outline: 2px solid #3498db;
    outline-offset: 2px;
}

/* Don't remove outline completely */
:focus:not(:focus-visible) {
    outline: none;
}

/* Reduced motion */
@media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
    }
}

/* High contrast mode */
@media (prefers-contrast: high) {
    .button {
        border: 2px solid currentColor;
    }
}

/* Hidden but accessible */
.visually-hidden {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
}
```

---

### Debugging CSS

```css
/* Outline all elements */
* {
    outline: 1px solid red !important;
}

/* Visualize box model */
* {
    background: rgba(255, 0, 0, 0.1);
}

/* Debug specific element */
.debug {
    outline: 2px dashed blue;
    background: rgba(0, 0, 255, 0.1);
}
```

---

## Summary

### Key Topics Covered

| # | Topic | Description |
|---|-------|-------------|
| 1 | **CSS Flexbox** | Flex container properties, flex item properties, practical layouts |
| 2 | **CSS Grid** | Grid container, grid items, complex layouts |
| 3 | **CSS Transitions and Animations** | Transition properties, @keyframes, transform property |
| 4 | **Responsive Web Design** | Viewport meta tag, media queries, mobile-first approach |
| 5 | **CSS Specificity and Inheritance** | Specificity calculation, cascade order, inheritance control |
| 6 | **CSS Units and Values** | Absolute units, relative units, CSS functions |
| 7 | **CSS Preprocessors** | Sass/SCSS features, Less basics, native CSS custom properties |
| 8 | **CSS Best Practices** | Code organization, performance optimization, accessibility |

---

## Practice Exercises

### Exercise 1: Flexbox Navigation

Create a responsive navigation bar using Flexbox that collapses into a hamburger menu on mobile devices.

**Requirements:**
- Logo on the left
- Navigation links on the right
- Responsive design with mobile menu toggle

### Exercise 2: Grid Gallery

Create an image gallery using CSS Grid with different sized images (spanning multiple columns/rows).

**Requirements:**
- Responsive grid layout
- Featured images span 2x2
- Regular images 1x1
- Auto-fit on smaller screens

### Exercise 3: Animated Button

Create a button with hover animations including:
- Color change
- Scale effect
- Moving background gradient

### Exercise 4: Responsive Layout

Build a responsive webpage layout with:
- Header
- Sidebar
- Main content
- Footer

Use CSS Grid and media queries for different screen sizes.

### Exercise 5: CSS Variables Theme

Create a theme switcher (light/dark mode) using CSS custom properties that changes:
- Colors
- Backgrounds
- Shadows

### Exercise 6: Card Component

Build a reusable card component using BEM naming convention with multiple variants:
- `.card--featured`
- `.card--compact`
- `.card--horizontal`

### Exercise 7: Loading Animation

Create various loading animations using CSS keyframes:
- Spinner
- Dots
- Progress bar

---

## References

1. **Robbins, J. N.** (2018). *Learning Web Design: A Beginner's Guide to HTML, CSS, JavaScript, and Web Graphics*. O'Reilly Media.

2. **MDN Web Docs - CSS:**
   [https://developer.mozilla.org/en-US/docs/Web/CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)

3. **CSS-Tricks - A Complete Guide to Flexbox:**
   [https://css-tricks.com/snippets/css/a-guide-to-flexbox/](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

4. **CSS-Tricks - A Complete Guide to Grid:**
   [https://css-tricks.com/snippets/css/complete-guide-grid/](https://css-tricks.com/snippets/css/complete-guide-grid/)

5. **Sass Documentation:**
   [https://sass-lang.com/documentation](https://sass-lang.com/documentation)

6. **W3Schools CSS Tutorial:**
   [https://www.w3schools.com/css/](https://www.w3schools.com/css/)

7. **Can I Use (Browser Compatibility):**
   [https://caniuse.com/](https://caniuse.com/)

---

## Tips for Success

1. **Practice Regularly:** Build small projects incorporating these advanced concepts
2. **Browser DevTools:** Learn to use browser developer tools for debugging CSS
3. **Start Mobile-First:** Always design for mobile devices first, then scale up
4. **Use Flexbox and Grid Together:** They complement each other for complex layouts
5. **Optimize for Performance:** Minimize repaints and reflows, use efficient selectors
6. **Stay Updated:** CSS evolves constantly; keep learning new features
7. **Accessibility First:** Always consider users with disabilities in your designs

---

**End of Unit 5 Notes**

*Prepared for BCSIT First Year, Semester I*
*Internet Technology (CMP 173)*
*Pokhara University*