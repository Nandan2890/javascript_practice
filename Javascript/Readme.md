Here’s the difference between `let`, `var`, and `const` formatted in Markdown for GitHub:

```markdown
# Difference Between `let`, `var`, and `const` in JavaScript

| Feature            | `var`                 | `let`                 | `const`                  |
|---------------------|-----------------------|-----------------------|--------------------------|
| **Scope**          | Function-scoped       | Block-scoped          | Block-scoped             |
| **Hoisting**       | Hoisted with `undefined` | Hoisted (TDZ applies) | Hoisted (TDZ applies)    |
| **Reassignment**   | Allowed               | Allowed               | Not allowed              |
| **Redeclaration**  | Allowed               | Not allowed           | Not allowed              |

---

## Detailed Explanation and Examples

### 1. `var`
- **Scope**: Function-scoped. Accessible within the function it is declared in or globally if declared outside a function.
- **Hoisting**: Variables are hoisted to the top of their scope but initialized with `undefined`.
- **Reassignment**: Can be reassigned.
- **Redeclaration**: Can be redeclared in the same scope.

#### Example:
```javascript
function testVar() {
    console.log(a); // undefined (hoisted but not initialized)
    var a = 10;
    console.log(a); // 10
}

testVar();

// Redeclaration
var x = 5;
var x = 10; // No error
console.log(x); // 10
```

---

### 2. `let`
- **Scope**: Block-scoped. Accessible only within the block (`{}`) in which it is declared.
- **Hoisting**: Variables are hoisted but not initialized (Temporal Dead Zone).
- **Reassignment**: Can be reassigned.
- **Redeclaration**: Cannot be redeclared in the same scope.

#### Example:
```javascript
function testLet() {
    // console.log(b); // ReferenceError (in Temporal Dead Zone)
    let b = 20;
    console.log(b); // 20
}

testLet();

// Block scope
{
    let y = 30;
    console.log(y); // 30
}
// console.log(y); // ReferenceError: y is not defined

// Redeclaration
let z = 15;
// let z = 25; // SyntaxError: Identifier 'z' has already been declared
```

---

### 3. `const`
- **Scope**: Block-scoped, similar to `let`.
- **Hoisting**: Variables are hoisted but not initialized (Temporal Dead Zone).
- **Reassignment**: Cannot be reassigned. The value must be assigned at the time of declaration.
- **Redeclaration**: Cannot be redeclared in the same scope.

#### Example:
```javascript
const PI = 3.14;
console.log(PI); // 3.14

// Reassignment
// PI = 3.14159; // TypeError: Assignment to constant variable

// Objects and Arrays
const obj = { name: "John" };
obj.name = "Doe"; // Allowed (modifying properties is okay)
console.log(obj); // { name: "Doe" }

// Redeclaration
// const PI = 22/7; // SyntaxError: Identifier 'PI' has already been declared
```

---

## Key Takeaways
- Use `var` **rarely**, only for backward compatibility with older JavaScript.
- Use `let` for variables that **may change value**.
- Use `const` for **constants** or variables that should not be reassigned.