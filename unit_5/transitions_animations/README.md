# CSS Transitions & Animations Examples - Unit 5

This folder contains comprehensive CSS Transitions and Animations examples for teaching Internet Technology course at Pokhara University.

## Examples Overview

### Transition Fundamentals (Examples 1-4)
1. **01_basic_transitions.html** - Introduction to Transitions
   - With vs without transitions
   - `transition` property
   - Different durations

2. **02_timing_functions.html** - Timing Functions
   - linear, ease, ease-in, ease-out, ease-in-out
   - cubic-bezier() custom curves
   - Visual race demonstration
   - Interactive button examples

3. **03_transform_property.html** - CSS Transform
   - scale(), rotate(), translate(), skew()
   - Combining multiple transforms
   - 3D transforms (rotateX, rotateY, rotateZ)
   - transform-origin property

4. **04_multiple_transitions.html** - Multiple Transitions
   - Transitioning multiple properties
   - Different durations per property
   - transition-delay for staggered effects
   - Best practices

### Animation Fundamentals (Examples 5-7)
5. **05_basic_animations.html** - Introduction to Animations
   - Transitions vs Animations comparison
   - @keyframes syntax
   - Common animations (pulse, bounce, rotate, fade)
   - animation property

6. **06_keyframes.html** - Advanced Keyframes
   - Multi-step animations (0%, 25%, 50%, 75%, 100%)
   - Complex animation paths
   - Staggered animations
   - steps() timing function

7. **07_animation_properties.html** - Animation Properties
   - animation-duration
   - animation-iteration-count
   - animation-direction (normal, reverse, alternate)
   - animation-fill-mode
   - animation-play-state
   - Interactive controls

### Practical Applications (Examples 8-10)
8. **08_loading_spinners.html** - Loading Indicators
   - 9 different loading spinner styles
   - Progress bars
   - Skeleton loaders
   - Ripple effects
   - When to use each type

9. **09_hover_effects.html** - Hover Effects & Microinteractions
   - Card effects (lift, grow, rotate, flip)
   - Button effects (glow, slide, shake, gradient)
   - Link underlines
   - Image zoom
   - Neon text effect
   - Mobile considerations

10. **10_complete_example.html** - Complete Interactive Demo
    - Full product card implementation
    - Combines multiple techniques
    - Page load animations
    - Staggered effects
    - Interactive states
    - Real-world application

## Syllabus Coverage

These examples align with **Unit 5: Advanced Topics on CSS**, specifically section **5.3 CSS Transitions and Animations**.

## Key Learning Outcomes

Students will learn to:
- Create smooth transitions between states
- Understand timing functions and their effects
- Use CSS transforms for performant animations
- Define complex animations with keyframes
- Control animation behavior with various properties
- Build practical loading indicators
- Implement engaging hover effects
- Combine transitions and animations effectively

## Transitions vs Animations

### Use Transitions for:
- State changes (hover, focus, active)
- Two-state animations (start → end)
- Simple, triggered effects
- UI feedback

### Use Animations for:
- Multi-step sequences
- Automatic/continuous motion
- Loading indicators
- Attention-grabbing effects
- Complex choreography

## Performance Best Practices

### ✅ High Performance (GPU Accelerated)
```css
transform: translate(), scale(), rotate();
opacity: 0 to 1;
```

### ❌ Lower Performance (Causes Reflow/Repaint)
```css
width, height (avoid animating these)
top, left, right, bottom
margin, padding
```

## Quick Reference

### Transition Syntax
```css
/* Shorthand */
transition: property duration timing-function delay;

/* Examples */
transition: all 0.3s ease;
transition: transform 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
transition: opacity 0.3s, transform 0.5s;
```

### Animation Syntax
```css
/* Define keyframes */
@keyframes animationName {
    0% { /* start styles */ }
    50% { /* middle styles */ }
    100% { /* end styles */ }
}

/* Apply animation */
animation: name duration timing-function delay iteration-count direction fill-mode;

/* Example */
animation: slide 2s ease-in-out 0s infinite alternate forwards;
```

### Transform Functions
```css
transform: translateX(100px);
transform: translateY(-50px);
transform: scale(1.5);
transform: rotate(45deg);
transform: skewX(20deg);

/* Combine multiple */
transform: translateX(50px) rotate(45deg) scale(1.2);

/* 3D transforms */
transform: rotateX(180deg);
transform: rotateY(180deg);
transform: perspective(500px) rotateY(45deg);
```

