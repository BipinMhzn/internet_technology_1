# Unit 3: HTML5

## 3.1 HTML5 APIs

HTML5 introduced several powerful APIs (Application Programming Interfaces) that enable rich web applications without plugins.

### Canvas API

The Canvas API provides a means for drawing graphics via JavaScript.

**Basic Canvas Setup:**

```html
<canvas id="myCanvas" width="500" height="300">
    Your browser does not support the canvas element.
</canvas>

<script>
    const canvas = document.getElementById('myCanvas');
    const ctx = canvas.getContext('2d');
</script>
```

### Drawing Basic Shapes

**1. Rectangles:**

```javascript
// Filled rectangle
ctx.fillStyle = 'blue';
ctx.fillRect(10, 10, 100, 50);  // x, y, width, height

// Stroked rectangle (outline)
ctx.strokeStyle = 'red';
ctx.lineWidth = 2;
ctx.strokeRect(120, 10, 100, 50);

// Clear rectangle (eraser)
ctx.clearRect(15, 15, 30, 20);
```

**2. Lines and Paths:**

```javascript
// Simple line
ctx.beginPath();
ctx.moveTo(50, 100);    // Starting point
ctx.lineTo(200, 100);   // End point
ctx.stroke();

// Closed path (triangle)
ctx.beginPath();
ctx.moveTo(300, 100);
ctx.lineTo(350, 180);
ctx.lineTo(250, 180);
ctx.closePath();
ctx.fillStyle = 'green';
ctx.fill();
ctx.stroke();
```

**3. Circles and Arcs:**

```javascript
// Full circle
ctx.beginPath();
ctx.arc(100, 250, 40, 0, Math.PI * 2);  // x, y, radius, startAngle, endAngle
ctx.fillStyle = 'purple';
ctx.fill();

// Semi-circle
ctx.beginPath();
ctx.arc(200, 250, 40, 0, Math.PI);
ctx.stroke();
```

**4. Text:**

```javascript
ctx.font = '30px Arial';
ctx.fillStyle = 'black';
ctx.fillText('Hello Canvas!', 50, 50);  // text, x, y

ctx.strokeStyle = 'blue';
ctx.strokeText('Outlined Text', 50, 100);

// Text alignment
ctx.textAlign = 'center';  // start, end, left, right, center
ctx.textBaseline = 'middle';  // top, hanging, middle, alphabetic, bottom
```

**5. Gradients:**

```javascript
// Linear gradient
const linearGradient = ctx.createLinearGradient(0, 0, 200, 0);
linearGradient.addColorStop(0, 'red');
linearGradient.addColorStop(0.5, 'yellow');
linearGradient.addColorStop(1, 'green');
ctx.fillStyle = linearGradient;
ctx.fillRect(10, 10, 200, 100);

// Radial gradient
const radialGradient = ctx.createRadialGradient(100, 200, 10, 100, 200, 50);
radialGradient.addColorStop(0, 'white');
radialGradient.addColorStop(1, 'blue');
ctx.fillStyle = radialGradient;
ctx.beginPath();
ctx.arc(100, 200, 50, 0, Math.PI * 2);
ctx.fill();
```

**6. Images on Canvas:**

```javascript
const img = new Image();
img.onload = function() {
    ctx.drawImage(img, 10, 10);              // x, y
    ctx.drawImage(img, 10, 10, 100, 100);    // x, y, width, height
    ctx.drawImage(img, 0, 0, 50, 50, 10, 10, 100, 100);  // crop and draw
};
img.src = 'image.jpg';
```

**7. Transformations:**

```javascript
ctx.translate(100, 100);    // Move origin
ctx.rotate(Math.PI / 4);    // Rotate 45 degrees
ctx.scale(2, 2);            // Double size

// Save and restore state
ctx.save();
ctx.translate(50, 50);
ctx.fillRect(0, 0, 50, 50);
ctx.restore();  // Back to original state
```

**Canvas Animation Example:**

```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

let x = 0;

function animate() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    ctx.beginPath();
    ctx.arc(x, 100, 20, 0, Math.PI * 2);
    ctx.fillStyle = 'blue';
    ctx.fill();

    x += 2;
    if (x > canvas.width) x = 0;

    requestAnimationFrame(animate);
}

animate();
```

