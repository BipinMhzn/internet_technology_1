# CSS Flexbox Examples - Unit 5

This folder contains comprehensive CSS Flexbox examples for teaching Internet Technology course at Pokhara University.

## Examples Overview

### Basic Concepts (Examples 1-4)
1. **01_basic_flexbox.html** - Introduction to Flexbox
   - `display: flex`
   - Flex container vs flex items
   - Comparison with normal block layout

2. **02_flex_direction.html** - Flex Direction
   - `flex-direction: row` (default)
   - `flex-direction: row-reverse`
   - `flex-direction: column`
   - `flex-direction: column-reverse`

3. **03_justify_content.html** - Main Axis Alignment
   - `justify-content: flex-start`
   - `justify-content: flex-end`
   - `justify-content: center`
   - `justify-content: space-between`
   - `justify-content: space-around`
   - `justify-content: space-evenly`

4. **04_align_items.html** - Cross Axis Alignment
   - `align-items: flex-start`
   - `align-items: flex-end`
   - `align-items: center`
   - `align-items: baseline`
   - `align-items: stretch`
   - Perfect centering technique

### Advanced Concepts (Examples 5-7)
5. **05_flex_wrap.html** - Wrapping Behavior
   - `flex-wrap: nowrap`
   - `flex-wrap: wrap`
   - `flex-wrap: wrap-reverse`
   - `align-content` property

6. **06_flex_properties.html** - Flex Item Properties
   - `flex-grow` - How items grow
   - `flex-shrink` - How items shrink
   - `flex-basis` - Initial size
   - `flex` shorthand (most common)

7. **07_align_self.html** - Individual Item Control
   - `align-self` property
   - `order` property
   - Responsive reordering

### Practical Applications (Examples 8-10)
8. **08_navigation_bar.html** - Responsive Navigation
   - Real-world navbar example
   - Desktop and mobile layouts
   - Space distribution techniques

9. **09_card_layout.html** - Flexible Cards
   - Nested flexbox
   - Responsive card grid
   - Equal height cards
   - Footer alignment

10. **10_holy_grail_layout.html** - Classic Layout
    - Three-column layout
    - Sticky footer
    - Fixed sidebars, fluid content
    - Complete page structure

## Syllabus Coverage

These examples align with **Unit 5: Advanced Topics on CSS**, specifically section **5.1 CSS Flexbox**.

## Key Learning Outcomes

Students will learn to:
- Create flexible, responsive layouts
- Understand main axis vs cross axis
- Master alignment and spacing
- Use flex properties for proportional sizing
- Build real-world components (navbars, cards, layouts)
- Implement responsive designs without media queries (when possible)

## Flexbox vs Grid - When to Use What?

### Use Flexbox for:
- One-dimensional layouts (rows OR columns)
- Navigation bars
- Card layouts where cards wrap
- Centering content
- Distributing space between items
- Component layouts

### Use Grid for:
- Two-dimensional layouts (rows AND columns)
- Page layouts
- Complex grid systems
- Gallery layouts
- Dashboard layouts

## Teaching Tips

1. **Start Simple**: Begin with basic flex containers (Example 1)
2. **Visual Learning**: Use browser DevTools to toggle properties
3. **Main vs Cross**: Emphasize the axis concept early
4. **Common Patterns**: Show navbar and card examples (Examples 8-9)
5. **Hands-on**: Have students modify examples and predict results

## Quick Reference

### Container Properties
```css
display: flex;
flex-direction: row | row-reverse | column | column-reverse;
flex-wrap: nowrap | wrap | wrap-reverse;
justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;
align-items: stretch | flex-start | flex-end | center | baseline;
align-content: flex-start | flex-end | center | space-between | space-around | stretch;
gap: 10px;  /* Spacing between items */
```

### Item Properties
```css
flex-grow: 0;      /* Default: 0 (don't grow) */
flex-shrink: 1;    /* Default: 1 (can shrink) */
flex-basis: auto;  /* Default: auto */
flex: 1;           /* Shorthand: flex-grow flex-shrink flex-basis */
align-self: auto | flex-start | flex-end | center | baseline | stretch;
order: 0;          /* Default: 0 */
```

## Common Patterns

### Perfect Centering
```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}
```

### Navigation Bar
```css
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
```

### Equal Width Columns
```css
.container {
    display: flex;
}
.item {
    flex: 1;
}
```

### Sticky Footer
```css
body {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}
main {
    flex: 1;
}
```

## Browser Compatibility

All examples use modern Flexbox features supported by:
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- All modern browsers

## Additional Resources

- [MDN Flexbox Guide](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout)
- [CSS-Tricks Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Flexbox Froggy](https://flexboxfroggy.com/) - Interactive game for learning

## Assignment Ideas

1. Create a responsive navigation bar with dropdown menus
2. Build a pricing card layout with equal height cards
3. Design a blog layout with sidebar using flexbox
4. Implement a mobile-first responsive gallery
5. Create a dashboard with flexible panels
6. Build a footer with multiple columns that stack on mobile
7. Design a form layout using flexbox for alignment

## Common Mistakes to Avoid

1. Using flexbox for two-dimensional layouts (use Grid instead)
2. Forgetting that `flex: 1` is shorthand for `flex: 1 1 0%`
3. Not understanding the difference between `align-items` and `align-content`
4. Overusing flexbox when simple block layout would work
5. Not considering `gap` property for spacing (cleaner than margins)

---

**Course:** Internet Technology (CMP 173)
**Level:** Bachelor BCSIT, First Year
**Institution:** Pokhara University

## Comparison with Grid Examples

While Flexbox excels at one-dimensional layouts, Grid (Unit 5.2) is better for two-dimensional layouts. Students should understand when to use each:

- **Flexbox**: Navigation bars, card wrapping, component alignment
- **Grid**: Page layouts, photo galleries, complex grid systems

Both can work together in the same project!
