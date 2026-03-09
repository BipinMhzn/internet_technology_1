# Unit 4: Cascading Style Sheets (CSS)

## 4.1 Introduction to CSS

### What is CSS?

CSS (Cascading Style Sheets) is a stylesheet language used to describe the presentation of a document written in HTML. It controls the visual appearance of web pages including layout, colors, fonts, and spacing.

**The Three Pillars of Web Development:**
- **HTML**: Structure and content (the skeleton)
- **CSS**: Presentation and styling (the skin and clothes)
- **JavaScript**: Behavior and interactivity (the muscles)

### Why CSS?

1. **Separation of Concerns**: Separates content (HTML) from presentation (CSS)
2. **Consistency**: Apply same styles across multiple pages
3. **Maintainability**: Change appearance without modifying HTML
4. **Efficiency**: Single stylesheet can style entire website
5. **Flexibility**: Multiple style options for same content
6. **Accessibility**: Better control for different devices and users

### History of CSS

| Version | Year | Key Features |
|---------|------|-------------|
| CSS1 | 1996 | Basic styling capabilities |
| CSS2 | 1998 | Positioning, z-index, media types |
| CSS2.1 | 2011 | Fixed bugs and inconsistencies |
| CSS3 | 2011+ | Modular approach, flexbox, grid, animations |

CSS3 introduced a modular approach: Selectors, Box Model, Backgrounds and Borders, Text Effects, 2D/3D Transformations, Animations, Flexbox, Grid Layout, Media Queries.

---

## 4.2 CSS Syntax

### Basic CSS Syntax

CSS consists of rules that define how HTML elements should be displayed.

```
selector {
    property: value;
    property: value;
}
```

**Components:**
- **Selector**: Targets HTML element(s) to style
- **Declaration Block**: Contains one or more declarations in `{ }`
- **Declaration**: A property-value pair
- **Property**: The style attribute to change (color, font-size, etc.)
- **Value**: The setting for the property
- **Semicolon**: Separates declarations (required)

**Example:**

```css
h1 {
    color: blue;
    font-size: 24px;
    text-align: center;
}
```

**Multiple Selectors:**

```css
h1, h2, h3 {
    color: navy;
    font-family: Arial, sans-serif;
}
```

**Case Sensitivity:**
- Selectors: Case-sensitive for class/ID names (`.MyClass` and `.myclass` are different)
- Properties: Case-insensitive (lowercase recommended)
- Values: Depends on context (URLs are case-sensitive)

---

## 4.3 Using CSS with HTML

There are three ways to apply CSS to HTML documents:

### 1. Inline CSS

CSS written directly in the HTML element's `style` attribute.

```html
<h1 style="color: blue; font-size: 24px;">Hello World</h1>
<p style="color: red; margin: 10px;">This is a paragraph.</p>
```

**Characteristics:**
- Highest specificity (overrides other styles)
- Applies to single element only
- Mixes content with presentation
- Difficult to maintain
- Not recommended for large projects

### 2. Internal CSS (Embedded CSS)

CSS written inside `<style>` tags in the HTML document's `<head>` section.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Internal CSS Example</title>
    <style>
        body {
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }
        h1 {
            color: navy;
            text-align: center;
        }
        p {
            color: #333;
            line-height: 1.6;
        }
    </style>
</head>
<body>
    <h1>Welcome</h1>
    <p>This is styled with internal CSS.</p>
</body>
</html>
```

**Characteristics:**
- Styles apply to single page only
- No additional HTTP request
- Good for single-page styles
- Increases HTML file size

### 3. External CSS

CSS written in separate `.css` files and linked to HTML documents.

**HTML File (index.html):**

```html
<!DOCTYPE html>
<html>
<head>
    <title>External CSS Example</title>
    <link rel="stylesheet" href="styles.css">
    <!-- Multiple stylesheets -->
    <link rel="stylesheet" href="reset.css">
    <link rel="stylesheet" href="main.css">
</head>
<body>
    <h1>Welcome</h1>
    <p>This is styled with external CSS.</p>
</body>
</html>
```

**CSS File (styles.css):**

```css
body {
    background-color: #f0f0f0;
    font-family: Arial, sans-serif;
}

h1 {
    color: navy;
    text-align: center;
}
```

**The `<link>` Element:**

```html
<link rel="stylesheet"       /* Relationship: stylesheet */
      href="styles.css"      /* Path to CSS file */
      type="text/css"        /* Optional in HTML5 */
      media="screen">        /* Optional: media type */
