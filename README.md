### **Stack in JavaScript: Deep Explanation**

A **stack** is a linear data structure that follows the **LIFO (Last In, First Out)** principle, meaning the last element added to the stack is the first one to be removed. Think of it as a stack of plates where you add and remove plates from the top.

---

### **Key Concepts of a Stack**

1. **Push Operation**  
   - Adds an element to the top of the stack.

2. **Pop Operation**  
   - Removes the top element from the stack.

3. **Peek/Top Operation**  
   - Returns the top element of the stack without removing it.

4. **IsEmpty Operation**  
   - Checks if the stack is empty.

5. **Size Operation**  
   - Returns the number of elements in the stack.

---

### **How Stacks Work**

Stacks can be implemented using arrays or linked lists. In JavaScript, arrays are commonly used because they provide built-in methods for stack-like operations.

---

### **Examples of Stack Usage**

1. **Reversing Strings**  
   - Push each character of a string onto a stack, then pop them to reverse the string.

2. **Bracket Matching**  
   - Use a stack to ensure that parentheses, brackets, or braces are properly matched.

3. **Undo/Redo Operations**  
   - Maintain a stack of operations to implement undo/redo functionality.

4. **Function Call Stack**  
   - The JavaScript runtime uses a call stack to manage function invocations.

---

### **Stack Implementation**

#### **1. Stack Using JavaScript Array**

JavaScript arrays have built-in methods like `push` and `pop` that make them ideal for implementing stacks.

```javascript
class Stack {
    constructor() {
        this.items = [];
    }

    // Push: Add an element to the stack
    push(element) {
        this.items.push(element);
    }

    // Pop: Remove and return the top element
    pop() {
        if (this.isEmpty()) {
            return "Underflow"; // Stack is empty
        }
        return this.items.pop();
    }

    // Peek: Return the top element without removing it
    peek() {
        if (this.isEmpty()) {
            return "Underflow"; // Stack is empty
        }
        return this.items[this.items.length - 1];
    }

    // IsEmpty: Check if the stack is empty
    isEmpty() {
        return this.items.length === 0;
    }

    // Size: Return the size of the stack
    size() {
        return this.items.length;
    }
}

// Usage
const stack = new Stack();
stack.push(10);
stack.push(20);
console.log(stack.peek()); // Output: 20
console.log(stack.pop());  // Output: 20
console.log(stack.isEmpty()); // Output: false
```

---

#### **2. Reverse a String Using a Stack**

```javascript
function reverseString(str) {
    const stack = [];
    for (let char of str) {
        stack.push(char);
    }

    let reversed = "";
    while (stack.length > 0) {
        reversed += stack.pop();
    }

    return reversed;
}

console.log(reverseString("hello")); // Output: "olleh"
```

---

#### **3. Bracket Matching**

Check if the parentheses/brackets in a string are balanced.

```javascript
function isBalanced(expression) {
    const stack = [];
    const matchingBrackets = {
        ')': '(',
        ']': '[',
        '}': '{',
    };

    for (let char of expression) {
        if (['(', '[', '{'].includes(char)) {
            stack.push(char);
        } else if ([')', ']', '}'].includes(char)) {
            if (stack.length === 0 || stack.pop() !== matchingBrackets[char]) {
                return false;
            }
        }
    }

    return stack.length === 0;
}

console.log(isBalanced("{[()]}")); // Output: true
console.log(isBalanced("{[(])}")); // Output: false
```

---

#### **4. Custom Stack Implementation (Using Linked List)**

An alternative approach using a linked list for stack implementation.

```javascript
class Node {
    constructor(value) {
        this.value = value;
        this.next = null;
    }
}

class Stack {
    constructor() {
        this.top = null;
        this.size = 0;
    }

    // Push: Add element to the stack
    push(value) {
        const newNode = new Node(value);
        newNode.next = this.top;
        this.top = newNode;
        this.size++;
    }

    // Pop: Remove the top element
    pop() {
        if (this.isEmpty()) {
            return "Underflow"; // Stack is empty
        }
        const poppedValue = this.top.value;
        this.top = this.top.next;
        this.size--;
        return poppedValue;
    }

    // Peek: Get the top element
    peek() {
        if (this.isEmpty()) {
            return "Underflow"; // Stack is empty
        }
        return this.top.value;
    }

    // IsEmpty: Check if the stack is empty
    isEmpty() {
        return this.size === 0;
    }
}

// Usage
const stack = new Stack();
stack.push(10);
stack.push(20);
console.log(stack.peek()); // Output: 20
console.log(stack.pop());  // Output: 20
console.log(stack.isEmpty()); // Output: false
```

---

### **Practical Applications of Stacks**

1. **Browser Back/Forward Navigation**  
   - Use two stacks: one for the back history and one for the forward history.

2. **Undo/Redo**  
   - Maintain two stacks: one for undo actions and one for redo actions.

3. **Expression Evaluation**  
   - Convert infix expressions to postfix or evaluate postfix expressions using a stack.

4. **DFS (Depth-First Search)**  
   - Use a stack to implement DFS in graph traversal.

5. **Call Stack in JavaScript**  
   - Manage function calls and recursion in the runtime environment.

---

### **Key Characteristics of Stacks**

1. **LIFO (Last In, First Out)** ensures operations on the topmost elements.
2. Simple implementation using arrays or linked lists.
3. Efficient for problems requiring backtracking or reversal.

---
