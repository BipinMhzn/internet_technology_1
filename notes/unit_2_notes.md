# Unit 2: Hyper Text Markup Language (HTML)

## 2.1 Introduction to HTML

### What is HTML?

HTML (HyperText Markup Language) is the standard markup language for creating web pages. It describes the structure of a web page using a series of elements that tell the browser how to display the content.

**Key Terms:**
- **HyperText**: Text that contains links to other texts
- **Markup**: Tags that define the structure and meaning of content
- **Language**: A system of syntax and rules for creating documents

### History of HTML

| Year | Version | Key Features |
|------|---------|-------------|
| 1991 | HTML 1.0 | Created by Tim Berners-Lee |
| 1995 | HTML 2.0 | First standard specification |
| 1997 | HTML 3.2 | Added tables, applets, text flow |
| 1999 | HTML 4.01 | Improved forms, scripting, stylesheets |
| 2000 | XHTML 1.0 | XML-based HTML |
| 2014 | HTML5 | Current standard with multimedia, APIs |

### Role of HTML in Web Development

HTML is one of three core technologies of the World Wide Web:

- **HTML** = Structure (Skeleton) - Defines content and layout: headings, paragraphs, lists, images, links, forms
- **CSS** = Presentation (Skin/Clothes) - Colors, fonts, spacing, layout, positioning
- **JavaScript** = Behavior (Muscles) - Interactivity, dynamic content updates

### HTML Basics

**1. Elements:**

An element is a complete unit consisting of opening tag, content, and closing tag.

```html
<tagname>Content goes here</tagname>

<!-- Examples -->
<p>This is a paragraph.</p>
<h1>This is a heading</h1>
```

**2. Tags:**

Tags are markers that define the start and end of an element.

```
Opening tag: <tagname>
Closing tag: </tagname>
```

Self-closing tags (void elements):
- `<br>` - Line break
- `<hr>` - Horizontal rule
- `<img>` - Image
- `<input>` - Input field
- `<meta>` - Metadata
- `<link>` - External resource

> Note: In XHTML/XML style: `<br />` `<hr />` `<img />`

**3. Attributes:**

Attributes provide additional information about elements.

```html
<tagname attribute="value">Content</tagname>

<!-- Examples -->
<a href="https://example.com">Link</a>
<img src="image.jpg" alt="Description" width="300" height="200">
```

**Common Global Attributes:**
- `id` - Unique identifier
- `class` - CSS class name(s)
- `style` - Inline CSS styles
- `title` - Tooltip text
- `lang` - Language code
- `dir` - Text direction (ltr/rtl)
- `hidden` - Hide element
- `tabindex` - Tab order

**4. Nesting:**

Elements can be nested inside other elements.

```html
<div>
    <h1>Title</h1>
    <p>This is a <strong>nested</strong> paragraph.</p>
</div>
```

Rules for nesting:
- Close inner elements before outer elements
- Maintain proper indentation for readability
- Some elements have nesting restrictions

**5. Comments:**

Comments are not displayed in the browser.

```html
<!-- This is a comment -->

<!--
    This is a
    multi-line comment
-->
```

### HTML File Structure

- Filename: `filename.html` or `filename.htm`
- Use lowercase letters
- No spaces (use hyphens: `my-page.html`)
- `index.html` is the default homepage

---

## 2.2 Document Structure

### Basic HTML Document Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title</title>
</head>
<body>
    <!-- Page content goes here -->
</body>
</html>
```

### Document Type Declaration (DOCTYPE)

The DOCTYPE declaration tells the browser which version of HTML is being used.

```html
<!-- HTML5 (Current Standard) -->
<!DOCTYPE html>

<!-- HTML 4.01 Strict (older) -->
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
    "http://www.w3.org/TR/html4/strict.dtd">

<!-- XHTML 1.0 Strict (older) -->
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
```

**Why DOCTYPE is Important:**
- Ensures standards mode rendering
- Prevents quirks mode (inconsistent rendering)
- Required for HTML validation

### The `<html>` Element

Root element that contains all other HTML elements.

```html
<html lang="en" dir="ltr">
    <!-- All content -->
</html>
```

**Attributes:**
- `lang` - Specifies the language (en, ne, hi, etc.)
- `dir` - Text direction (ltr = left-to-right, rtl = right-to-left)

### The `<head>` Element

Contains metadata and links to external resources. Not displayed on the page.

```html
<head>
    <!-- Metadata -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Page description for SEO">
    <meta name="keywords" content="keyword1, keyword2">
    <meta name="author" content="Author Name">

    <!-- Title (shown in browser tab) -->
    <title>Page Title | Website Name</title>

    <!-- Favicon -->
    <link rel="icon" href="favicon.ico" type="image/x-icon">

    <!-- CSS Stylesheets -->
    <link rel="stylesheet" href="styles.css">

    <!-- Internal CSS -->
    <style>
        body { font-family: Arial, sans-serif; }
    </style>

    <!-- JavaScript (in head with defer) -->
    <script src="script.js" defer></script>
</head>
```

### Head Elements in Detail

**1. `<title>`:**

Page title shown in browser tab and search results.

```html
<title>Home | My Website</title>
```

Best practices:
- Keep under 60 characters
- Include main keyword
- Use format: `Page Title | Site Name`

**2. `<meta>` Tags:**

```html
<!-- Character Encoding (UTF-8 supports all characters including Nepali, Chinese, etc.) -->
<meta charset="UTF-8">

<!-- Viewport (for responsive design) -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- Description (for SEO) -->
<meta name="description" content="A brief description of the page content.">