```

**Alternative: @import:**

```css
@import url('reset.css');
@import url('typography.css');
```

> Note: `@import` is slower than `<link>` - not recommended.

**Characteristics:**
- Separation of concerns
- Reusable across multiple pages
- Browser caching (faster subsequent loads)
- Easier maintenance
- Best practice for production

### Comparison of CSS Methods

| Aspect | Inline | Internal | External |
|--------|--------|----------|----------|
| Location | HTML element | `<head>` | Separate file |
| Scope | Single element | Single page | Multiple pages |
| Reusability | None | Limited | High |
| Maintenance | Difficult | Medium | Easy |
| Caching | No | No | Yes |
| Specificity | Highest | Normal | Normal |
| Best For | Testing | Single page | Production |

**Priority Order (Cascade):**
1. Inline styles (highest priority)
2. Internal styles
3. External styles
4. Browser defaults (lowest priority)

> Note: `!important` and specificity can override this order.

---

## 4.4 CSS Selectors

Selectors are patterns used to select and style HTML elements.

### Basic Selectors

**1. Universal Selector (`*`)** - Selects all elements.

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

**2. Element/Type Selector** - Selects all elements of a given type.

```css
p { color: #333; line-height: 1.6; }
h1 { font-size: 32px; }
div { background-color: #f0f0f0; }
```

**3. Class Selector (`.`)** - Selects elements with a specific class.

```css
.highlight { background-color: yellow; }
.btn { padding: 10px 20px; border-radius: 5px; }

/* Multiple classes */
.btn.btn-primary {
    background-color: blue;
    color: white;
}
```

```html
<p class="highlight">Highlighted text</p>
<button class="btn btn-primary">Click Me</button>
```

**4. ID Selector (`#`)** - Selects element with a specific ID (unique per page).

```css
#header { background-color: #333; padding: 20px; }
#main-content { max-width: 1200px; margin: 0 auto; }
```

> Note: IDs should be unique; use classes for repeated styles.

**5. Attribute Selector** - Selects elements based on attributes.

```css
[disabled] { opacity: 0.5; }             /* Has attribute */
[type="text"] { border: 1px solid #ccc; } /* Exact value */
[href^="https"] { color: green; }         /* Starts with */
[href$=".pdf"] { color: red; }            /* Ends with */
[href*="example"] { font-weight: bold; }  /* Contains */
[lang|="en"] { font-family: Arial; }      /* Starts with or followed by hyphen */
```

### Combinator Selectors

**1. Descendant Selector (space)** - Selects all descendants.

```css
div p { color: blue; }
```

```html
<div>
    <p>Blue text</p>           <!-- Selected -->
    <section>
        <p>Also blue</p>       <!-- Selected -->
    </section>
</div>
```

**2. Child Selector (`>`)** - Selects only direct children.

```css
div > p { color: red; }
```

```html
<div>
    <p>Red text</p>            <!-- Selected -->
    <section>
        <p>Not red</p>         <!-- NOT selected -->
    </section>
</div>
```

**3. Adjacent Sibling Selector (`+`)** - Selects element immediately after another.

```css
h1 + p { font-size: 1.2em; }
```

```html
<h1>Title</h1>
<p>First paragraph</p>         <!-- Selected -->
<p>Second paragraph</p>        <!-- NOT selected -->
```

**4. General Sibling Selector (`~`)** - Selects all siblings after an element.

```css
h1 ~ p { color: gray; }
```

```html
<h1>Title</h1>
<p>First paragraph</p>         <!-- Selected -->
<p>Second paragraph</p>        <!-- Selected -->
<div>Not a paragraph</div>
<p>Third paragraph</p>         <!-- Selected -->
```

### Pseudo-Class Selectors

**1. Link States:**

```css
a:link { color: blue; }        /* Unvisited link */
a:visited { color: purple; }   /* Visited link */
a:hover { color: red; }        /* Mouse over */
a:active { color: orange; }    /* Being clicked */

/* Order matters: LoVe HAte (Link, Visited, Hover, Active) */
```

**2. Form States:**

```css
input:focus { border-color: blue; outline: none; }
input:disabled { background-color: #eee; }
input:enabled { background-color: white; }
input:checked { accent-color: green; }
input:required { border-left: 3px solid red; }
input:valid { border-color: green; }
input:invalid { border-color: red; }
input:placeholder-shown { font-style: italic; }
```

**3. Structural Pseudo-classes:**

```css
li:first-child { font-weight: bold; }
li:last-child { border-bottom: none; }
li:nth-child(2) { color: red; }           /* Second item */
li:nth-child(odd) { background: #f0f0f0; } /* 1st, 3rd, 5th... */
li:nth-child(even) { background: #fff; }   /* 2nd, 4th, 6th... */
li:nth-child(3n) { color: blue; }          /* Every 3rd item */
li:nth-child(3n+1) { color: green; }       /* 1st, 4th, 7th... */

p:first-of-type { font-size: 1.2em; }
p:last-of-type { margin-bottom: 0; }
p:only-child { text-align: center; }
div:empty { display: none; }

:root { --primary-color: blue; }
```

**4. Negation Pseudo-class:**

```css
p:not(.intro) { color: gray; }
li:not(:last-child) { border-bottom: 1px solid #ccc; }
input:not([type="submit"]) { border: 1px solid #ccc; }
```

### Pseudo-Element Selectors

```css
p::first-letter { font-size: 2em; font-weight: bold; float: left; }
p::first-line { font-weight: bold; }

.required::before { content: "* "; color: red; }
a[href^="http"]::after { content: " ↗"; }

::selection { background-color: yellow; color: black; }
input::placeholder { color: #999; font-style: italic; }
```

### Selector Grouping

```css
h1, h2, h3, h4, h5, h6 {
    font-family: Georgia, serif;
    color: #333;
}

.btn-primary,
.btn-secondary,
.btn-danger {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}
```

---

## 4.5 CSS Comments

Comments are used to explain code and are ignored by browsers.

```css
/* Single-line comment */

/*
 * Multi-line comment
 * Used for documentation
 */

/* ========================================
   SECTION: HEADER STYLES
   ======================================== */

p {
    color: blue;  /* Inline comment */
}
```

**Best Practices:**
- Comment complex or non-obvious code
- Use comments to organize sections
- Don't over-comment obvious code
- Keep comments up to date

---

## 4.6 CSS Properties

### 4.6.1 Backgrounds

```css
/* background-color */
body {
    background-color: #f0f0f0;
    background-color: rgb(240, 240, 240);
    background-color: rgba(0, 0, 0, 0.5);  /* With transparency */
}

/* background-image */
.hero {
    background-image: url('image.jpg');
    background-image: linear-gradient(to right, red, blue);
    background-image: radial-gradient(circle, white, black);
}

/* background-repeat */
.element {
    background-repeat: repeat;     /* Default: tile both ways */
    background-repeat: repeat-x;   /* Tile horizontally */
    background-repeat: repeat-y;   /* Tile vertically */
    background-repeat: no-repeat;  /* Don't tile */
}

/* background-position */
.element {
    background-position: center center;
    background-position: 50% 50%;
    background-position: 100px 50px;
}

/* background-size */
.element {
    background-size: auto;          /* Original size */
    background-size: cover;         /* Cover entire area */
    background-size: contain;       /* Fit within area */
    background-size: 100px 200px;   /* Width height */
}

/* background-attachment */
.element {
    background-attachment: scroll;  /* Scrolls with content */
    background-attachment: fixed;   /* Fixed to viewport */
}

/* background (Shorthand) */
.element {
    background: #f0f0f0 url('bg.jpg') center/cover no-repeat fixed;
}

/* Hero with overlay */
.hero {
    background:
        linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)),
        url('hero.jpg') center/cover no-repeat;
}
```

### 4.6.2 Border and Margin

**Border:**

```css
/* border-width */
.element { border-width: 1px; }
.element { border-width: 1px 2px 3px 4px; }  /* top right bottom left */

/* border-style */
.element {
    border-style: solid;    /* Also: none, dashed, dotted, double, groove, ridge, inset, outset */
}

/* border-color */
.element { border-color: #333; }

/* border (Shorthand) */
.element {
    border: 1px solid #333;
    border-top: 2px dashed red;
    border-bottom: 3px double green;
}

/* border-radius */
.element {
    border-radius: 5px;                    /* All corners */
    border-radius: 50%;                    /* Circle/ellipse */
    border-radius: 10px 20px 30px 40px;    /* Each corner */
    border-top-left-radius: 10px;          /* Individual corner */
}
```

**Margin:**

Margin creates space OUTSIDE the element.

```css
.element {
    margin: 20px;                     /* All sides */
    margin: 10px 20px;                /* Vertical horizontal */
    margin: 10px 20px 30px;           /* Top horizontal bottom */
    margin: 10px 20px 30px 40px;      /* Top right bottom left */

    margin-top: 10px;
    margin-right: 20px;
    margin-bottom: 30px;
    margin-left: 40px;

    margin: 0 auto;                   /* Center horizontally */
    margin-top: -10px;                /* Negative margins */
}
```

**Margin Collapsing:**

```css
/* Vertical margins of adjacent elements collapse */
.box1 { margin-bottom: 20px; }
.box2 { margin-top: 30px; }
/* Actual gap = 30px (larger margin wins, not 50px) */
```

### 4.6.3 Padding

Padding creates space INSIDE the element (between content and border).

```css
.element {
    padding: 20px;                     /* All sides */
    padding: 10px 20px;                /* Vertical horizontal */
    padding: 10px 20px 30px 40px;      /* Top right bottom left */

    padding-top: 10px;
    padding-right: 20px;
    padding-bottom: 30px;
    padding-left: 40px;
}
```

**Margin vs Padding:**

```
┌─────────────────────────────┐
│ MARGIN (outside)            │
│  ┌──────────────────────┐   │
│  │ BORDER               │   │
│  │  ┌────────────────┐  │   │
│  │  │ PADDING (inside)│  │   │
│  │  │  ┌──────────┐  │  │   │
│  │  │  │ CONTENT  │  │  │   │
│  │  │  └──────────┘  │  │   │
│  │  └────────────────┘  │   │
│  └──────────────────────┘   │
└─────────────────────────────┘
```

### 4.6.4 Height

```css
.element {
    height: 200px;
    height: 50%;           /* Percentage of parent */
    height: auto;          /* Default: fit content */
    height: 100vh;         /* Viewport height */

    min-height: 100px;
    max-height: 500px;
}
```

### 4.6.5 Width

```css
.element {
    width: 300px;
    width: 50%;            /* Percentage of parent */
    width: auto;           /* Default */
    width: 100vw;          /* Viewport width */
    width: fit-content;
    width: max-content;
    width: min-content;

    min-width: 200px;
    max-width: 1200px;
}
```

### 4.6.6 Color (Color Wheel)

**Color Formats:**

```css
/* 1. Named Colors (140+ available) */
color: red;
color: rebeccapurple;

/* 2. Hexadecimal */
color: #ff0000;        /* Red */
color: #f00;           /* Shorthand */
color: #ff0000ff;      /* With alpha */

/* 3. RGB */
color: rgb(255, 0, 0);

/* 4. RGBA (with transparency) */
color: rgba(255, 0, 0, 0.5);    /* 50% transparent */

/* 5. HSL (Hue, Saturation, Lightness) */
color: hsl(0, 100%, 50%);       /* Red */
color: hsl(120, 100%, 50%);     /* Green */
color: hsl(240, 100%, 50%);     /* Blue */

/* 6. HSLA */
color: hsla(0, 100%, 50%, 0.5);

/* Modern syntax (CSS Color Level 4) */
color: rgb(255 0 0 / 50%);
color: hsl(0 100% 50% / 50%);
```

**HSL Color Wheel:**
- **Hue**: 0-360 (position on color wheel)
- **Saturation**: 0-100% (gray to full color)
- **Lightness**: 0-100% (black to white)

| Color | HSL Value |
|-------|-----------|
| Red | `hsl(0, 100%, 50%)` |
| Orange | `hsl(30, 100%, 50%)` |
| Yellow | `hsl(60, 100%, 50%)` |
| Green | `hsl(120, 100%, 50%)` |
| Cyan | `hsl(180, 100%, 50%)` |
| Blue | `hsl(240, 100%, 50%)` |
| Magenta | `hsl(300, 100%, 50%)` |

---

## 4.7 Text

### Text Properties

```css
/* color */
p { color: #333; }

/* text-align */
.element {
    text-align: left;      /* Default */
    text-align: center;
    text-align: right;
    text-align: justify;   /* Stretch to fill width */
}

/* text-decoration */
.element {
    text-decoration: none;
    text-decoration: underline;
    text-decoration: overline;
    text-decoration: line-through;

    /* Detailed control */
    text-decoration-line: underline;
    text-decoration-color: red;
    text-decoration-style: wavy;  /* solid, double, dotted, dashed, wavy */
    text-decoration-thickness: 2px;
}

/* text-transform */
.element {
    text-transform: uppercase;   /* ALL CAPS */
    text-transform: lowercase;   /* all lowercase */
    text-transform: capitalize;  /* First Letter Of Each Word */
}

/* text-indent */
p { text-indent: 50px; }

/* text-shadow */
.element {
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);  /* x y blur color */
    text-shadow: 1px 1px 2px black, 0 0 10px blue;  /* Multiple */
}

/* letter-spacing */
.element { letter-spacing: 2px; }

/* word-spacing */
.element { word-spacing: 10px; }

/* white-space */
.element {
    white-space: normal;     /* Default: collapse spaces, wrap */
    white-space: nowrap;     /* No wrapping */
    white-space: pre;        /* Preserve all whitespace */
    white-space: pre-wrap;   /* Preserve, but wrap */
}

/* text-overflow (with ellipsis) */
.element {
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
}

/* word-break */
.element { word-break: break-all; }

/* overflow-wrap */
.element { overflow-wrap: break-word; }
```

---

## 4.8 Font

### Font Properties

```css
/* font-family (font stack) */
body {
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
```

**Generic Font Families:**
- `serif`: Times New Roman, Georgia
- `sans-serif`: Arial, Helvetica, Verdana
- `monospace`: Courier, Consolas
- `cursive`: Comic Sans, Brush Script
- `fantasy`: Impact, Papyrus

```css
/* font-size */
.element {
    font-size: 16px;
    font-size: 1rem;       /* Relative to root */
    font-size: 1.2em;      /* Relative to parent */
}

/* font-weight */
.element {
    font-weight: normal;   /* 400 */
    font-weight: bold;     /* 700 */
    font-weight: 100;      /* Thin */
    font-weight: 300;      /* Light */
    font-weight: 500;      /* Medium */
    font-weight: 600;      /* Semi Bold */
    font-weight: 900;      /* Black */
}

/* font-style */
.element {
    font-style: normal;
    font-style: italic;
    font-style: oblique;
}

/* font-variant */
.element { font-variant: small-caps; }

/* font (Shorthand): style variant weight size/line-height family */
.element {
    font: italic small-caps bold 16px/1.5 Arial, sans-serif;
    font: 400 1rem/1.6 "Open Sans", sans-serif;
}
```

### Web Fonts

**Google Fonts (in HTML):**

```html
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
```

**Google Fonts (in CSS):**

```css
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
```

**Custom Fonts (@font-face):**

```css
@font-face {
    font-family: 'MyCustomFont';
    src: url('fonts/myfont.woff2') format('woff2'),
         url('fonts/myfont.woff') format('woff');
    font-weight: normal;
    font-style: normal;
    font-display: swap;  /* Show fallback while loading */
}

body {
    font-family: 'MyCustomFont', sans-serif;
}
```

---

## 4.9 Alignment

### Text Alignment

```css
.element {
    text-align: left;
    text-align: center;
    text-align: right;
    text-align: justify;
}
```

### Vertical Alignment

```css
/* For inline/inline-block elements */
img {
    vertical-align: baseline;  /* Default */
    vertical-align: top;
    vertical-align: middle;
    vertical-align: bottom;
}
```

### Centering Techniques

**1. Horizontal Center - Block Element:**

```css
.center-block {
    width: 300px;
    margin: 0 auto;
}
```

**2. Horizontal Center - Inline/Text:**

```css
.center-text { text-align: center; }
```

**3. Vertical Center - Single Line Text:**

```css
.center-single-line {
    height: 100px;
    line-height: 100px;  /* Same as height */
}
```

**4. Vertical + Horizontal Center - Flexbox:**

```css
.flex-center {
    display: flex;
    justify-content: center;  /* Horizontal */
    align-items: center;      /* Vertical */
}
```

**5. Absolute Center:**

```css
.absolute-center {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

**6. Grid Center:**

```css
.grid-center {
    display: grid;
    place-items: center;
}
```

---

## 4.10 Line Height

Line height controls the space between lines of text.

```css
.element {
    line-height: normal;      /* Default: ~1.2 */
    line-height: 1.5;         /* Unitless (recommended) */
    line-height: 150%;        /* Percentage */
    line-height: 24px;        /* Fixed */
}
```

**Why Unitless is Best:**

```css
/* Children inherit the multiplier, not the computed value */
body {
    font-size: 16px;
    line-height: 1.5;  /* 24px, but children recalculate */
}

h1 {
    font-size: 32px;
    /* line-height becomes 48px (32 * 1.5) */
}
```

**Readability Guidelines:**
- Body text: 1.4 to 1.6
- Headings: 1.1 to 1.3
- Line length: 45-75 characters

---

## 4.11 Box Model

Every HTML element is a rectangular box with four areas.

### The CSS Box Model

```
┌────────────────────────────────────────────┐
│                 MARGIN                      │
│  ┌──────────────────────────────────────┐  │
│  │              BORDER                  │  │
│  │  ┌────────────────────────────────┐  │  │
│  │  │           PADDING              │  │  │
│  │  │  ┌──────────────────────────┐  │  │  │
│  │  │  │        CONTENT           │  │  │  │
│  │  │  │     (width x height)     │  │  │  │
│  │  │  └──────────────────────────┘  │  │  │
│  │  └────────────────────────────────┘  │  │
│  └──────────────────────────────────────┘  │
└────────────────────────────────────────────┘
```

**Components:**
1. **Content**: The actual content (text, images)
2. **Padding**: Space between content and border (inside)
3. **Border**: Surrounds the padding
4. **Margin**: Space outside the border (between elements)

### box-sizing Property

**`content-box` (Default):** Width/height applies to content only.

```css
.element {
    box-sizing: content-box;
    width: 200px;
    padding: 20px;
    border: 5px solid black;
}
/* Total width = 200 + 40 + 10 = 250px */
```

**`border-box` (Recommended):** Width/height includes padding and border.

```css
.element {
    box-sizing: border-box;
    width: 200px;
    padding: 20px;
    border: 5px solid black;
}
/* Total width = 200px (content shrinks to 150px) */
```

**Universal Border-Box (Best Practice):**

```css
*, *::before, *::after {
    box-sizing: border-box;
}
```

### Calculating Total Dimensions

**With `content-box`:**
```
Total Width = width + padding-left + padding-right + border-left + border-right
Example: 300 + 20 + 20 + 5 + 5 = 350px
```

**With `border-box`:**
```
Total Width = width (set value)
Content Width = width - padding - border
```

---

## 4.12 Working with Images

### Basic Image Styling

```css
img {
    max-width: 100%;       /* Responsive */
    height: auto;          /* Maintain aspect ratio */
    display: block;        /* Remove bottom gap */
}
```

### object-fit

Controls how content fits within its container.

```css
.image-container img {
    width: 300px;
    height: 200px;

    object-fit: fill;       /* Stretch to fill (distorts) */
    object-fit: contain;    /* Fit inside, maintain ratio */
    object-fit: cover;      /* Cover area, crop if needed */
    object-fit: none;       /* Original size */
    object-fit: scale-down; /* Smaller of none or contain */
}
```

### object-position

```css
img {
    object-fit: cover;
    object-position: center center;  /* Default */
    object-position: top left;
    object-position: 50% 25%;
}
```

### Image Effects

```css
img {
    border: 3px solid #333;
    border-radius: 10px;
    border-radius: 50%;    /* Circle */

    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);

    filter: grayscale(100%);
    filter: blur(5px);
    filter: brightness(1.2);
    filter: contrast(1.5);
    filter: sepia(100%);
}
```

### Background Images

```css
.hero {
    background-image: url('hero.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    min-height: 400px;
}

/* Image with overlay */
.hero-overlay {
    background:
        linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)),
        url('hero.jpg') center/cover no-repeat;
}
```

### Image Gallery Example

```css
.gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 10px;
}

