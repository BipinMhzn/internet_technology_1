# Responsive Web Design Examples

This directory contains comprehensive examples for teaching responsive web design concepts in Unit 5 (Section 5.4) of the Internet Technology course.

## Files Included

### 1. **01_basic_responsive_layout.html**
- **Concepts Covered:**
  - Mobile-first approach
  - Basic media query breakpoints (576px, 768px, 992px, 1200px)
  - Flexible containers
  - Responsive cards
  - Flexbox layouts
  - Print styles

- **Key Features:**
  - Container that adjusts width based on screen size
  - Sidebar and main content that stack on mobile, side-by-side on tablet+
  - Card grid that shows 1, 2, or 3 columns based on viewport
  - Demonstrates mobile-first CSS methodology

### 2. **02_responsive_navigation.html**
- **Concepts Covered:**
  - Responsive navigation patterns
  - Hamburger menu for mobile
  - Horizontal navigation for desktop
  - JavaScript toggle functionality
  - Showing/hiding elements based on breakpoints

- **Key Features:**
  - Mobile: Hamburger menu with vertical navigation
  - Desktop: Horizontal navigation bar
  - Smooth transitions
  - Visual indicators for current breakpoint

### 3. **03_responsive_images.html**
- **Concepts Covered:**
  - Fluid/flexible images (max-width: 100%)
  - Responsive background images with media queries
  - Picture element for art direction
  - srcset and sizes attributes
  - object-fit property
  - Responsive image grids

- **Key Features:**
  - Multiple methods for handling responsive images
  - Code examples for each technique
  - Visual demonstrations
  - Best practices section

### 4. **04_media_queries_demo.html**
- **Concepts Covered:**
  - Width-based media queries
  - Orientation media queries (portrait/landscape)
  - Dark mode detection (prefers-color-scheme)
  - Hover capability detection
  - Print media queries
  - Reduced motion preference

- **Key Features:**
  - Live breakpoint indicator
  - Visual demonstration of each media query type
  - Comprehensive code examples
  - Common breakpoints reference table

### 5. **05_complete_responsive_website.html**
- **Concepts Covered:**
  - Complete responsive website structure
  - Mobile-first development
  - Responsive navigation
  - Hero section
  - Grid layouts
  - Forms
  - Footer
  - Accessibility features

- **Key Features:**
  - Full website example combining all concepts
  - Sticky navigation
  - Responsive grids (features, services, gallery)
  - Contact form
  - Smooth scrolling
  - Reduced motion support

## How to Use These Examples

### For Students:
1. Open each HTML file in a web browser
2. Resize the browser window to see responsive behavior
3. Use browser DevTools to test different device sizes
4. Study the CSS code to understand media query syntax
5. Try modifying values to see how changes affect the layout

### For Instructors:
1. Use these as live demonstrations in class
2. Assign students to modify and enhance the examples
3. Use as reference for practical assignments
4. Demonstrate mobile-first vs desktop-first approaches
5. Show how to use browser DevTools for testing

## Key Concepts Demonstrated

### Mobile-First Approach
All examples use mobile-first CSS, starting with base styles for mobile devices and adding complexity for larger screens:

```css
/* Base (mobile) styles */
.element {
    width: 100%;
    padding: 15px;
}

/* Tablet and up */
@media (min-width: 768px) {
    .element {
        width: 750px;
        margin: 0 auto;
    }
}
```

### Common Breakpoints
- **Mobile:** < 576px
- **Small:** ≥ 576px (landscape phones)
- **Medium:** ≥ 768px (tablets)
- **Large:** ≥ 992px (desktops)
- **Extra Large:** ≥ 1200px (large desktops)

### Responsive Techniques
1. **Fluid Grids:** Using percentages and flexible units
2. **Flexible Images:** max-width: 100%, height: auto
3. **Media Queries:** Conditional styles based on device characteristics
4. **Viewport Meta Tag:** Essential for mobile responsiveness
5. **Flexbox/Grid:** Modern layout systems

## Testing Responsive Designs

### Browser DevTools
1. Open DevTools (F12 or Right-click → Inspect)
2. Click the device toggle icon (Ctrl+Shift+M)
3. Select different device presets
4. Or manually resize the viewport

### Real Device Testing
- Test on actual mobile devices when possible
- Use different browsers (Chrome, Firefox, Safari)
- Test both portrait and landscape orientations

## Assignment Ideas

1. **Modify Basic Layout:** Change breakpoints and colors
2. **Create Your Navigation:** Build a custom responsive menu
3. **Image Gallery:** Create a photo gallery with different layouts
4. **Landing Page:** Build a complete responsive landing page
5. **Blog Layout:** Create a responsive blog with sidebar

## Best Practices Demonstrated

✓ Mobile-first approach
✓ Semantic HTML
✓ Accessible navigation
✓ Performance optimization
✓ Cross-browser compatibility
✓ Print-friendly styles
✓ Reduced motion support
✓ Clear, commented code

## Additional Resources

- MDN Web Docs: Responsive Design
- CSS-Tricks: Complete Guide to Responsive Web Design
- W3C Mobile Web Best Practices
- Google Web Fundamentals: Responsive Design

## Browser Compatibility

All examples use standard CSS that works in:
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers

## Notes for BCSIT Students

These examples align with the Unit 5 syllabus requirements:
- ✓ Create responsive designs using media queries
- ✓ Implement breakpoints and mobile-first approach
- ✓ Apply responsive typography
- ✓ Handle responsive images
- ✓ Build responsive layouts

**Remember:** Responsive design is not just about screen sizes, it's about creating flexible, accessible websites that work well for all users on all devices!

---

**Course:** Internet Technology (CMP 173)
**Program:** BCSIT, Pokhara University
**Unit:** 5.4 - Responsive Web Design
**Created:** 2024
