# Unit 7: Scope and Closures - Practical Examples

## 📚 Example Files Overview

This directory contains interactive HTML examples for teaching JavaScript scope and closures to BCSIT students.

### Example Files

| File | Topic | Description |
|------|-------|-------------|
| `01_global_scope.html` | Global Scope | Understanding variables accessible from anywhere |
| `02_function_scope.html` | Function Scope | Variables local to functions |
| `03_block_scope.html` | Block Scope | let/const vs var in blocks |
| `04_hoisting.html` | Hoisting | Variable and function hoisting behavior |
| `05_basic_closure.html` | Basic Closure | Introduction to closures |
| `06_closure_counter.html` | Interactive Counter | Practical closure example with UI |
| `07_closure_function_factory.html` | Function Factory | Creating specialized functions with closures |

## 🎯 Learning Path

### For Students:
1. Start with `01_global_scope.html` - understand global variables
2. Move to `02_function_scope.html` - learn function-level scope
3. Study `03_block_scope.html` - see the difference between var, let, const
4. Learn `04_hoisting.html` - understand JavaScript's hoisting mechanism
5. Begin closures with `05_basic_closure.html` - fundamental closure concepts
6. Practice with `06_closure_counter.html` - interactive closure application
7. Master with `07_closure_function_factory.html` - advanced closure patterns

### For Instructors:
- Each file is self-contained and can be opened directly in a browser
- Files include clear explanations, code examples, and console outputs
- Interactive buttons allow students to experiment
- Color-coded sections highlight important concepts
- Browser console integration for deeper exploration

## 💡 How to Use

### In Classroom:
1. Open any HTML file in a web browser (Chrome/Firefox recommended)
2. Click the "Run Example" button to see the demonstration
3. Read the explanations and observe the outputs
4. Open browser console (F12) for additional logs
5. Modify the code and reload to experiment

### For Practice:
- Open browser console (F12)
- Try the suggested console commands
- Experiment with creating your own examples
- Modify the code to test your understanding

## 🔍 Key Concepts Covered

### Scope
- **Global Scope**: Variables accessible everywhere
- **Function Scope**: Variables local to functions
- **Block Scope**: let/const within `{}`
- **Scope Chain**: How JavaScript looks up variables

### Hoisting
- `var` hoisting behavior (declaration moves up)
- Temporal Dead Zone (TDZ) for `let`/`const`
- Function hoisting differences

### Closures
- Functions remembering outer variables
- Data privacy and encapsulation
- Function factories
- Practical applications (counters, calculators)

## 📝 Practice Exercises

After completing the examples, students should be able to:

1. **Scope Exercise**: Write functions demonstrating all three scope types
2. **Hoisting Exercise**: Predict output of code with hoisting
3. **Closure Exercise**: Create a bank account with private balance
4. **Factory Exercise**: Build a discount calculator factory

## ⚠️ Common Mistakes to Avoid

1. **Using `var` in loops**: Always prefer `let` for loop variables
2. **Polluting global scope**: Use functions and modules
3. **Forgetting TDZ**: Don't access `let`/`const` before declaration
4. **Closure in loops**: Remember the loop closure pitfall with `var`

## 🛠️ Browser Requirements

- Modern web browser (Chrome, Firefox, Edge, Safari)
- JavaScript enabled
- Developer console access (F12 or Cmd+Option+I)

## 📖 Additional Resources

Students should refer to:
- Unit 7 notes: `unit_7_notes.md`
- MDN Web Docs: https://developer.mozilla.org/en-US/docs/Web/JavaScript
- JavaScript.info: https://javascript.info/

## 🎓 Assessment Tips

For instructors assessing student understanding:

1. **Scope Understanding**: Can students identify variable accessibility?
2. **Hoisting Awareness**: Do they understand declaration vs initialization?
3. **Closure Comprehension**: Can they explain how closures work?
4. **Practical Application**: Can they use closures to solve problems?

## 📧 Notes

- All examples work offline (no internet required)
- Examples use ES6+ syntax (arrow functions, let/const)
- Color-coded for visual learning
- Interactive for hands-on practice
- Console logs for deeper exploration

---

**Created for:** BCSIT First Year, Semester I
**Course:** Internet Technology (CMP 173)
**Institution:** Pokhara University

**Last Updated:** 2026-02-04