.gallery img {
    width: 100%;
    height: 200px;
    object-fit: cover;
    border-radius: 5px;
    transition: transform 0.3s ease;
}

.gallery img:hover {
    transform: scale(1.05);
}
```

---

## 4.13 Layout and Positioning

### Display Property

```css
.element {
    display: block;        /* Full width, new line */
    display: inline;       /* Inline with text flow */
    display: inline-block; /* Inline but accepts width/height */
    display: none;         /* Hidden, removed from flow */
    display: flex;         /* Flexbox container */
    display: grid;         /* Grid container */
}
```

**Block vs Inline vs Inline-Block:**
- **Block** (div, p, h1-h6): Takes full width, starts on new line, accepts width/height
- **Inline** (span, a, strong): Flows with text, does NOT accept width/height
- **Inline-Block**: Flows inline but accepts width/height

### Position Property

**1. `static` (Default):**

```css
.element { position: static; }
/* Normal document flow, top/right/bottom/left don't work */
```

**2. `relative`:**

```css
.element {
    position: relative;
    top: 10px;
    left: 20px;
}
/* Offset from normal position, space still reserved */
```

**3. `absolute`:**

```css
.element {
    position: absolute;
    top: 0;
    right: 0;
}
/* Removed from flow, positioned relative to nearest positioned ancestor */
```

**4. `fixed`:**

```css
.element {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
}
/* Fixed to viewport, doesn't move on scroll */
```

**5. `sticky`:**

```css
.element {
    position: sticky;
    top: 0;
}
/* Normal until scroll position reached, then fixed */
```

### Z-Index

Controls stacking order of positioned elements.

```css
.behind { position: relative; z-index: 1; }
.infront { position: relative; z-index: 2; }    /* Higher = in front */
.way-back { position: relative; z-index: -1; }  /* Behind normal flow */
```

### Float and Clear

```css
/* Float */
.image-left { float: left; margin-right: 20px; }
.image-right { float: right; margin-left: 20px; }