### Geolocation API

Allows websites to access the user's geographical location.

```javascript
if ('geolocation' in navigator) {
    navigator.geolocation.getCurrentPosition(
        // Success callback
        function(position) {
            console.log('Latitude:', position.coords.latitude);
            console.log('Longitude:', position.coords.longitude);
            console.log('Accuracy:', position.coords.accuracy, 'meters');
        },
        // Error callback
        function(error) {
            switch(error.code) {
                case error.PERMISSION_DENIED:
                    console.log('User denied the request.');
                    break;
                case error.POSITION_UNAVAILABLE:
                    console.log('Location information unavailable.');
                    break;
                case error.TIMEOUT:
                    console.log('Request timed out.');
                    break;
            }
        },
        // Options
        {
            enableHighAccuracy: true,
            timeout: 5000,
            maximumAge: 0
        }
    );

    // Watch position (continuous tracking)
    const watchId = navigator.geolocation.watchPosition(successCallback);

    // Stop watching
    navigator.geolocation.clearWatch(watchId);
}
```

### Web Storage API

Provides mechanisms for storing data in the browser.

**1. localStorage (persistent - data persists even after browser is closed):**

```javascript
// Store data
localStorage.setItem('username', 'John');
localStorage.setItem('user', JSON.stringify({name: 'John', age: 30}));

// Retrieve data
const username = localStorage.getItem('username');
const user = JSON.parse(localStorage.getItem('user'));

// Remove data
localStorage.removeItem('username');

// Clear all data
localStorage.clear();

// Check storage length
console.log(localStorage.length);

// Get key by index
const key = localStorage.key(0);
```

**2. sessionStorage (cleared when tab closes):**

```javascript
sessionStorage.setItem('sessionData', 'value');
sessionStorage.getItem('sessionData');
sessionStorage.removeItem('sessionData');
sessionStorage.clear();
```

**Storage Capacity:**
- Typically 5-10 MB per origin
- Synchronous API (can block main thread)

### Drag and Drop API

Enables drag-and-drop functionality.

```html
<div id="dragItem" draggable="true">Drag me!</div>
<div id="dropZone">Drop here</div>
```

```javascript
const dragItem = document.getElementById('dragItem');
const dropZone = document.getElementById('dropZone');

// Drag events on draggable element
dragItem.addEventListener('dragstart', function(e) {
    e.dataTransfer.setData('text/plain', e.target.id);
    e.target.style.opacity = '0.5';
});

dragItem.addEventListener('dragend', function(e) {
    e.target.style.opacity = '1';
});

// Drop events on drop zone
dropZone.addEventListener('dragover', function(e) {
    e.preventDefault();  // Required to allow drop
    e.target.style.background = '#e0e0e0';
});

dropZone.addEventListener('dragleave', function(e) {
    e.target.style.background = '';
});

dropZone.addEventListener('drop', function(e) {
    e.preventDefault();
    const id = e.dataTransfer.getData('text/plain');
    const draggedElement = document.getElementById(id);
    e.target.appendChild(draggedElement);
    e.target.style.background = '';
});
```

### Web Workers API

Run scripts in background threads without blocking the main thread.

**Main Script (main.js):**

```javascript
const worker = new Worker('worker.js');

worker.postMessage({data: [1, 2, 3, 4, 5]});

worker.onmessage = function(e) {
    console.log('Result from worker:', e.data);
};

worker.onerror = function(e) {
    console.error('Worker error:', e.message);
};

worker.terminate();
```

**Worker Script (worker.js):**

```javascript
self.onmessage = function(e) {
    const data = e.data.data;
    const sum = data.reduce((a, b) => a + b, 0);
    self.postMessage(sum);
};
```

### History API

Manipulate browser history without page reload.

```javascript
history.back();      // Go back
history.forward();   // Go forward
history.go(-2);      // Go back 2 pages

// Push new state (no page reload)
history.pushState({page: 1}, 'Page 1', '/page1');

// Replace current state
history.replaceState({page: 2}, 'Page 2', '/page2');

// Listen for popstate (back/forward)
window.addEventListener('popstate', function(e) {
    console.log('State:', e.state);
});
```

