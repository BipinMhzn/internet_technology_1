# Unit 5: Advanced Topics on CSS - Question Bank

**Course:** Internet Technology I (CMP 173)
**Program:** BCSIT, Pokhara University
**Unit Duration:** 7 Hours

---

## Section A: Very Short Answer Questions (2 Marks Each)

### CSS Flexbox

1. What is CSS Flexbox and what is its primary use case?

2. Differentiate between flex container and flex items.

3. What is the default value of the `flex-direction` property?

4. Explain the difference between `justify-content` and `align-items` in Flexbox.

5. What does the `flex: 1` shorthand property represent?

6. Write the CSS code to center an element both horizontally and vertically using Flexbox.

7. What is the purpose of the `flex-wrap` property?

8. Explain the `order` property in Flexbox.

### CSS Grid

9. What is CSS Grid and how does it differ from Flexbox?

10. Define grid lines, grid tracks, and grid cells.

11. What is the `fr` unit in CSS Grid?

12. Differentiate between `auto-fill` and `auto-fit` in CSS Grid.

13. What is the purpose of `grid-template-areas` property?

14. Write the syntax to create a 3-column grid with equal width.

15. Explain the use of `grid-gap` or `gap` property.

16. What does `grid-column: span 2` mean?

### CSS Transitions and Animations

17. What is the difference between CSS transitions and animations?

18. List any four transition timing functions.

19. What is the purpose of the `@keyframes` rule?

20. Write the shorthand syntax for CSS transition property.

21. What is the `animation-fill-mode` property used for?

22. Explain the `transform` property with one example.

23. What is the difference between `animation-iteration-count: 3` and `animation-iteration-count: infinite`?

24. Define the `animation-direction: alternate` property.

### Responsive Web Design

25. What is responsive web design and how can it be accomplished?

26. What is the purpose of the viewport meta tag in HTML?

27. Write the basic syntax of a media query.

28. Differentiate between mobile-first and desktop-first approaches.

29. What are CSS breakpoints?

30. Explain the `max-width: 100%` rule for responsive images.

31. What is the difference between `min-width` and `max-width` in media queries?

32. List any four common breakpoint sizes for responsive design.

### CSS Specificity and Inheritance

33. What is CSS specificity?

34. Which has higher specificity: class selector or ID selector?

35. What is the purpose of the `!important` rule in CSS?

36. Explain CSS inheritance with an example.

37. What is the difference between `inherit` and `initial` values?

38. Calculate the specificity score of `#header .nav li a`.

39. Which CSS properties are inherited by default?

40. What does the `unset` value do in CSS?

### CSS Units and Values

41. Differentiate between absolute and relative units in CSS.

42. What is the difference between `em` and `rem` units?

43. What are viewport units (vw, vh, vmin, vmax)?

44. Explain the `ch` unit in CSS.

45. What is the difference between `px` and `pt` units?

46. Write the syntax of the `calc()` function with an example.

47. What does `clamp(16px, 4vw, 32px)` do?

48. Explain the purpose of CSS custom properties (variables).

### CSS Preprocessors

49. What are CSS preprocessors? Name any two.

50. What is the main advantage of using Sass/SCSS?

51. What is the purpose of variables in CSS preprocessors?

52. Explain nesting in Sass with a simple example.

53. What is a mixin in Sass?

54. How do you import partial files in Sass?

55. What does the `&` symbol represent in Sass?

56. Differentiate between Sass and SCSS syntax.

### CSS Best Practices and Optimization

57. It is better to avoid `@import` statements in CSS. Why?

58. What is the BEM naming convention in CSS?

59. Why should you minimize CSS specificity?

60. What is the purpose of CSS reset or normalize?

61. Explain the concept of CSS code organization.

62. What are vendor prefixes in CSS?

63. Why is it important to reduce repaints and reflows?

64. What is the `will-change` property used for?

---

## Section B: Descriptive Answer Questions (10 Marks Each)

### CSS Flexbox

1. Explain CSS Flexbox layout with its container and item properties. Provide examples of at least 5 properties.

2. Create a responsive navigation bar using CSS Flexbox that displays items horizontally on desktop and vertically on mobile.

3. Design the following web page layout using CSS Flexbox, incorporating at least three different flex properties:
   ```
   [Header - Full Width]
   [Sidebar 1] [Article - Main Content] [Sidebar 2]
   [Footer - Full Width]
   ```