/* Clear */
.clear-both { clear: both; }

/* Clearfix (for parent of floated elements) */
.clearfix::after {
    content: "";
    display: table;
    clear: both;
}
```

### Overflow

```css
.element {
    overflow: visible;  /* Default: content spills out */
    overflow: hidden;   /* Clip content */
    overflow: scroll;   /* Always show scrollbars */
    overflow: auto;     /* Scrollbars when needed */

    overflow-x: hidden;
    overflow-y: auto;
}
```

### Visibility

```css
.element {
    visibility: visible;  /* Default */
    visibility: hidden;   /* Hidden but space preserved */
}
/* vs display: none which removes element from flow entirely */
```

---

## 4.14 Media Query

Media queries apply styles based on device characteristics.

### Basic Syntax

```css
@media media-type and (condition) {
    /* CSS rules */
}
```

### Media Types

```css
@media all { }      /* All devices (default) */
@media screen { }   /* Screens */
@media print { }    /* Printed pages */
@media speech { }   /* Screen readers */
```

### Width-Based Queries

**Mobile First (min-width):**

```css
/* Base styles for mobile */

@media (min-width: 576px) { /* Small devices and up */ }
@media (min-width: 768px) { /* Medium devices and up */ }
@media (min-width: 992px) { /* Large devices and up */ }
@media (min-width: 1200px) { /* Extra large devices */ }
```

**Desktop First (max-width):**

```css
@media (max-width: 1199px) { /* Below extra large */ }
@media (max-width: 991px) { /* Below large */ }
@media (max-width: 767px) { /* Below medium (tablets) */ }
@media (max-width: 575px) { /* Mobile only */ }
```

### Range Queries

```css
/* Between two widths */
@media (min-width: 768px) and (max-width: 991px) {
    /* Tablets only */
}