---

## 3.2 HTML5 Forms

HTML5 introduced new input types, attributes, and validation features.

### New Input Types

```html
<!-- 1. email - Auto-validates email format -->
<input type="email" name="email" placeholder="Enter email">

<!-- 2. url - Auto-validates URL format -->
<input type="url" name="website" placeholder="https://example.com">

<!-- 3. tel - Shows telephone keypad on mobile -->
<input type="tel" name="phone" placeholder="123-456-7890">

<!-- 4. number - Shows number spinner -->
<input type="number" name="quantity" min="1" max="100" step="1" value="1">

<!-- 5. range - Shows slider control -->
<input type="range" name="volume" min="0" max="100" value="50">

<!-- 6. date - Shows date picker -->
<input type="date" name="birthday" min="1900-01-01" max="2024-12-31">

<!-- 7. time - Shows time picker -->
<input type="time" name="appointment">

<!-- 8. datetime-local - Shows date and time picker -->
<input type="datetime-local" name="meeting">

<!-- 9. month - Shows month/year picker -->
<input type="month" name="expiry">

<!-- 10. week - Shows week picker -->
<input type="week" name="week">

<!-- 11. color - Shows color picker -->
<input type="color" name="favcolor" value="#ff0000">

<!-- 12. search - Search-styled input with clear button -->
<input type="search" name="query" placeholder="Search...">
```

### New Form Attributes

| Attribute | Description | Example |
|-----------|-------------|---------|
| `placeholder` | Hint text that disappears on focus | `placeholder="Enter name"` |
| `required` | Field must be filled before submission | `required` |
| `autofocus` | Automatically focuses on page load | `autofocus` |
| `autocomplete` | Browser auto-completion behavior | `autocomplete="email"` |
| `pattern` | Regular expression validation | `pattern="[A-Za-z]{3}"` |
| `min` / `max` | Minimum/maximum value | `min="0" max="100"` |
| `step` | Value increment | `step="5"` |
| `multiple` | Allow multiple values | `multiple` |
| `list` | Connect to datalist | `list="browsers"` |
| `form` | Link input to form by ID | `form="myForm"` |
| `formaction` | Override form action | `formaction="/other"` |

```html
<!-- Datalist example -->
<input type="text" list="browsers">
<datalist id="browsers">
    <option value="Chrome">
    <option value="Firefox">
    <option value="Safari">
    <option value="Edge">
</datalist>

<!-- Form attribute - link input outside form -->
<form id="myForm">
    <input type="text" name="inside">
</form>
<input type="text" name="outside" form="myForm">
```

### Form Validation

**Built-in Validation:**

```html
<!-- 1. Required validation -->
<input type="text" required>

<!-- 2. Type validation -->
<input type="email">  <!-- Validates email format -->
<input type="url">    <!-- Validates URL format -->

<!-- 3. Pattern validation -->
<input type="tel" pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}"
       title="Format: 123-456-7890">

<input type="text" pattern="[a-zA-Z0-9]{4,12}"
       title="4-12 alphanumeric characters">

<!-- 4. Length validation -->
<input type="text" minlength="3" maxlength="20">

<!-- 5. Range validation -->
<input type="number" min="1" max="100">
```

**Validation CSS Pseudo-classes:**

```css
input:valid { border-color: green; }
input:invalid { border-color: red; }
input:required { border-left: 3px solid red; }
input:optional { border-left: 3px solid gray; }
input:in-range { background-color: #dff0d8; }
input:out-of-range { background-color: #f2dede; }
```

**Custom Validation Messages:**

```html
<input type="email" id="email" required
       oninvalid="this.setCustomValidity('Please enter a valid email address')"
       oninput="this.setCustomValidity('')">
```

**JavaScript Validation API:**

```javascript
const form = document.getElementById('myForm');
const email = document.getElementById('email');

form.addEventListener('submit', function(e) {
    if (!email.validity.valid) {
        e.preventDefault();

        if (email.validity.valueMissing) {
            email.setCustomValidity('Email is required');
        } else if (email.validity.typeMismatch) {
            email.setCustomValidity('Please enter a valid email');
        }
    }
});
```