4. Explain the following Flexbox properties with examples:
   - justify-content
   - align-items
   - flex-grow
   - flex-shrink
   - flex-basis

5. Write HTML and CSS code to create a card layout using Flexbox where cards wrap to the next line and grow equally to fill available space.

### CSS Grid

6. Explain CSS Grid layout system with its key concepts. Demonstrate the use of `grid-template-columns`, `grid-template-rows`, and `gap` properties.

7. Create a responsive image gallery using CSS Grid where images automatically adjust based on screen size using `auto-fit` or `auto-fill`.

8. Design a dashboard layout using CSS Grid with named grid areas:
   ```
   [Header spanning full width]
   [Sidebar] [Main Content] [Widgets]
   [Footer spanning full width]
   ```

9. Differentiate between CSS Flexbox and CSS Grid with suitable examples. When would you use one over the other?

10. Explain the following CSS Grid properties with examples:
    - grid-template-areas
    - grid-column
    - grid-row
    - justify-items
    - align-items

### CSS Transitions and Animations

11. Explain CSS transitions with all transition properties. Create a button with hover effects using transitions.

12. What are CSS animations? Explain the `@keyframes` rule and animation properties with a practical example.

13. Create the following animations using CSS:
    a. A loading spinner
    b. A pulse effect on a button
    c. A fade-in effect

14. Explain the difference between CSS transitions and animations. Provide examples where each would be more appropriate.

15. Create a card component that has the following effects:
    - Scale up on hover
    - Shadow increases on hover
    - Smooth transition for all changes

### Responsive Web Design

16. What is responsive web design? Explain media queries, breakpoints, and the mobile-first approach with examples.

17. Create a responsive webpage layout that displays:
    - 3 columns on desktop (width >= 992px)
    - 2 columns on tablet (width >= 768px)
    - 1 column on mobile (width < 768px)

18. Explain the viewport meta tag and its properties. Demonstrate responsive typography using relative units and media queries.

19. Implement a responsive navigation menu using HTML and CSS with media queries. The menu should be horizontal on desktop and collapse into a vertical menu on mobile.

20. Explain responsive images using:
    a. CSS max-width property
    b. HTML srcset attribute
    c. Picture element

### CSS Specificity and Inheritance

21. Explain CSS specificity with its hierarchy and calculation method. Provide examples showing how specificity determines which rule applies.

22. What is CSS inheritance? List inherited and non-inherited properties. Explain the values: inherit, initial, unset, and revert.

23. Explain the CSS cascade with its priority order. How do origin, specificity, and source order affect which styles are applied?

24. Calculate the specificity for the following selectors and determine which rule would apply:
    ```css
    div p { color: blue; }
    .text { color: red; }
    #content p { color: green; }
    p.text { color: yellow; }
    ```

25. Explain techniques to avoid specificity wars in CSS. Discuss best practices for writing maintainable CSS selectors.

### CSS Units and Values

26. Differentiate between absolute and relative units in CSS. Explain with examples: px, em, rem, %, vw, vh, and ch.

27. Explain the following CSS functions with practical examples:
    - calc()
    - min()
    - max()
    - clamp()
    - var()

28. What are CSS custom properties (variables)? Demonstrate their use in creating a theme switcher for light and dark modes.

29. Explain viewport units (vw, vh, vmin, vmax) with examples. What are the new viewport units (svh, lvh, dvh) and why were they introduced?

30. Compare and provide use cases for:
    - px vs rem
    - em vs rem
    - % vs vw/vh
    - Absolute vs relative units

### CSS Preprocessors

31. What are CSS preprocessors? Explain the features of Sass/SCSS including variables, nesting, mixins, and functions.

32. Demonstrate the use of Sass with examples covering:
    - Variables
    - Nesting
    - Mixins with parameters
    - @import and partials

33. Explain the following Sass features with examples:
    - @extend and inheritance
    - Control directives (@if, @for, @each)
    - Functions
    - Parent selector (&)

34. Compare Sass and Less preprocessors. What are the advantages of using preprocessors over plain CSS?

35. Explain CSS custom properties (native CSS variables) and compare them with Sass variables. When would you use one over the other?

### CSS Best Practices and Optimization

36. Explain CSS code organization methodologies: BEM, OOCSS, and SMACSS. Provide examples of each.

37. What are CSS performance optimization techniques? Explain:
    - Minimizing CSS
    - Reducing specificity
    - Avoiding expensive selectors
    - Minimizing repaints and reflows