<!-- Keywords (less important for SEO now) -->
<meta name="keywords" content="HTML, CSS, JavaScript, web development">

<!-- Author -->
<meta name="author" content="John Doe">

<!-- Robots (search engine instructions) -->
<meta name="robots" content="index, follow">
<meta name="robots" content="noindex, nofollow">

<!-- Refresh/Redirect -->
<meta http-equiv="refresh" content="5;url=https://example.com">

<!-- Open Graph (for social media sharing) -->
<meta property="og:title" content="Page Title">
<meta property="og:description" content="Page description">
<meta property="og:image" content="https://example.com/image.jpg">
<meta property="og:url" content="https://example.com">
```

**3. `<link>` Element:**

Links external resources.

```html
<!-- Stylesheet -->
<link rel="stylesheet" href="styles.css">

<!-- Favicon -->
<link rel="icon" href="favicon.ico">
<link rel="apple-touch-icon" href="apple-touch-icon.png">

<!-- Preconnect (performance) -->
<link rel="preconnect" href="https://fonts.googleapis.com">

<!-- Preload (performance) -->
<link rel="preload" href="font.woff2" as="font" crossorigin>

<!-- Canonical URL (SEO) -->
<link rel="canonical" href="https://example.com/page">
```

**4. `<style>` Element:**

Internal CSS styles.

```html
<style>
    body {
        margin: 0;
        padding: 0;
        font-family: Arial, sans-serif;
    }
</style>
```

**5. `<script>` Element:**

JavaScript code or link.

```html
<!-- External script -->
<script src="script.js"></script>

<!-- With defer (loads after HTML parsing) -->
<script src="script.js" defer></script>

<!-- With async (loads in parallel) -->
<script src="analytics.js" async></script>

<!-- Internal script -->
<script>
    console.log('Hello, World!');
</script>
```

**6. `<base>` Element:**

Sets base URL for relative links.

```html
<base href="https://example.com/" target="_blank">
```

### The `<body>` Element

Contains all visible content of the web page.

```html
<body>
    <header><!-- Header content --></header>
    <nav><!-- Navigation --></nav>
    <main><!-- Main content --></main>
    <aside><!-- Sidebar --></aside>
    <footer><!-- Footer content --></footer>

    <!-- Scripts at end of body -->
    <script src="script.js"></script>
</body>
```

> Note: Body attributes like `bgcolor`, `text`, `link` are deprecated. Use CSS instead.

### Complete Document Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Page description here">
    <meta name="author" content="Author Name">

    <title>Page Title | Website Name</title>

    <link rel="icon" href="favicon.ico">
    <link rel="stylesheet" href="styles.css">
</head>
<body>
<header>
    <h1>Website Title</h1>
    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
            <li><a href="/contact">Contact</a></li>
        </ul>
    </nav>
</header>

<main>
    <article>
        <h2>Article Title</h2>
        <p>Article content goes here...</p>
    </article>
</main>

<aside>
    <h3>Sidebar</h3>
    <p>Related content...</p>
</aside>

<footer>
    <p>&copy; 2024 Website Name. All rights reserved.</p>
</footer>

<script src="script.js"></script>
</body>
</html>
```

---

## 2.3 Text Formatting

### Headings

HTML provides six levels of headings, from `<h1>` (most important) to `<h6>` (least important).

```html
<h1>Heading Level 1</h1>   <!-- Main page title -->
<h2>Heading Level 2</h2>   <!-- Major sections -->
<h3>Heading Level 3</h3>   <!-- Subsections -->
<h4>Heading Level 4</h4>   <!-- Sub-subsections -->
<h5>Heading Level 5</h5>
<h6>Heading Level 6</h6>
```

**Best Practices:**
- Use only ONE `<h1>` per page
- Don't skip heading levels (h1 -> h3)
- Use headings for structure, not styling
- Keep heading hierarchy logical

### Paragraphs

```html
<p>This is a paragraph of text. Paragraphs automatically add
   space above and below.</p>

<p>This is another paragraph. Each paragraph starts on a new line
   with vertical spacing.</p>
```

### Line Breaks and Horizontal Rules

**Line Break `<br>`:**

```html
<p>This is line one.<br>
This is line two.<br>
This is line three.</p>
```

**Horizontal Rule `<hr>`:**

```html
<p>Content above the line.</p>
<hr>
<p>Content below the line.</p>
```

### Text Formatting Elements

| Element | Purpose | Example |
|---------|---------|---------|
| `<b>` | Visual bold only | `<b>Bold text</b>` |
| `<strong>` | Bold with semantic importance | `<strong>Strong text</strong>` |
| `<i>` | Visual italic only | `<i>Italic text</i>` |
| `<em>` | Italic with semantic emphasis | `<em>Emphasized text</em>` |
| `<u>` | Underlined text | `<u>Underlined text</u>` |
| `<s>` | Strikethrough (no longer relevant) | `<s>Strikethrough</s>` |
| `<del>` | Deleted content | `<del>Deleted text</del>` |
| `<ins>` | Inserted text (shows as underlined) | `<ins>Inserted text</ins>` |
| `<mark>` | Highlighted text | `<mark>Highlighted text</mark>` |
| `<small>` | Small text (fine print) | `<small>Small text</small>` |
| `<sub>` | Subscript | `H<sub>2</sub>O` |
| `<sup>` | Superscript | `E = mc<sup>2</sup>` |

> Use `<strong>` for important text (screen readers emphasize it), use `<b>` for visual styling only. Use `<em>` for emphasized text, use `<i>` for terms, technical words, foreign phrases.