**Validity Properties:**

| Property | Description |
|----------|-------------|
| `validity.valid` | Overall validity |
| `validity.valueMissing` | Required but empty |
| `validity.typeMismatch` | Wrong type (email, url) |
| `validity.patternMismatch` | Pattern not matched |
| `validity.tooLong` | Exceeds maxlength |
| `validity.tooShort` | Below minlength |
| `validity.rangeUnderflow` | Below min |
| `validity.rangeOverflow` | Above max |
| `validity.stepMismatch` | Doesn't match step |

```javascript
email.checkValidity();    // Returns true/false
email.reportValidity();   // Shows validation message
```

**Disable validation:**

```html
<form novalidate>
<input formnovalidate type="submit">
```

### New Form Elements

**1. `<datalist>` - Predefined options:**

```html
<input type="text" list="countries" name="country">
<datalist id="countries">
    <option value="Nepal">
    <option value="India">
    <option value="China">
    <option value="USA">
</datalist>
```

**2. `<output>` - Calculation result:**

```html
<form oninput="result.value = parseInt(a.value) + parseInt(b.value)">
    <input type="number" id="a" value="0"> +
    <input type="number" id="b" value="0"> =
    <output name="result" for="a b">0</output>
</form>
```

**3. `<progress>` - Progress bar:**

```html
<progress value="70" max="100">70%</progress>

<!-- Indeterminate progress -->
<progress></progress>
```

**4. `<meter>` - Measurement gauge:**

```html
<meter value="0.6" min="0" max="1" low="0.3" high="0.7" optimum="0.8">
    60%
</meter>
```

---

## 3.3 Responsive Web Design

Responsive Web Design (RWD) makes web pages look good on all devices (desktops, tablets, and phones).

### Viewport Meta Tag

Essential for responsive design on mobile devices.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**Viewport Properties:**

| Property | Description |
|----------|-------------|
| `width=device-width` | Match screen width |
| `initial-scale=1.0` | Initial zoom level (1 = no zoom) |
| `maximum-scale=1.0` | Maximum zoom allowed |
| `minimum-scale=1.0` | Minimum zoom allowed |
| `user-scalable=no` | Disable user zoom (not recommended) |

### Responsive Images

**1. Fluid Images:**

```css
img {
    max-width: 100%;
    height: auto;
}
```

**2. srcset attribute (resolution switching):**

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

**3. `<picture>` element (art direction):**

```html
<picture>
    <source media="(min-width: 1200px)" srcset="large.jpg">
    <source media="(min-width: 768px)" srcset="medium.jpg">
    <source media="(min-width: 480px)" srcset="small.jpg">
    <img src="default.jpg" alt="Responsive image">
</picture>
```

### Responsive Typography

```css
/* Relative units */
html { font-size: 16px; }
body { font-size: 1rem; }
h1 { font-size: 2.5rem; }

@media (max-width: 768px) {
    html { font-size: 14px; }
}

/* Viewport units */
h1 { font-size: 5vw; }

/* clamp() function - min, preferred, max */
h1 { font-size: clamp(1.5rem, 4vw, 3rem); }
```

### Responsive Layout Techniques

**1. Percentage Widths:**

```css
.container {
    width: 90%;
    max-width: 1200px;
    margin: 0 auto;
}
```

**2. Flexbox:**

```css
.container {
    display: flex;
    flex-wrap: wrap;
}

.item {
    flex: 1 1 300px;  /* grow shrink basis */
}
```

**3. CSS Grid:**

```css
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
}
```

### Media Queries in HTML5

```css
/* Mobile first approach */
.container {
    width: 100%;
    padding: 10px;
}

/* Tablet and up */
@media (min-width: 768px) {
    .container {
        width: 750px;
        margin: 0 auto;
    }
}

/* Desktop and up */
@media (min-width: 992px) {
    .container { width: 970px; }
}

/* Large desktop */
@media (min-width: 1200px) {
    .container { width: 1170px; }
}
```

**Common Breakpoints:**
- Mobile: < 576px
- Small: >= 576px
- Medium: >= 768px
- Large: >= 992px
- Extra Large: >= 1200px

