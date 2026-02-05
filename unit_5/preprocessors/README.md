# Unit 5.7: CSS Preprocessors - Practical Examples

## 📚 Example Files Overview

This directory contains interactive HTML examples for teaching CSS Preprocessors (SCSS/Sass) to BCSIT students.

### Example Files

| File | Topic | Description |
|------|-------|-------------|
| `01_variables.html` | SCSS Variables | Using $variables for colors, fonts, sizes |
| `02_nesting.html` | SCSS Nesting | Nesting selectors, parent selector (&), BEM |
| `03_mixins.html` | SCSS Mixins | Creating reusable code with @mixin and @include |

## 🎯 Learning Path

### For Students:
1. Start with `01_variables.html` - understand variable basics
2. Move to `02_nesting.html` - learn to nest selectors
3. Master `03_mixins.html` - create reusable mixins

### For Instructors:
- Each file is self-contained and browser-ready
- Examples show SCSS code and compiled CSS side-by-side
- Live demos demonstrate the concepts visually
- Color-coded sections for better learning

## 💡 How to Use

### In Classroom:
1. Open `index.html` for navigation or any example directly
2. Show SCSS code and compiled CSS comparison
3. Demonstrate live examples
4. Encourage students to try similar patterns
5. Explain compilation process

### For Practice:
- View SCSS code and predict compiled CSS
- Try to write similar SCSS patterns
- Understand when to use each feature
- Practice organizing code with preprocessors

## 🔍 Key Concepts Covered

### Variables ($)
- Declaring variables with $
- Using variables for colors, fonts, spacing
- Variable scope (global vs local)
- Variable interpolation #{}

### Nesting
- Basic nesting syntax
- Parent selector (&)
- Pseudo-classes and pseudo-elements
- BEM methodology with nesting
- Best practices (max 3-4 levels)

### Mixins
- Creating mixins with @mixin
- Using mixins with @include
- Mixins with parameters
- Default parameter values
- @content directive
- Mixins vs Extends

## 📝 Practice Exercises

After completing the examples, students should be able to:

1. **Variables Exercise**: Create a color scheme using SCSS variables
2. **Nesting Exercise**: Build a navigation menu with proper nesting
3. **Mixins Exercise**: Create button and card mixins with parameters
4. **Project**: Convert existing CSS to SCSS using all features

## ⚠️ Important Notes

### Compilation Required
- SCSS files need to be compiled to CSS
- Browsers don't understand SCSS directly
- Use Sass compiler: `sass style.scss style.css`
- Or use build tools: Webpack, Gulp, etc.

### Installation
```bash
# Install Sass globally
npm install -g sass

# Compile once
sass input.scss output.css

# Watch for changes
sass --watch input.scss:output.css
```

## 🛠️ Browser Requirements

- Modern web browser (Chrome, Firefox, Edge, Safari)
- JavaScript enabled
- No SCSS compiler needed for these examples (demos use plain CSS)

## 📖 Additional Resources

Students should refer to:
- Unit 5 notes: `../unit_5_notes.md`
- Sass Documentation: https://sass-lang.com/
- Sass Guidelines: https://sass-guidelin.es/

## 🎓 Assessment Tips

For instructors assessing student understanding:

1. **Variables**: Can students identify when to use variables?
2. **Nesting**: Do they understand nesting depth limits?
3. **Mixins**: Can they create mixins with parameters?
4. **Organization**: Do they know how to structure SCSS files?
5. **Compilation**: Do they understand the compilation process?

## 💡 Best Practices

1. **Naming Convention**: Use descriptive variable names
2. **Nesting Limit**: Max 3-4 levels deep
3. **File Organization**: Use partials (_variables.scss, _mixins.scss)
4. **Comments**: Document complex mixins and functions
5. **DRY Principle**: Don't repeat yourself - use mixins and variables

## 📧 Notes

- All examples are educational demonstrations
- SCSS code shown is for learning purposes
- Live demos use compiled CSS (CSS variables for similarity)
- Examples work offline

## 🎨 SCSS vs CSS Variables

| Feature | SCSS Variables | CSS Variables |
|---------|---------------|---------------|
| Syntax | `$color: blue;` | `--color: blue;` |
| Compilation | Build time | Runtime |
| Browser Support | All (compiles to CSS) | Modern browsers |
| Dynamic Changes | ❌ No | ✅ Yes (with JS) |
| Functions | ✅ Yes | Limited |
| Best For | Development | Dynamic theming |

---

**Created for:** BCSIT First Year, Semester I
**Course:** Internet Technology (CMP 173)
**Institution:** Pokhara University

**Last Updated:** 2026-02-04