/* Modern syntax */
@media (768px <= width <= 991px) {
    /* Same as above */
}
```

### Other Conditions

```css
/* Orientation */
@media (orientation: portrait) { }
@media (orientation: landscape) { }

/* Resolution (Retina/HiDPI) */
@media (min-resolution: 2dppx) { }

/* Hover capability */
@media (hover: hover) { }    /* Has hover (mouse) */
@media (hover: none) { }     /* Touch devices */

/* Pointer precision */
@media (pointer: fine) { }   /* Mouse */
@media (pointer: coarse) { } /* Touch */

/* Prefers color scheme (Dark mode) */
@media (prefers-color-scheme: dark) {
    body { background: #333; color: #fff; }
}

@media (prefers-color-scheme: light) {
    body { background: #fff; color: #333; }
}

/* Reduced motion */
@media (prefers-reduced-motion: reduce) {
    * { animation: none !important; transition: none !important; }
}
```

### Combining Conditions

```css
/* AND */
@media screen and (min-width: 768px) and (orientation: landscape) { }

/* OR (comma) */
@media (max-width: 600px), (orientation: portrait) { }

/* NOT */
@media not print { }
```

### Practical Example

```css
/* Base styles (mobile) */
.container { width: 100%; padding: 15px; }
.card { width: 100%; margin-bottom: 20px; }

/* Tablet */
@media (min-width: 768px) {
    .container { max-width: 750px; margin: 0 auto; }
    .card { width: 48%; display: inline-block; }
}

/* Desktop */
@media (min-width: 992px) {
    .container { max-width: 970px; }
    .card { width: 31%; }
}

/* Large Desktop */
@media (min-width: 1200px) {
    .container { max-width: 1170px; }
}
```

### Viewport Meta Tag

Required in HTML for responsive design on mobile:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

---

## 4.15 CSS Website Layout

### Common Layout Patterns

**1. Single Column Layout:**

```css
.container {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
}
```

**2. Two Column Layout (Flexbox):**

```css
.wrapper { display: flex; }
.main-content { flex: 2; }
.sidebar { flex: 1; }
```

**3. Three Column Layout (Holy Grail):**

```html
<div class="holy-grail">
    <header>Header</header>
    <div class="content">
        <nav class="sidebar-left">Left</nav>
        <main>Main Content</main>
        <aside class="sidebar-right">Right</aside>
    </div>
    <footer>Footer</footer>
</div>
```

```css
.holy-grail { display: flex; flex-direction: column; min-height: 100vh; }
.content { display: flex; flex: 1; }
.sidebar-left, .sidebar-right { flex: 0 0 200px; }
main { flex: 1; }

@media (max-width: 768px) {
    .content { flex-direction: column; }
    .sidebar-left, .sidebar-right { flex: 0 0 auto; }
}
```

**4. Header-Main-Footer (Sticky Footer):**

```css
body {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    margin: 0;
}
header { background: #333; color: white; padding: 20px; }
main { flex: 1; padding: 20px; }  /* Pushes footer down */
footer { background: #333; color: white; padding: 20px; text-align: center; }
```

**5. Card Layout:**

```css
.card-container {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
}

.card {
    flex: 1 1 300px;
    max-width: 400px;
    background: white;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    overflow: hidden;
}

.card img { width: 100%; height: 200px; object-fit: cover; }
.card-content { padding: 20px; }
```

**6. Navigation Bar:**

```css
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background: #333;
}

.logo { color: white; font-size: 1.5rem; font-weight: bold; }

.nav-links {
    display: flex;
    list-style: none;
    gap: 2rem;
}

.nav-links a { color: white; text-decoration: none; }
.nav-links a:hover { color: #3498db; }

/* Mobile menu */
@media (max-width: 768px) {
    .nav-links {
        display: none;
        flex-direction: column;
        position: absolute;
        top: 70px;
        left: 0;
        right: 0;
        background: #333;
        padding: 1rem;
    }
    .nav-links.active { display: flex; }
}
```

**7. Full Page Sections:**

```css
section {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 2rem;
}

.hero {
    background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)),
                url('hero.jpg') center/cover;
    color: white;
    text-align: center;
}
```

### Complete Website Layout Example

```css
/* Reset */
* { margin: 0; padding: 0; box-sizing: border-box; }

body { font-family: 'Segoe UI', Arial, sans-serif; line-height: 1.6; color: #333; }

/* Container */
.container { max-width: 1200px; margin: 0 auto; padding: 0 20px; }

/* Header */
header {
    background: #2c3e50;
    padding: 1rem 0;
    position: sticky;
    top: 0;
    z-index: 100;
}

header .container { display: flex; justify-content: space-between; align-items: center; }

/* Navigation */
nav ul { display: flex; list-style: none; gap: 2rem; }
nav a { color: white; text-decoration: none; transition: color 0.3s; }
nav a:hover { color: #3498db; }

/* Hero Section */
.hero {
    height: 80vh;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    color: white;
}

/* Main Content */
main { padding: 4rem 0; }

/* Sidebar Layout */
.content-wrapper { display: flex; gap: 2rem; }
.main-content { flex: 2; }
.sidebar { flex: 1; background: #f8f9fa; padding: 1.5rem; border-radius: 8px; }

/* Footer */
footer { background: #2c3e50; color: white; padding: 2rem 0; text-align: center; }

/* Responsive */
@media (max-width: 768px) {
    nav ul { display: none; }
    .content-wrapper { flex-direction: column; }
    .hero { height: 60vh; }
}
```

---

## Summary

| Topic | Key Points |
|-------|-----------|
| Introduction to CSS | Purpose, separation of concerns, CSS history |
| CSS Syntax | Selectors, properties, values, declarations |
| Using CSS with HTML | Inline, internal, external; cascade priority |
| CSS Selectors | Basic, combinator, pseudo-class, pseudo-element, attribute |
| CSS Properties | Backgrounds, borders, margins, padding, colors |
| Text & Font | Alignment, decoration, transform, font families, web fonts |
| Box Model | Content, padding, border, margin; box-sizing |
| Layout & Positioning | Display, position (static/relative/absolute/fixed/sticky), float, z-index |
| Media Queries | Breakpoints, responsive design, mobile-first approach |
| Website Layout | Common patterns, navigation, card layouts, responsive layouts |

---

## Study Questions

1. What is CSS and why is it important in web development?
2. Compare the three methods of applying CSS to HTML (inline, internal, external).
3. Explain the CSS cascade and specificity. How do they determine which styles are applied?
4. What are pseudo-classes and pseudo-elements? Give three examples of each.
5. Explain the CSS box model with a diagram. What is the difference between `content-box` and `border-box`?
6. What is the difference between margin and padding?
7. Explain the five CSS position values with examples.
8. What are media queries? How do you implement a mobile-first responsive design?
9. What are the different color formats in CSS? Explain HSL.
10. How do you center an element both horizontally and vertically using CSS?