**Responsive Video:**

```html
<div class="video-container">
    <iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen></iframe>
</div>
```

```css
.video-container {
    position: relative;
    padding-bottom: 56.25%;  /* 16:9 aspect ratio */
    height: 0;
    overflow: hidden;
}

.video-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
```

**Responsive Tables:**

```html
<div class="table-responsive">
    <table>...</table>
</div>
```

```css
.table-responsive {
    overflow-x: auto;
}
```

---

## 3.4 HTML5 (New Elements and Features)

HTML5 introduced many new elements for better structure and functionality.

### New Structural Elements

| Element | Purpose |
|---------|---------|
| `<header>` | Introductory content or navigation |
| `<nav>` | Navigation links |
| `<main>` | Main content (one per page) |
| `<article>` | Self-contained content |
| `<section>` | Thematic grouping |
| `<aside>` | Sidebar/related content |
| `<footer>` | Footer content |
| `<figure>` / `<figcaption>` | Self-contained content with caption |
| `<details>` / `<summary>` | Collapsible content |
| `<mark>` | Highlighted text |
| `<time>` | Machine-readable date/time |
| `<address>` | Contact information |

```html
<!-- Details and Summary -->
<details>
    <summary>Click to expand</summary>
    <p>Hidden content that appears when expanded.</p>
</details>

<details open>
    <summary>Already expanded</summary>
    <p>This content is visible by default.</p>
</details>

<!-- Mark -->
<p>Search results for <mark>HTML5</mark> found.</p>

<!-- Time -->
<time datetime="2024-01-15">January 15, 2024</time>
<time datetime="2024-01-15T14:30:00">2:30 PM on January 15</time>
<time datetime="PT2H30M">2 hours 30 minutes</time>
```

### Multimedia Elements

**`<audio>`:**

```html
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    Your browser does not support the audio element.
</audio>
```

Attributes: `controls`, `autoplay`, `muted`, `loop`, `preload` (auto | metadata | none)

**`<video>`:**

```html
<video controls width="640" height="360" poster="thumbnail.jpg">
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    <track src="captions.vtt" kind="subtitles" srclang="en" label="English">
    Your browser does not support the video element.
</video>
```

Attributes: `controls`, `autoplay`, `muted`, `loop`, `poster`, `width`/`height`, `preload`, `playsinline`

**`<track>`** - Text tracks for video:

```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <track src="subtitles_en.vtt" kind="subtitles" srclang="en" label="English" default>
    <track src="subtitles_np.vtt" kind="subtitles" srclang="ne" label="Nepali">
</video>
```

Track kinds: `subtitles`, `captions`, `descriptions`, `chapters`, `metadata`

### Embedded Content

```html
<!-- iframe with sandbox -->
<iframe src="https://example.com"
        width="600" height="400"
        frameborder="0"
        allowfullscreen
        sandbox="allow-scripts allow-same-origin">
</iframe>
```

Sandbox values: `allow-forms`, `allow-scripts`, `allow-same-origin`, `allow-popups`

### Other New Elements

```html
<!-- Word break opportunity -->
<p>This is a verylongwordthatmight<wbr>needtobreak</p>

<!-- Bi-directional isolation -->
<p>User <bdi>إيان</bdi> posted: Hello</p>

<!-- Ruby annotations (East Asian typography) -->
<ruby>
    漢 <rp>(</rp><rt>かん</rt><rp>)</rp>
    字 <rp>(</rp><rt>じ</rt><rp>)</rp>
</ruby>
```

### New Global Attributes

**1. `contenteditable`:**

```html
<div contenteditable="true">
    Click to edit this text...
</div>
```

**2. `data-*` (custom data attributes):**

```html
<div data-user-id="123" data-role="admin">User info</div>

<script>
    const div = document.querySelector('div');
    console.log(div.dataset.userId);  // "123"
    console.log(div.dataset.role);    // "admin"
</script>
```

**3. `hidden`:**

```html
<p hidden>This paragraph is hidden.</p>
```

**4. `draggable`:**

```html
<div draggable="true">Drag me</div>
```

**5. `spellcheck`:**

