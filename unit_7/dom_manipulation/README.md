# Unit 7.3: DOM Manipulation - Practical Examples

## 📚 Example Files Overview

This directory contains interactive HTML examples for teaching DOM Manipulation to BCSIT students.

### Example Files

| File | Topic | Description |
|------|-------|-------------|
| `01_selecting_elements.html` | Selecting Elements | getElementById, querySelector, live vs static collections |
| `02_modifying_elements.html` | Modifying Elements | innerHTML, attributes, styles, classes |
| `03_event_handling.html` | Event Handling | addEventListener, event object, delegation |

## 🎯 Learning Path

### For Students:
1. Start with `01_selecting_elements.html` - learn to select elements
2. Move to `02_modifying_elements.html` - modify element properties
3. Master `03_event_handling.html` - handle user interactions

### For Instructors:
- Each file is self-contained and browser-ready
- Interactive demos for hands-on learning
- Console logging for debugging practice
- Real-world examples (counters, todo lists, forms)

## 💡 How to Use

### In Classroom:
1. Open `index.html` for navigation
2. Click through examples in order
3. Demonstrate interactive features
4. Encourage students to modify code
5. Use browser console (F12) to show logs

### For Practice:
- View source code of examples
- Modify demo behavior
- Create similar functionality
- Build mini-projects combining concepts

## 🔍 Key Concepts Covered

### Selecting Elements
- getElementById() - fastest for unique IDs
- getElementsByClassName() - live HTMLCollection
- getElementsByTagName() - all elements of type
- querySelector() - first match with CSS selector
- querySelectorAll() - all matches (NodeList)

### Modifying Elements
- Content: innerHTML, textContent, innerText
- Attributes: getAttribute, setAttribute, dataset
- Styles: element.style.property
- Classes: classList.add/remove/toggle

### Event Handling
- addEventListener() - attach event listeners
- Event object - target, type, coordinates
- Common events - click, input, keydown, submit
- Event delegation - handle dynamic elements

## 📝 Practice Exercises

After completing the examples, students should be able to:

1. **Selection Exercise**: Select and highlight elements based on criteria
2. **Modification Exercise**: Build a theme switcher
3. **Event Exercise**: Create an interactive form validator
4. **Project**: Build a complete todo list app

## ⚠️ Common Pitfalls

1. **Security**: Using innerHTML with user input (XSS risk)
2. **Performance**: Selecting elements repeatedly in loops
3. **Null checks**: Not checking if element exists before using it
4. **Event listeners**: Not removing when cleaning up

## 🛠️ Browser Requirements

- Modern web browser (Chrome, Firefox, Edge, Safari)
- JavaScript enabled
- Developer console access (F12)

## 📖 Additional Resources

Students should refer to:
- Unit 7 notes: `../unit_7_notes.md`
- MDN Web Docs: https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model
- JavaScript.info: https://javascript.info/document

## 🎓 Assessment Tips

For instructors assessing student understanding:

1. **Selection**: Can they choose the right method?
2. **Modification**: Do they understand innerHTML vs textContent?
3. **Events**: Can they attach listeners correctly?
4. **Delegation**: Do they understand event bubbling?
5. **Best Practices**: Do they follow security guidelines?

## 💡 Best Practices

1. **Use textContent for user input** - Prevents XSS attacks
2. **Cache DOM selections** - Better performance
3. **addEventListener over inline handlers** - More flexible
4. **Event delegation** - Better for dynamic content
5. **classList over className** - Safer and clearer

---

**Created for:** BCSIT First Year, Semester I
**Course:** Internet Technology (CMP 173)
**Institution:** Pokhara University

**Last Updated:** 2026-02-04