**Preformatted Text:**

```html
<pre>
This text preserves
    all whitespace
        and line breaks.
</pre>
```

**Code:**

```html
<!-- Inline code -->
<code>console.log('Hello');</code>

<!-- Code block -->
<pre><code>
function greet() {
    console.log('Hello');
}
</code></pre>
```

**Other Text Elements:**

```html
<!-- Keyboard Input -->
<p>Press <kbd>Ctrl</kbd> + <kbd>C</kbd> to copy.</p>

<!-- Sample Output -->
<samp>Error: File not found</samp>

<!-- Variable -->
<p>The variable <var>x</var> represents the unknown value.</p>

<!-- Abbreviation (hover shows full text) -->
<abbr title="HyperText Markup Language">HTML</abbr>

<!-- Citation -->
<p>According to <cite>The HTML Handbook</cite>, semantics matter.</p>

<!-- Definition -->
<p><dfn>HTML</dfn> is a markup language for creating web pages.</p>

<!-- Inline quote -->
<p>She said, <q>HTML is awesome!</q></p>

<!-- Block quote -->
<blockquote cite="https://example.com">
    <p>This is a longer quotation that spans multiple lines
       and is indented from the surrounding text.</p>
</blockquote>

<!-- Address -->
<address>
    Written by John Doe.<br>
    Email: john@example.com<br>
    Phone: 123-456-7890
</address>

<!-- Bidirectional Text -->
<bdo dir="rtl">This text is reversed</bdo>
```

### Special Characters (HTML Entities)

HTML entities represent special characters.

| Entity | Symbol | Description |
|--------|--------|-------------|
| `&nbsp;` | (space) | Non-breaking space |
| `&lt;` | < | Less than |
| `&gt;` | > | Greater than |
| `&amp;` | & | Ampersand |
| `&quot;` | " | Quotation mark |
| `&apos;` | ' | Apostrophe |
| `&copy;` | &copy; | Copyright |
| `&reg;` | &reg; | Registered |
| `&trade;` | &trade; | Trademark |
| `&deg;` | &deg; | Degree |
| `&plusmn;` | &plusmn; | Plus-minus |
| `&times;` | &times; | Multiplication |
| `&divide;` | &divide; | Division |
| `&euro;` | &euro; | Euro |
| `&pound;` | &pound; | Pound |
| `&yen;` | &yen; | Yen |
| `&mdash;` | &mdash; | Em dash |
| `&ndash;` | &ndash; | En dash |
| `&hellip;` | &hellip; | Ellipsis |
| `&larr;` | &larr; | Left arrow |
| `&rarr;` | &rarr; | Right arrow |

```html
<p>Price: $99.99 &copy; 2024</p>
<p>5 &lt; 10 &amp; 10 &gt; 5</p>
```

**Numeric Character References:**
- `&#169;` - &copy; (decimal)
- `&#x00A9;` - &copy; (hexadecimal)

---

## 2.4 Links and Navigation

### The Anchor Element `<a>`

The anchor element creates hyperlinks to other pages, files, or locations.

```html
<a href="URL">Link Text</a>
```

### Link Types

**1. External Links (to other websites):**

```html
<a href="https://www.google.com">Visit Google</a>
<a href="https://www.example.com">Example Website</a>
```

**2. Internal Links (to pages within same website):**

```html
<a href="about.html">About Us</a>
<a href="pages/contact.html">Contact</a>
<a href="../index.html">Back to Home</a>
```

**3. Anchor Links (to specific location on page):**

```html
<!-- Create anchor target -->
<h2 id="section1">Section 1</h2>

<!-- Link to anchor -->
<a href="#section1">Go to Section 1</a>

<!-- Link to anchor on another page -->
<a href="page.html#section1">Section 1 on another page</a>
```

**4. Email Links:**

```html
<a href="mailto:info@example.com">Email Us</a>

<!-- With subject and body -->
<a href="mailto:info@example.com?subject=Hello&body=Message%20here">
    Email with Subject
</a>
```

**5. Telephone Links:**

```html
<a href="tel:+9779800000000">Call Us</a>
```

**6. Download Links:**

```html
<a href="document.pdf" download>Download PDF</a>
<a href="image.png" download="my-image.png">Download Image</a>
```

### Anchor Attributes

| Attribute | Description | Example |
|-----------|-------------|---------|
| `href` | Hypertext reference (URL) | `href="https://example.com"` |
| `target` | Where to open the link | `target="_blank"` |
| `rel` | Relationship to linked page | `rel="noopener noreferrer"` |
| `title` | Tooltip text | `title="Click to visit"` |
| `hreflang` | Language of linked page | `hreflang="ne"` |

**Target values:**
- `_self` - Same window (default)
- `_blank` - New tab/window
- `_parent` - Parent frame
- `_top` - Full window

```html
<!-- External link with security best practice -->
<a href="https://example.com" target="_blank" rel="noopener noreferrer">
    External Link
</a>
```

### Creating a Navigation Menu

**Basic Navigation:**

```html
<nav>
    <ul>
        <li><a href="index.html">Home</a></li>
        <li><a href="about.html">About</a></li>
        <li><a href="services.html">Services</a></li>
        <li><a href="contact.html">Contact</a></li>
    </ul>
</nav>
```

**Dropdown Navigation:**