```html
<textarea spellcheck="true">Check my spelling</textarea>
```

**6. `translate`:**

```html
<p translate="no">Brand Name</p>  <!-- Don't translate -->
```

---

## 3.5 Semantic Markup

Semantic HTML uses elements that clearly describe their meaning to both the browser and the developer.

### Why Semantic HTML?

1. **Accessibility**: Screen readers understand content structure
2. **SEO**: Search engines better understand page content
3. **Maintainability**: Code is easier to read and maintain
4. **Consistency**: Standard structure across websites

### Non-Semantic vs Semantic

**Non-Semantic (Generic):**

```html
<div id="header">
    <div id="nav"><div class="nav-item">Home</div></div>
</div>
<div id="main">
    <div class="post">
        <div class="post-title">Title</div>
        <div class="post-content">Content</div>
    </div>
</div>
<div id="footer">Footer</div>
```

**Semantic (Meaningful):**

```html
<header>
    <nav><a href="/">Home</a></nav>
</header>
<main>
    <article>
        <h1>Title</h1>
        <p>Content</p>
    </article>
</main>
<footer>Footer</footer>
```

### Semantic Elements Reference

**Structural Elements:**

| Element | Purpose |
|---------|---------|
| `<header>` | Introductory content, navigation |
| `<nav>` | Navigation links |
| `<main>` | Main content (one per page) |
| `<article>` | Self-contained content |
| `<section>` | Thematic grouping |
| `<aside>` | Sidebar, related content |
| `<footer>` | Footer content |

**Text Semantics:**

| Element | Purpose |
|---------|---------|
| `<h1>`-`<h6>` | Headings (hierarchical) |
| `<p>` | Paragraph |
| `<blockquote>` | Block quotation |
| `<q>` | Inline quotation |
| `<cite>` | Citation/reference |
| `<abbr>` | Abbreviation |
| `<code>` | Code snippet |
| `<pre>` | Preformatted text |
| `<strong>` | Strong importance |
| `<em>` | Emphasis |
| `<mark>` | Highlighted text |
| `<del>` | Deleted text |
| `<ins>` | Inserted text |

**Interactive Elements:**

| Element | Purpose |
|---------|---------|
| `<details>` | Collapsible content |
| `<summary>` | Summary for `<details>` |
| `<dialog>` | Dialog box |

### Proper Heading Structure

```html
<body>
    <header>
        <h1>Website Name</h1>  <!-- Only one h1 per page -->
    </header>
    <main>
        <article>
            <h2>Article Title</h2>
            <section>
                <h3>Section 1</h3>
                <h4>Subsection 1.1</h4>
            </section>
            <section>
                <h3>Section 2</h3>
            </section>
        </article>
    </main>
    <aside>
        <h2>Related Links</h2>
    </aside>
</body>
```

**Heading Rules:**
- Use only one `<h1>` per page (main title)
- Don't skip heading levels (h1 -> h3)
- Use headings for structure, not styling
- Keep heading hierarchy logical

### ARIA Roles and Attributes

ARIA (Accessible Rich Internet Applications) enhances accessibility.

```html
<!-- Landmark roles (redundant with semantic elements but useful for older browsers) -->
<header role="banner">...</header>
<nav role="navigation">...</nav>
<main role="main">...</main>
<aside role="complementary">...</aside>
<footer role="contentinfo">...</footer>

<!-- ARIA labels -->
<button aria-label="Close menu">X</button>
<nav aria-label="Main navigation">...</nav>
<div role="alert" aria-live="polite">Message</div>

<!-- ARIA states -->
<button aria-expanded="false">Toggle</button>
<input aria-invalid="true">
<div aria-hidden="true">Hidden from screen readers</div>
```