38. Describe CSS naming conventions and file structure for large projects. How would you organize CSS for maintainability?

39. Explain CSS accessibility best practices including:
    - Focus styles
    - Reduced motion preferences
    - High contrast mode
    - Screen reader considerations

40. What are vendor prefixes in CSS? Explain their purpose and demonstrate tools like Autoprefixer. Discuss CSS reset vs Normalize.

---

## Section C: Long Answer Questions (15 Marks Each)

### Comprehensive Questions

1. **Complete Responsive Website Layout**

   Create a fully responsive website layout for a restaurant with the following requirements:

   a. Use CSS Flexbox for the navigation bar (7 marks)
   - Logo on the left
   - Menu items (Home, Menu, About, Contact) on the right
   - Hamburger menu icon on mobile
   - Smooth transitions on hover

   b. Use CSS Grid for the main content area (8 marks)
   - Hero section spanning full width
   - 3-column menu items grid on desktop
   - 2-column grid on tablet
   - 1-column grid on mobile
   - Gap between grid items

   Include proper HTML structure, CSS styling, and media queries.

2. **Advanced CSS Animations and Interactions**

   a. Create a loading animation with three dots that bounce sequentially using CSS animations and keyframes. (5 marks)

   b. Design an animated card component with the following features: (10 marks)
   - Card flips on hover showing back content
   - Smooth transitions for all effects
   - Scale and shadow changes
   - Use transform properties (rotateY, scale, translateZ)
   - Implement animation timing functions

   Provide complete HTML and CSS code with explanations.

3. **CSS Flexbox vs Grid: Complete Comparison**

   a. Write detailed differences between CSS Flexbox and CSS Grid with examples. (6 marks)
   - Dimensional differences
   - Use cases
   - Content-first vs layout-first
   - Alignment capabilities

   b. Implement the same layout using both Flexbox and Grid: (9 marks)
   ```
   [Header]
   [Sidebar] [Main] [Aside]
   [Footer]
   ```
   - Write HTML structure
   - Implement using Flexbox
   - Implement using Grid
   - Make both responsive
   - Compare which is better for this layout and why

4. **Responsive Design: Complete Implementation**

   Your city is planning a technology conference and has asked you to create a responsive website.

   a. Create a responsive registration form with: (7 marks)
   - Personal details (Name, Email, Phone)
   - Conference track selection (Web Development, Mobile, AI)
   - Responsive form layout
   - Form styling with CSS

   b. Implement responsive design with: (8 marks)
   - Mobile-first approach
   - Breakpoints for mobile (< 768px), tablet (768px-1024px), desktop (> 1024px)
   - Responsive typography using clamp()
   - Responsive images
   - Flexible grid layout
   - Media queries for different screen sizes

   Include complete HTML and CSS code.

5. **CSS Preprocessors and Modern CSS**

   a. Explain CSS preprocessors (Sass/SCSS) with examples covering: (8 marks)
   - Variables and their scope
   - Nesting with parent selector
   - Mixins with parameters and default values
   - Functions and operations
   - @import and partials
   - Control directives (@if, @for, @each)

   b. Create a theme system using CSS custom properties: (7 marks)
   - Define color variables for light and dark themes
   - Create a theme switcher mechanism
   - Demonstrate scope and inheritance of variables
   - Show how variables can be changed with JavaScript
   - Compare with Sass variables

6. **CSS Specificity, Inheritance, and Best Practices**

   a. Explain CSS specificity with: (5 marks)
   - Specificity hierarchy
   - Calculation method with examples
   - The !important rule
   - Techniques to avoid specificity wars

   b. Describe CSS inheritance with: (4 marks)
   - Inherited vs non-inherited properties
   - Controlling inheritance (inherit, initial, unset, revert)

   c. Implement a component using BEM methodology: (6 marks)
   - Create a card component with variations
   - Use proper BEM naming (block__element--modifier)
   - Demonstrate low specificity
   - Include modifiers for different card types
   - Write maintainable and scalable CSS

7. **Advanced CSS Units and Responsive Typography**

   a. Explain CSS units with examples: (6 marks)
   - Absolute units (px, pt, cm)
   - Relative units (em, rem, %)
   - Viewport units (vw, vh, vmin, vmax)
   - Character units (ch, ex)
   - When to use each unit

   b. Demonstrate CSS functions: (5 marks)
   - calc() for complex calculations
   - min() and max() for responsive sizing
   - clamp() for fluid typography
   - var() for CSS custom properties

   c. Create a fully responsive typography system: (4 marks)
   - Base font size setup
   - Headings using clamp()
   - Responsive spacing using rem
   - Media query adjustments