### Timing Functions
```css
linear              /* Constant speed */
ease                /* Slow-fast-slow (default) */
ease-in             /* Slow start */
ease-out            /* Slow end */
ease-in-out         /* Slow start and end */
cubic-bezier(x1, y1, x2, y2)  /* Custom curve */
steps(n)            /* Stepped animation */
```

## Common Patterns

### Hover Effect
```css
.button {
    transition: transform 0.3s, box-shadow 0.3s;
}

.button:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.2);
}
```

### Loading Spinner
```css
@keyframes spin {
    to { transform: rotate(360deg); }
}

.spinner {
    border: 3px solid #f3f3f3;
    border-top: 3px solid #3498db;
    border-radius: 50%;
    animation: spin 1s linear infinite;
}
```

### Fade In on Load
```css
@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

.element {
    animation: fadeIn 1s ease-in;
}
```

### Staggered Animation
```css
.item:nth-child(1) { animation-delay: 0s; }
.item:nth-child(2) { animation-delay: 0.1s; }
.item:nth-child(3) { animation-delay: 0.2s; }
```

## Teaching Tips

1. **Start Simple**: Begin with basic transitions before moving to animations
2. **Visual Learning**: Use browser DevTools to manipulate animation values live
3. **Compare Methods**: Show when to use transitions vs animations
4. **Performance**: Emphasize using transform and opacity
5. **Practical Examples**: Focus on real-world use cases (buttons, cards, loaders)
6. **Mobile**: Discuss hover alternatives for touch devices

## Browser Compatibility

All examples use modern CSS features supported by:
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)

For older browsers, consider vendor prefixes:
```css
-webkit-transform: rotate(45deg);
-ms-transform: rotate(45deg);
transform: rotate(45deg);
```

## Tools & Resources

- [Cubic Bezier Generator](https://cubic-bezier.com) - Create custom timing functions
- [Animista](https://animista.net) - Ready-made CSS animations
- [Loading.io](https://loading.io/css/) - CSS loading animations
- [MDN Transitions Guide](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions)
- [MDN Animations Guide](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations)

## Assignment Ideas

1. Create a loading screen with multiple animated elements
2. Build an interactive card gallery with hover effects
3. Design an animated navigation menu
4. Implement a progress indicator for multi-step form
5. Create a logo animation that plays on page load
6. Build a parallax scrolling effect
7. Design an animated timeline
8. Create custom button hover effects library
9. Build an animated hero section
10. Implement a typing animation effect

## Common Mistakes to Avoid

1. ❌ Animating width/height instead of transform: scale()
2. ❌ Animating top/left instead of transform: translate()
3. ❌ Using transitions when animations are needed (multi-step)
4. ❌ Making animations too slow (>1s for UI feedback)
5. ❌ Forgetting animation-fill-mode for states
6. ❌ Not considering reduced-motion preferences
7. ❌ Overusing animations (less is more)
8. ❌ Not testing on actual devices (especially mobile)

## Accessibility Considerations

### Respect User Preferences
```css
/* Disable animations for users who prefer reduced motion */
@media (prefers-reduced-motion: reduce) {
    * {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
    }
}
```

### Best Practices
- Don't rely solely on animation to convey information
- Avoid rapid flashing (seizure risk)
- Provide pause/stop controls for continuous animations
- Ensure sufficient color contrast in animated elements
- Test with screen readers

## Animation Performance Checklist

- ✅ Use `transform` and `opacity` when possible
- ✅ Use `will-change` for complex animations (sparingly)
- ✅ Keep animations under 60fps
- ✅ Test on low-end devices
- ✅ Use Chrome DevTools Performance panel
- ✅ Minimize paint and layout operations
- ✅ Use CSS instead of JavaScript when possible

---

**Course:** Internet Technology (CMP 173)
**Level:** Bachelor BCSIT, First Year
**Institution:** Pokhara University

## Integration with Other Topics

These animations work great with:
- **Flexbox (5.1)** - Animated flex layouts
- **Grid (5.2)** - Animated grid transitions
- **JavaScript (Units 6-7)** - Trigger animations via JS
- **Responsive Design (5.4)** - Adaptive animations for different screens