### Complete Semantic Page Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Semantic HTML5 Page</title>
</head>
<body>
    <header>
        <h1>Company Name</h1>
        <nav aria-label="Main navigation">
            <ul>
                <li><a href="/">Home</a></li>
                <li><a href="/about">About</a></li>
                <li><a href="/services">Services</a></li>
                <li><a href="/contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <article>
            <header>
                <h2>Article Title</h2>
                <p>
                    By <address><a href="mailto:author@example.com">Author Name</a></address>
                    on <time datetime="2024-01-15">January 15, 2024</time>
                </p>
            </header>

            <section>
                <h3>Introduction</h3>
                <p>This is the introduction with <strong>important</strong> and
                   <em>emphasized</em> text.</p>
            </section>

            <section>
                <h3>Main Content</h3>
                <p>Main content with a <abbr title="HyperText Markup Language">HTML</abbr>
                   abbreviation.</p>

                <figure>
                    <img src="diagram.png" alt="Process diagram">
                    <figcaption>Figure 1: Process flow diagram</figcaption>
                </figure>

                <blockquote cite="https://example.com/quote">
                    <p>This is a quotation from an external source.</p>
                    <footer>— <cite>Source Name</cite></footer>
                </blockquote>
            </section>

            <footer>
                <p>Tags: <a href="/tag/html5">HTML5</a>, <a href="/tag/semantic">Semantic</a></p>
            </footer>
        </article>

        <aside>
            <h2>Related Articles</h2>
            <ul>
                <li><a href="/article-1">Related Article 1</a></li>
                <li><a href="/article-2">Related Article 2</a></li>
            </ul>

            <details>
                <summary>More Information</summary>
                <p>Additional details that can be expanded.</p>
            </details>
        </aside>
    </main>

    <footer>
        <nav aria-label="Footer navigation">
            <ul>
                <li><a href="/privacy">Privacy Policy</a></li>
                <li><a href="/terms">Terms of Service</a></li>
            </ul>
        </nav>
        <p><small>&copy; 2024 Company Name. All rights reserved.</small></p>
    </footer>
</body>
</html>
```

---

## 3.6 Best Practices and Optimization

### Code Indentation and Formatting

**1. Consistent Indentation:**

```html
<!-- Use 2 or 4 spaces consistently -->
<div class="container">
    <header>
        <h1>Title</h1>
        <nav>
            <ul>
                <li><a href="/">Home</a></li>
                <li><a href="/about">About</a></li>
            </ul>
        </nav>
    </header>
</div>
```

**2. Element Formatting:**

```html
<!-- Short elements - single line -->
<p>Short paragraph.</p>

<!-- Long elements - multiple lines -->
<p>
    This is a longer paragraph that contains more text
    and benefits from being on multiple lines.
</p>

<!-- Many attributes - multiple lines -->
<input
    type="text"
    id="username"
    name="username"
    class="form-input"
    placeholder="Enter username"
    required
    minlength="4"
    maxlength="20">
```

**3. Proper Nesting:**

```html
<!-- Correct -->
<p>This is <strong>bold and <em>italic</em></strong> text.</p>

<!-- Incorrect - AVOID -->
<p>This is <strong>bold and <em>italic</strong> text.</em></p>
```

### Naming Conventions

**1. File Names:**
- Use lowercase
- Use hyphens for spaces
- Be descriptive: `index.html`, `about-us.html`, `contact-form.html`

**2. ID and Class Names:**

```html
<!-- Good - descriptive, kebab-case -->
<div id="main-navigation" class="nav-container">
<button class="btn btn-primary submit-button">

<!-- Avoid - meaningless names -->
<div id="div1" class="x">
```

**3. BEM Naming Convention:** `Block__Element--Modifier`

```html
<div class="card">
    <img class="card__image" src="...">
    <h3 class="card__title">Title</h3>
    <p class="card__description">Description</p>
    <button class="card__button card__button--primary">Click</button>
</div>
```

### HTML Validation

- Always include DOCTYPE
- Close all tags properly
- Use proper nesting
- Include required attributes (e.g., `alt` on images)
- Avoid duplicate IDs
- Validate with W3C Validator: https://validator.w3.org/

### Accessibility Best Practices

**1. Image Alt Text:**

```html
<!-- Descriptive alt text -->
<img src="chart.png" alt="Sales growth chart showing 25% increase in Q4">