8. **Complete CSS Animation Project**

   Create an animated product showcase page with the following features:

   a. Hero section with animations: (5 marks)
   - Fade-in and slide-up animation for heading
   - Staggered animation for multiple elements
   - Background gradient animation
   - Call-to-action button with hover effects

   b. Product cards with interactions: (6 marks)
   - Grid layout using CSS Grid
   - Hover effects with scale and shadow
   - Flip animation showing product details on back
   - Smooth transitions for all properties

   c. Loading states and micro-interactions: (4 marks)
   - Skeleton loading animation
   - Button loading spinner
   - Smooth transitions between states

   Provide complete HTML, CSS code with proper comments.

9. **CSS Architecture for Large Projects**

   a. Explain CSS code organization for a large-scale project: (6 marks)
   - File structure (base, components, layouts, utilities)
   - Naming conventions (BEM, OOCSS, or SMACSS)
   - CSS methodologies comparison
   - Import strategy

   b. Demonstrate a component-based approach: (5 marks)
   - Create a button component with variations
   - Create a card component with modifiers
   - Show proper separation of concerns
   - Use CSS custom properties for theming

   c. Explain CSS optimization techniques: (4 marks)
   - Minimizing CSS size
   - Reducing specificity
   - Avoiding expensive selectors
   - Performance best practices

10. **Responsive Web Design: Complete Case Study**

    Design a complete responsive portfolio website with:

    a. Header and Navigation: (4 marks)
    - Responsive navigation using Flexbox
    - Mobile hamburger menu
    - Sticky navigation
    - Smooth scroll transitions

    b. Main Content Area: (6 marks)
    - Hero section with full viewport height
    - Project gallery using CSS Grid
    - Responsive image handling
    - Card hover effects with transitions

    c. Responsive Implementation: (5 marks)
    - Mobile-first approach
    - Three breakpoints (mobile, tablet, desktop)
    - Responsive typography
    - Media queries for all sections
    - Accessibility considerations (focus states, reduced motion)

    Include complete HTML and CSS code with comments.

---

## Practice Problems

### Flexbox Challenges

1. Create a holy grail layout using Flexbox (header, footer, sidebar, main, aside)
2. Build a responsive pricing table with three cards
3. Create a centered login form using Flexbox
4. Implement a sticky footer using Flexbox

### Grid Challenges

1. Create a magazine-style layout with asymmetric grid
2. Build a responsive dashboard with multiple widgets
3. Create a masonry-style image gallery
4. Implement an auto-responsive grid using auto-fit

### Animation Challenges

1. Create a typewriter effect using CSS animations
2. Build a shake animation for error states
3. Create a smooth page transition effect
4. Implement a parallax scrolling effect

### Responsive Design Challenges

1. Create a mobile-first responsive form
2. Build a responsive email template
3. Create a responsive data table
4. Implement a responsive carousel

---

## Model Answers Guide (For Reference)

### Short Answer (2 marks) - Structure:
- **Definition/Concept** (0.5 marks)
- **Key points** (1 mark)
- **Example/Syntax** (0.5 marks)

### Descriptive Answer (10 marks) - Structure:
- **Introduction** (1-2 marks)
- **Main content with examples** (6-7 marks)
- **Code examples** (2-3 marks)
- **Conclusion/Summary** (0-1 marks)

### Long Answer (15 marks) - Structure:
- **Introduction** (1-2 marks)
- **Detailed explanation** (4-5 marks)
- **Complete code implementation** (7-8 marks)
- **Comments and best practices** (1-2 marks)

---

## Tips for Exam Preparation

1. **Focus on Practical Implementation**: Practice writing complete code examples
2. **Understand Concepts**: Don't just memorize; understand when and why to use each technique
3. **Compare and Contrast**: Be ready to differentiate between similar concepts
4. **Real-world Examples**: Think of practical use cases for each concept
5. **Code Neatly**: Proper indentation and commenting are important
6. **Cover All Topics**: Don't skip any subtopic from the syllabus
7. **Practice Responsive Design**: This is heavily tested
8. **Review Old Questions**: Understand the pattern and types of questions asked

---

**Prepared for BCSIT First Year, Semester I**
**Internet Technology I (CMP 173)**
**Pokhara University**