```html
<nav>
    <ul>
        <li><a href="index.html">Home</a></li>
        <li>
            <a href="products.html">Products</a>
            <ul>
                <li><a href="product1.html">Product 1</a></li>
                <li><a href="product2.html">Product 2</a></li>
                <li><a href="product3.html">Product 3</a></li>
            </ul>
        </li>
        <li><a href="about.html">About</a></li>
        <li><a href="contact.html">Contact</a></li>
    </ul>
</nav>
```

**Breadcrumb Navigation:**

```html
<nav aria-label="Breadcrumb">
    <ol>
        <li><a href="/">Home</a></li>
        <li><a href="/products">Products</a></li>
        <li><a href="/products/electronics">Electronics</a></li>
        <li aria-current="page">Laptops</li>
    </ol>
</nav>
```

**Skip Navigation (Accessibility):**

```html
<a href="#main-content" class="skip-link">Skip to main content</a>
<!-- ... navigation ... -->
<main id="main-content">
    <!-- Main content -->
</main>
```

---

## 2.5 Hyperlink

### Understanding URLs

**URL (Uniform Resource Locator) Structure:**

```
protocol://domain:port/path/filename?query#fragment
```

**Example:**
```
https://www.example.com:443/products/item.html?id=123#reviews
```

| Component | Value | Description |
|-----------|-------|-------------|
| Protocol | `https` | (or http, ftp, mailto, tel) |
| Domain | `www.example.com` | Host name |
| Port | `443` | (default 443 for HTTPS, 80 for HTTP) |
| Path | `/products/` | Resource location |
| Filename | `item.html` | Specific file |
| Query | `?id=123` | Parameters |
| Fragment | `#reviews` | Page section |

### Absolute vs Relative URLs

**Absolute URLs (Complete path):**

```html
<a href="https://www.example.com/pages/about.html">About</a>
<img src="https://www.example.com/images/logo.png" alt="Logo">
```

Use for links to external websites or when the complete URL is needed.

**Relative URLs (Relative to current location):**

```html
<!-- Same directory -->
<a href="about.html">About</a>

<!-- Subdirectory -->
<a href="pages/about.html">About</a>

<!-- Parent directory -->
<a href="../index.html">Home</a>

<!-- Root-relative (from website root) -->
<a href="/pages/about.html">About</a>
```

### Path Navigation

Given the website structure:
```
mywebsite/
├── index.html
├── about.html
├── css/
│   └── styles.css
├── images/
│   ├── logo.png
│   └── banner.jpg
└── pages/
    ├── contact.html
    └── services/
        └── web-design.html
```

**From `index.html`:**
- To about.html: `href="about.html"`
- To contact.html: `href="pages/contact.html"`
- To web-design.html: `href="pages/services/web-design.html"`

**From `contact.html` (in pages/):**
- To index.html: `href="../index.html"`
- To about.html: `href="../about.html"`
- To logo.png: `src="../images/logo.png"`

**From `web-design.html` (in pages/services/):**
- To index.html: `href="../../index.html"`
- To contact.html: `href="../contact.html"`

### Link States (CSS)

```css
a:link { color: blue; }        /* Unvisited link */
a:visited { color: purple; }   /* Visited link */
a:hover { color: red; }        /* Mouse over */
a:active { color: orange; }    /* Being clicked */

/* Order matters: LoVe HAte (Link, Visited, Hover, Active) */
```

### Image as Link

```html
<a href="https://example.com">
    <img src="button.png" alt="Click here">
</a>
```

---

## 2.6 Images and Multimedia

### Images

**The `<img>` Element:**

```html
<img src="image.jpg" alt="Description of image">
```