<!-- Decorative images -->
<img src="decoration.png" alt="" role="presentation">
```

**2. Form Labels:**

```html
<label for="email">Email:</label>
<input type="email" id="email" name="email">
```

**3. Skip Navigation:**

```html
<a href="#main-content" class="skip-link">Skip to main content</a>
<main id="main-content">
```

**4. Language Attribute:**

```html
<html lang="en">
<p lang="ne">नेपाली टेक्स्ट</p>
```

**5. Focus Management:**

```css
:focus {
    outline: 2px solid #007bff;
    outline-offset: 2px;
}
```

### SEO Best Practices

```html
<!-- 1. Proper Title (under 60 characters) -->
<title>Page Title | Website Name</title>

<!-- 2. Meta Description (under 160 characters) -->
<meta name="description" content="A brief description of the page content.">

<!-- 3. Heading Hierarchy -->
<h1>Main Title (one per page)</h1>
<h2>Section Heading</h2>
<h3>Subsection Heading</h3>

<!-- 4. Descriptive Links -->
<a href="/products">View our products</a>  <!-- Good -->
<a href="/products">Click here</a>         <!-- Avoid -->
```

### Performance Optimization

**1. Optimize Loading Order:**

```html
<head>
    <!-- CSS in head -->
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- content -->
    <!-- JavaScript at end of body or with defer -->
    <script src="script.js" defer></script>
</body>
```

**2. Lazy Loading:**

```html
<img src="image.jpg" loading="lazy" alt="Description">
<iframe src="video.html" loading="lazy"></iframe>
```

**3. Preload Critical Resources:**

```html
<link rel="preload" href="critical.css" as="style">
<link rel="preload" href="hero.jpg" as="image">
<link rel="preload" href="font.woff2" as="font" crossorigin>
```

**4. Prefetch Future Resources:**

```html
<link rel="prefetch" href="next-page.html">
<link rel="dns-prefetch" href="//api.example.com">
```

**5. Image Optimization:**

```html
<!-- Use modern formats with fallback -->
<picture>
    <source type="image/webp" srcset="image.webp">
    <source type="image/jpeg" srcset="image.jpg">
    <img src="image.jpg" alt="Description">
</picture>

<!-- Specify dimensions to prevent layout shift -->
<img src="image.jpg" width="800" height="600" alt="Description">
```

### Optimized Document Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- SEO -->
    <meta name="description" content="Page description">
    <meta name="author" content="Author Name">

    <!-- Open Graph -->
    <meta property="og:title" content="Page Title">
    <meta property="og:description" content="Page description">
    <meta property="og:image" content="https://example.com/image.jpg">

    <!-- Favicon -->
    <link rel="icon" href="/favicon.ico">

    <!-- Preconnect -->
    <link rel="preconnect" href="https://fonts.googleapis.com">

    <!-- CSS -->
    <link rel="stylesheet" href="styles.css">

    <title>Page Title | Website Name</title>
</head>
<body>
    <header>
        <nav><!-- Navigation --></nav>
    </header>

    <main>
        <article><!-- Main content --></article>
        <aside><!-- Sidebar --></aside>
    </main>

    <footer><!-- Footer content --></footer>

    <script src="script.js" defer></script>
</body>
</html>
```

---

## Summary

| Topic | Key Points |
|-------|-----------|
| HTML5 APIs | Canvas, Geolocation, Web Storage, Drag & Drop, Web Workers, History |
| HTML5 Forms | New input types (email, date, color, range), validation attributes, datalist |
| Responsive Web Design | Viewport meta tag, responsive images, media queries, mobile-first |
| HTML5 Elements | Structural elements, multimedia (audio/video), interactive elements |
| Semantic Markup | Meaningful elements, ARIA roles, proper heading structure |
| Best Practices | Code formatting, naming conventions, accessibility, SEO, performance |

---

## Study Questions

1. What is the Canvas API and how do you draw basic shapes with it?
2. Explain the difference between localStorage and sessionStorage.
3. List five new HTML5 input types and their purposes.
4. What is form validation in HTML5? Explain built-in validation attributes.
5. What is responsive web design? Why is the viewport meta tag important?
6. Explain the `srcset` attribute and the `<picture>` element for responsive images.
7. What are HTML5 semantic elements? List five with their purposes.
8. How do ARIA roles and attributes improve accessibility?
9. What are the key HTML5 best practices for performance optimization?
10. Explain the BEM naming convention with an example.