**Required Attributes:**
- `src` - Source (path to image)
- `alt` - Alternative text (for accessibility and when image doesn't load)

**Optional Attributes:**

```html
<img src="photo.jpg"
     alt="A beautiful sunset"
     width="800"
     height="600"
     title="Sunset photo"
     loading="lazy"
     decoding="async">
```

- `width` / `height` - Dimensions in pixels or percentage
- `title` - Tooltip on hover
- `loading` - `"lazy"` (defer loading) or `"eager"` (load immediately)
- `decoding` - `"async"` (decode asynchronously)

### Image Formats

| Format | Best For | Features |
|--------|----------|----------|
| JPEG | Photos, complex images | Lossy compression |
| PNG | Graphics, transparency | Lossless, alpha channel |
| GIF | Simple animations | 256 colors, animation |
| WebP | Modern web (photos/graphics) | Better compression |
| SVG | Icons, logos, vector art | Scalable, small size |
| AVIF | Modern web (best quality) | Best compression |

### Responsive Images

```html
<!-- CSS approach -->
<style>
    img { max-width: 100%; height: auto; }
</style>

<!-- HTML5 srcset (resolution switching) -->
<img src="photo-small.jpg"
     srcset="photo-small.jpg 300w,
             photo-medium.jpg 600w,
             photo-large.jpg 1200w"
     sizes="(max-width: 600px) 300px,
            (max-width: 1200px) 600px,
            1200px"
     alt="Mountain landscape">

<!-- Picture element (art direction) -->
<picture>
    <source media="(min-width: 1200px)" srcset="photo-large.jpg">
    <source media="(min-width: 600px)" srcset="photo-medium.jpg">
    <img src="photo-small.jpg" alt="Mountain landscape">
</picture>

<!-- Different formats with fallback -->
<picture>
    <source type="image/avif" srcset="photo.avif">
    <source type="image/webp" srcset="photo.webp">
    <img src="photo.jpg" alt="Mountain landscape">
</picture>
```

### Figure with Caption

```html
<figure>
    <img src="chart.png" alt="Sales data chart">
    <figcaption>Figure 1: Quarterly sales data for 2024</figcaption>
</figure>
```

### Image Map (Clickable Areas)

```html
<img src="world-map.jpg" alt="World Map" usemap="#worldmap">
<map name="worldmap">
    <area shape="rect" coords="0,0,100,100" href="europe.html" alt="Europe">
    <area shape="circle" coords="200,150,50" href="asia.html" alt="Asia">
    <area shape="poly" coords="300,100,350,150,300,200,250,150" href="africa.html" alt="Africa">
</map>
```

### Audio

```html
<!-- Basic Audio -->
<audio src="audio.mp3" controls>
    Your browser does not support the audio element.
</audio>

<!-- Multiple Sources -->
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    <source src="audio.wav" type="audio/wav">
    Your browser does not support the audio element.
</audio>
```

**Audio Attributes:**
- `controls` - Show play/pause/volume controls
- `autoplay` - Start playing automatically
- `muted` - Start muted
- `loop` - Loop playback
- `preload` - `"auto"` | `"metadata"` | `"none"`

### Video

```html
<!-- Basic Video -->
<video src="video.mp4" controls width="640" height="360">
    Your browser does not support the video element.
</video>

<!-- Multiple Sources with Poster -->
<video controls width="640" height="360" poster="thumbnail.jpg">
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    <source src="video.ogg" type="video/ogg">
    Your browser does not support the video element.
</video>

<!-- Video with Captions -->
<video controls width="640" height="360">
    <source src="video.mp4" type="video/mp4">
    <track src="captions-en.vtt" kind="captions" srclang="en" label="English" default>
    <track src="captions-ne.vtt" kind="captions" srclang="ne" label="Nepali">
</video>
```

**Video Attributes:**
- `controls` - Show video controls
- `autoplay` - Start playing automatically (often requires `muted`)
- `muted` - Start muted
- `loop` - Loop playback
- `poster` - Image shown before play
- `width` / `height` - Dimensions
- `preload` - `"auto"` | `"metadata"` | `"none"`
- `playsinline` - Play inline on mobile (not fullscreen)

### Embedded Content

```html
<!-- YouTube Video -->
<iframe width="560" height="315"
        src="https://www.youtube.com/embed/VIDEO_ID"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write;
               encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen>
</iframe>

<!-- Object Element (PDF) -->
<object data="document.pdf" type="application/pdf" width="600" height="400">
    <p>PDF cannot be displayed. <a href="document.pdf">Download</a></p>
</object>
```

---

## 2.7 Lists, Tables, Forms and Input

### Lists

**1. Unordered List (Bulleted):**

```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

CSS `list-style-type` values: `disc` (default), `circle`, `square`, `none`

**2. Ordered List (Numbered):**

```html
<ol>
    <li>First item</li>
    <li>Second item</li>
    <li>Third item</li>
</ol>
```

**Ordered List Attributes:**

```html
<ol type="1">  <!-- 1, 2, 3 (default) -->
<ol type="A">  <!-- A, B, C -->
<ol type="a">  <!-- a, b, c -->
<ol type="I">  <!-- I, II, III -->
<ol type="i">  <!-- i, ii, iii -->

<ol start="5">     <!-- Start from 5 -->
<ol reversed>      <!-- Reverse order -->
<li value="10">    <!-- Set specific value -->
```

**3. Description List (Definition):**

```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language - structure of web pages</dd>

    <dt>CSS</dt>
    <dd>Cascading Style Sheets - styling of web pages</dd>

    <dt>JavaScript</dt>
    <dd>Programming language for web interactivity</dd>
</dl>
```

**4. Nested Lists:**

```html
<ul>
    <li>Fruits
        <ul>
            <li>Apple</li>
            <li>Banana</li>
            <li>Orange</li>
        </ul>
    </li>
    <li>Vegetables
        <ul>
            <li>Carrot</li>
            <li>Broccoli</li>
        </ul>
    </li>
</ul>
```

### Tables

**Basic Table Structure:**

```html
<table>
    <thead>
        <tr>
            <th>Header 1</th>
            <th>Header 2</th>
            <th>Header 3</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Row 1, Cell 1</td>
            <td>Row 1, Cell 2</td>
            <td>Row 1, Cell 3</td>
        </tr>
        <tr>
            <td>Row 2, Cell 1</td>
            <td>Row 2, Cell 2</td>
            <td>Row 2, Cell 3</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Footer 1</td>
            <td>Footer 2</td>
            <td>Footer 3</td>
        </tr>
    </tfoot>
</table>
```

**Table Elements:**
- `<table>` - Container for the table
- `<thead>` - Table header section
- `<tbody>` - Table body section
- `<tfoot>` - Table footer section
- `<tr>` - Table row
- `<th>` - Table header cell (bold, centered by default)
- `<td>` - Table data cell
- `<caption>` - Table caption/title

**Table with Caption:**

```html
<table>
    <caption>Monthly Sales Report</caption>
    <thead>
        <tr>
            <th>Month</th>
            <th>Sales</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>January</td>
            <td>$10,000</td>
        </tr>
        <tr>
            <td>February</td>
            <td>$12,000</td>
        </tr>
    </tbody>
</table>
```

**Cell Spanning:**

```html
<!-- colspan (span multiple columns) -->
<table border="1">
    <tr>
        <th colspan="2">Name</th>
        <th>Age</th>
    </tr>
    <tr>
        <td>First</td>
        <td>Last</td>
        <td>25</td>
    </tr>
</table>

<!-- rowspan (span multiple rows) -->
<table border="1">
    <tr>
        <th>Name</th>
        <td rowspan="2">John</td>
    </tr>
    <tr>
        <th>Age</th>
    </tr>
</table>
```

**Complex Table Example:**

```html
<table border="1">
    <caption>Student Grades</caption>
    <thead>
        <tr>
            <th rowspan="2">Student</th>
            <th colspan="3">Subjects</th>
            <th rowspan="2">Total</th>
        </tr>
        <tr>
            <th>Math</th>
            <th>Science</th>
            <th>English</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>John</td>
            <td>85</td>
            <td>90</td>
            <td>88</td>
            <td>263</td>
        </tr>
        <tr>
            <td>Jane</td>
            <td>92</td>
            <td>88</td>
            <td>95</td>
            <td>275</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Average</td>
            <td>88.5</td>
            <td>89</td>
            <td>91.5</td>
            <td>269</td>
        </tr>
    </tfoot>
</table>
```

**Table Accessibility:**

```html
<table>
    <caption>Employee Directory</caption>
    <thead>
        <tr>
            <th scope="col">Name</th>
            <th scope="col">Department</th>
            <th scope="col">Email</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">John Doe</th>
            <td>Engineering</td>
            <td>john@example.com</td>
        </tr>
    </tbody>
</table>
```

`scope` attribute values: `col`, `row`, `colgroup`, `rowgroup`

### Forms

**Basic Form Structure:**

```html
<form action="/submit" method="post">
    <input type="text" name="username">
    <button type="submit">Submit</button>
</form>
```

**Form Attributes:**

```html
<form action="/submit"              <!-- Where to send data -->
      method="post"                 <!-- HTTP method: get or post -->
      enctype="multipart/form-data" <!-- For file uploads -->
      name="myForm"                 <!-- Form name -->
      target="_blank"               <!-- Where to show response -->
      autocomplete="on"             <!-- Enable autocomplete -->
      novalidate>                   <!-- Disable validation -->
```

**GET vs POST:**
- **GET**: Data in URL, visible, bookmarkable, limited size
- **POST**: Data in body, hidden, not bookmarkable, larger data

### Input Types

```html
<!-- Text -->
<input type="text" name="username" placeholder="Enter username">

<!-- Password -->
<input type="password" name="password" placeholder="Enter password">

<!-- Email -->
<input type="email" name="email" placeholder="email@example.com">

<!-- Number -->
<input type="number" name="age" min="0" max="120" step="1">

<!-- Tel (Phone) -->
<input type="tel" name="phone" placeholder="123-456-7890">

<!-- URL -->
<input type="url" name="website" placeholder="https://example.com">

<!-- Search -->
<input type="search" name="query" placeholder="Search...">

<!-- Date -->
<input type="date" name="birthday">

<!-- Time -->
<input type="time" name="appointment">

<!-- Datetime-local -->
<input type="datetime-local" name="meeting">

<!-- Month -->
<input type="month" name="expiry">

<!-- Week -->
<input type="week" name="week">

<!-- Color -->
<input type="color" name="favcolor" value="#ff0000">

<!-- Range (Slider) -->
<input type="range" name="volume" min="0" max="100" value="50">

<!-- File -->
<input type="file" name="document" accept=".pdf,.doc">
<input type="file" name="images" accept="image/*" multiple>

<!-- Hidden -->
<input type="hidden" name="userId" value="12345">

<!-- Checkbox -->
<input type="checkbox" name="agree" id="agree" value="yes">
<label for="agree">I agree to terms</label>

<!-- Radio Buttons -->
<input type="radio" name="gender" value="male" id="male">
<label for="male">Male</label>
<input type="radio" name="gender" value="female" id="female">
<label for="female">Female</label>

<!-- Submit, Reset, Button -->
<input type="submit" value="Submit Form">
<input type="reset" value="Clear Form">
<button type="button">Click Me</button>
<button type="submit">Submit</button>
<button type="reset">Reset</button>
```

### Input Attributes

```html
<input type="text"
       name="username"           <!-- Field name -->
       id="username"             <!-- Unique ID -->
       value="default"           <!-- Default value -->
       placeholder="Enter name"  <!-- Hint text -->
       required                  <!-- Must be filled -->
       disabled                  <!-- Cannot be edited -->
       readonly                  <!-- Can read, can't edit -->
       autofocus                 <!-- Focus on page load -->
       autocomplete="off"        <!-- Disable autocomplete -->
       minlength="3"             <!-- Minimum characters -->
       maxlength="50"            <!-- Maximum characters -->
       pattern="[A-Za-z]{3,}"    <!-- Regex pattern -->
       size="30"                 <!-- Visible width -->
       list="suggestions">       <!-- Datalist reference -->
```

### Other Form Elements

**1. Label:**

```html
<!-- Associated by 'for' attribute -->
<label for="email">Email:</label>
<input type="email" id="email" name="email">

<!-- Implicit association -->
<label>
    Email:
    <input type="email" name="email">
</label>
```

**2. Textarea:**

```html
<textarea name="message" rows="5" cols="40"
          placeholder="Enter your message..."
          maxlength="500"></textarea>
```

**3. Select (Dropdown):**

```html
<select name="country">
    <option value="">Select Country</option>
    <option value="np">Nepal</option>
    <option value="in">India</option>
    <option value="cn">China</option>
</select>

<!-- With optgroup -->
<select name="car">
    <optgroup label="Japanese">
        <option value="toyota">Toyota</option>
        <option value="honda">Honda</option>
    </optgroup>
    <optgroup label="German">
        <option value="bmw">BMW</option>
        <option value="mercedes">Mercedes</option>
    </optgroup>
</select>

<!-- Multiple selection -->
<select name="skills" multiple size="4">
    <option value="html">HTML</option>
    <option value="css">CSS</option>
    <option value="js">JavaScript</option>
    <option value="php">PHP</option>
</select>
```

**4. Datalist:**

```html
<input type="text" list="browsers" name="browser">
<datalist id="browsers">
    <option value="Chrome">
    <option value="Firefox">
    <option value="Safari">
    <option value="Edge">
</datalist>
```

**5. Fieldset and Legend:**

```html
<fieldset>
    <legend>Personal Information</legend>
    <label for="fname">First Name:</label>
    <input type="text" id="fname" name="fname"><br>
    <label for="lname">Last Name:</label>
    <input type="text" id="lname" name="lname">
</fieldset>
```

**6. Output:**

```html
<form oninput="result.value = parseInt(a.value) + parseInt(b.value)">
    <input type="number" id="a" value="0"> +
    <input type="number" id="b" value="0"> =
    <output name="result" for="a b">0</output>
</form>
```

**7. Progress:**

```html
<progress value="70" max="100">70%</progress>
```

**8. Meter:**

```html
<meter value="0.7" min="0" max="1" low="0.3" high="0.7" optimum="0.8">
    70%
</meter>
```

### Complete Form Example

```html
<form action="/register" method="post" enctype="multipart/form-data">
    <fieldset>
        <legend>Personal Information</legend>

        <div>
            <label for="fullname">Full Name: *</label>
            <input type="text" id="fullname" name="fullname"
                   required minlength="2" maxlength="100">
        </div>

        <div>
            <label for="email">Email: *</label>
            <input type="email" id="email" name="email" required>
        </div>

        <div>
            <label for="phone">Phone:</label>
            <input type="tel" id="phone" name="phone"
                   pattern="[0-9]{10}" placeholder="9800000000">
        </div>

        <div>
            <label for="dob">Date of Birth:</label>
            <input type="date" id="dob" name="dob">
        </div>

        <div>
            <label>Gender:</label>
            <input type="radio" id="male" name="gender" value="male">
            <label for="male">Male</label>
            <input type="radio" id="female" name="gender" value="female">
            <label for="female">Female</label>
        </div>
    </fieldset>

    <fieldset>
        <legend>Account Details</legend>

        <div>
            <label for="username">Username: *</label>
            <input type="text" id="username" name="username"
                   required pattern="[a-zA-Z0-9_]{4,20}">
        </div>

        <div>
            <label for="password">Password: *</label>
            <input type="password" id="password" name="password"
                   required minlength="8">
        </div>

        <div>
            <label for="country">Country:</label>
            <select id="country" name="country">
                <option value="">Select Country</option>
                <option value="np">Nepal</option>
                <option value="in">India</option>
                <option value="us">USA</option>
            </select>
        </div>
    </fieldset>

    <fieldset>
        <legend>Additional Information</legend>

        <div>
            <label for="bio">Bio:</label>
            <textarea id="bio" name="bio" rows="4" cols="50"
                      maxlength="500"></textarea>
        </div>

        <div>
            <label for="photo">Profile Photo:</label>
            <input type="file" id="photo" name="photo" accept="image/*">
        </div>

        <div>
            <input type="checkbox" id="newsletter" name="newsletter">
            <label for="newsletter">Subscribe to newsletter</label>
        </div>

        <div>
            <input type="checkbox" id="terms" name="terms" required>
            <label for="terms">I agree to the terms and conditions *</label>
        </div>
    </fieldset>

    <div>
        <button type="submit">Register</button>
        <button type="reset">Clear Form</button>
    </div>
</form>
```

---

## 2.8 Semantic HTML

### What is Semantic HTML?

Semantic HTML uses elements that clearly describe their meaning to both the browser and the developer, improving accessibility, SEO, and maintainability.

### Non-Semantic vs Semantic Elements

**Non-Semantic Elements (no meaning):**
- `<div>` - Generic container
- `<span>` - Generic inline container

**Semantic Elements (meaningful):**
- `<header>` - Introductory content
- `<nav>` - Navigation links
- `<main>` - Main content
- `<article>` - Self-contained content
- `<section>` - Thematic grouping
- `<aside>` - Sidebar content
- `<footer>` - Footer content
- `<figure>` - Self-contained media
- `<figcaption>` - Caption for figure

### Comparison

**Without Semantic HTML:**

```html
<div id="header">
    <div id="nav">
        <div class="nav-item">Home</div>
        <div class="nav-item">About</div>
    </div>
</div>
<div id="main">
    <div class="article">
        <div class="title">Article Title</div>
        <div class="content">Content here...</div>
    </div>
    <div id="sidebar">
        <div class="widget">Widget content</div>
    </div>
</div>
<div id="footer">
    <div class="copyright">&copy; 2024</div>
</div>
```

**With Semantic HTML:**

```html
<header>
    <nav>
        <a href="/">Home</a>
        <a href="/about">About</a>
    </nav>
</header>
<main>
    <article>
        <h1>Article Title</h1>
        <p>Content here...</p>
    </article>
    <aside>
        <section class="widget">Widget content</section>
    </aside>
</main>
<footer>
    <p>&copy; 2024</p>
</footer>
```

### Semantic Elements in Detail

**1. `<header>`** - Introductory content, typically contains logo, navigation, search.

```html
<header>
    <h1>Website Name</h1>
    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
        </ul>
    </nav>
</header>
```

**2. `<nav>`** - Contains navigation links.

```html
<nav aria-label="Main navigation">
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/products">Products</a></li>
        <li><a href="/contact">Contact</a></li>
    </ul>
</nav>
```

**3. `<main>`** - The main content of the document (only one per page).

```html
<main>
    <h1>Page Title</h1>
    <p>Main content goes here...</p>
</main>
```

**4. `<article>`** - Self-contained content that could be distributed independently.

```html
<article>
    <header>
        <h2>Blog Post Title</h2>
        <time datetime="2024-01-15">January 15, 2024</time>
    </header>
    <p>Blog post content...</p>
    <footer>
        <p>Tags: HTML, Web Development</p>
    </footer>
</article>
```

**5. `<section>`** - Thematic grouping of content with a heading.

```html
<section>
    <h2>About Us</h2>
    <p>Information about the company...</p>
</section>
```

**6. `<aside>`** - Content tangentially related to the main content (sidebar).

```html
<aside>
    <h3>Related Articles</h3>
    <ul>
        <li><a href="#">Article 1</a></li>
        <li><a href="#">Article 2</a></li>
    </ul>
</aside>
```

**7. `<footer>`** - Footer for document or section.

```html
<footer>
    <nav>
        <a href="/privacy">Privacy</a>
        <a href="/terms">Terms</a>
    </nav>
    <p>&copy; 2024 Company Name</p>
</footer>
```

**8. `<figure>` and `<figcaption>`** - Self-contained content with caption.

```html
<figure>
    <img src="chart.png" alt="Sales chart">
    <figcaption>Figure 1: 2024 Sales Data</figcaption>
</figure>
```

**9. `<time>`** - Machine-readable date/time.

```html
<p>Published on <time datetime="2024-01-15">January 15, 2024</time></p>
<p>Event starts at <time datetime="14:00">2:00 PM</time></p>
```

**10. `<details>` and `<summary>`** - Collapsible content.

```html
<details>
    <summary>Click to see more</summary>
    <p>Hidden content revealed when expanded.</p>
</details>
```

**11. `<address>`** - Contact information.

```html
<address>
    <p>Contact us:</p>
    <a href="mailto:info@example.com">info@example.com</a>
</address>
```

### Complete Semantic Page Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Semantic HTML Example</title>
</head>
<body>
    <header>
        <h1>Website Name</h1>
        <nav aria-label="Main">
            <ul>
                <li><a href="/">Home</a></li>
                <li><a href="/about">About</a></li>
                <li><a href="/blog">Blog</a></li>
                <li><a href="/contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <article>
            <header>
                <h2>Article Title</h2>
                <p>
                    By <address><a href="mailto:author@example.com">Author</a></address>
                    on <time datetime="2024-01-15">January 15, 2024</time>
                </p>
            </header>

            <section>
                <h3>Introduction</h3>
                <p>Introduction content with <strong>important</strong> text.</p>
            </section>

            <section>
                <h3>Main Points</h3>
                <p>Detailed content here...</p>

                <figure>
                    <img src="diagram.png" alt="Process diagram">
                    <figcaption>Figure 1: Process Flow</figcaption>
                </figure>
            </section>

            <footer>
                <p>Tags: <a href="/tag/html">HTML</a>, <a href="/tag/web">Web</a></p>
            </footer>
        </article>

        <aside>
            <section>
                <h3>Related Posts</h3>
                <ul>
                    <li><a href="#">Related Post 1</a></li>
                    <li><a href="#">Related Post 2</a></li>
                </ul>
            </section>
        </aside>
    </main>

    <footer>
        <nav aria-label="Footer">
            <ul>
                <li><a href="/privacy">Privacy Policy</a></li>
                <li><a href="/terms">Terms of Service</a></li>
            </ul>
        </nav>
        <p><small>&copy; 2024 Website Name. All rights reserved.</small></p>
    </footer>
</body>
</html>
```

### Benefits of Semantic HTML

1. **Accessibility**: Screen readers understand page structure, users can navigate by landmarks
2. **SEO (Search Engine Optimization)**: Search engines understand content better, improved ranking potential, rich snippets in search results
3. **Maintainability**: Code is self-documenting, easier for developers to understand, faster development and debugging
4. **Consistency**: Standard structure across websites, predictable behavior, better browser compatibility

---

## Summary

| Topic | Key Points |
|-------|-----------|
| Introduction to HTML | Elements, tags, attributes, HTML history |
| Document Structure | DOCTYPE, `<html>`, `<head>`, `<body>`, meta tags |
| Text Formatting | Headings (h1-h6), paragraphs, text elements, HTML entities |
| Links and Navigation | Anchor element, link types, navigation menus |
| Hyperlinks | URL structure, absolute vs relative URLs, path navigation |
| Images and Multimedia | Image element, formats, responsive images, audio, video |
| Lists, Tables, Forms | Ordered/unordered/description lists, table structure, form elements |
| Semantic HTML | Semantic elements, accessibility, SEO benefits |

---

## Study Questions

1. What is HTML and what is its role in web development?
2. Explain the basic structure of an HTML document with all its components.
3. What is the difference between `<strong>` and `<b>` tags?
4. How do you create different types of hyperlinks in HTML?
5. Explain the difference between absolute and relative URLs with examples.
6. What are the different image formats used in web development and when should each be used?
7. How do you create a table with merged cells using colspan and rowspan?
8. What is the difference between GET and POST methods in forms?
9. List and explain five different input types available in HTML.
10. What is semantic HTML and what are its benefits?
