# TypeScript Learning Guide

## 1. Introduction to TypeScript:
- **What is TypeScript?**
- **Advantages of TypeScript over JavaScript.**

## 2. Setting Up Development Environment:
- **Installing Node.js and npm.**
- **Installing TypeScript using npm.**
- **Configuring TypeScript compiler options.**

## 3. Basic TypeScript Types:
- **Number, String, Boolean, Null, and Undefined types.**
- **Type inference and type annotations.**

## 4. Working with Variables and Constants:
- **Declaring variables and constants.**
- **Type annotations for variables.**

## 5. TypeScript Functions:
- **Defining functions with parameters and return types.**
- **Optional and default parameters.**
- **Arrow functions.**

## 6. TypeScript Data Structures:
- **Arrays and tuples.**
- **Type assertions.**

## 7. TypeScript Interfaces:
- **Creating and using interfaces.**
- **Optional and readonly properties.**

## 8. TypeScript Classes:
- **Class definitions and constructors.**
- **Properties, methods, and access modifiers (public, private, protected).**
- **Inheritance and extending classes.**

## 9. TypeScript Modules:
- **Organizing code with modules.**
- **Importing and exporting modules.**
- **Namespace and ambient declarations.**

## 10. TypeScript Enums:
- **Enumerated types and their usage.**

## 11. TypeScript Generics:
- **Introduction to generics.**
- **Generic functions and classes.**

## 12. TypeScript Decorators (Optional):
- **Applying decorators to classes and methods.**

## 13. Error Handling in TypeScript:
- **Handling errors using try-catch blocks.**
- **Custom error classes.**

## 14. TypeScript Tooling and Development:
- **Using TypeScript with code editors (VSCode).**
- **Debugging TypeScript code.**

## 15. Practical Exercises and Projects:
- **Implementing simple programs and exercises using TypeScript.**
- **Building a basic application using TypeScript.**


https://github.com/iamshaunjp/typescript-tutorial




# Basic Syntax in TypeScript

## 1. Variables and Data Types

TypeScript allows us to define variables with specific types, ensuring type safety at compile time.

```typescript
let age: number = 25;       // 'age' is a number
const userName: string = "Bob"; // 'userName' is a string

let message = "Hello, TypeScript!"; 
// TypeScript infers 'message' as a string based on the assigned value.
```

### Key Points:
- **Type Annotations:** Explicitly specify the type of a variable.
- **Type Inference:** TypeScript automatically infers the type based on the initial value.

---

## 2. Type Annotations

Explicitly defining types makes your code more predictable and helps avoid errors.

```typescript
let isActive: boolean = true;  // Explicitly declaring a boolean
let price: number = 99.99;     // Explicitly declaring a number
```

### Benefits of Type Annotations:
- Improved code readability.
- Reduced runtime errors by catching type mismatches during compilation.

---

## 3. Type Inference

You don’t always need to explicitly annotate types; TypeScript can infer them from the context.

```typescript
let isStudent = true;  // TypeScript infers 'boolean'
let total = 42;        // TypeScript infers 'number'
```

### When to Use:
- Use type inference for simple assignments.
- Use explicit annotations for complex structures or when clarity is important.

---

## 4. Functions

TypeScript allows you to specify types for function parameters and return values.

```typescript
function greet(name: string): string {
    return "Hello " + name;
}
```

### Optional and Default Parameters:
- **Optional Parameters:** Use `?` to mark a parameter as optional.
- **Default Parameters:** Assign default values directly in the parameter list.

Example:
```typescript
function greetUser(name: string = "Guest", age?: number): string {
    return `Hello ${name}, age ${age ?? "unknown"}`;
}
```

---

## 5. Arrays

TypeScript enforces the type of elements in an array.

```typescript
let names: string[] = ['john', 'bob', 'sam'];
names.push('man'); // Allowed
names.push(3);     // Error: Type 'number' is not assignable to type 'string'

let numbers: number[] = [10, 20, 30];
numbers.push(40);  // Allowed
numbers.push('sd'); // Error: Type 'string' is not assignable to type 'number'
```

### Mixed Arrays:
You can define arrays that hold multiple types.

```typescript
let mixed: (number | string | boolean)[] = [1, "str", true];
mixed.push('Rec', 1, true); // Allowed
mixed[0] = 4; // Allowed
```

---

## 6. Objects

Objects in TypeScript must conform to the defined structure.

```typescript
let ninja = {
    names: "Mario",
    belt: "black",
    age: 30
};

// Modifying existing properties
ninja.names = "Luigi";

// Adding new properties is not allowed
ninja.skills = "kill"; // Error: Property 'skills' does not exist on type
```

### Reassigning Objects:
You can reassign the entire object as long as it matches the original structure.

```typescript
ninja = {
    names: "Luigi",
    belt: "white",
    age: 45
}; // Allowed
```

### Key Points:
- Object properties can be modified, but adding or removing properties requires a change in the type definition.
- Use **interfaces** if you need to define reusable object structures.

---

## Additional Notes

- TypeScript enforces type rules at compile time, helping you catch errors early.
- The `strict` mode in `tsconfig.json` (enabled by default) ensures stricter type checks, enhancing type safety.
- Always use type annotations or inference to write predictable and maintainable TypeScript code.


--- 

# TypeScript Syntax: Understanding Types and Structure

## 1. Explicit Types

In TypeScript, you can explicitly declare the types of your variables to ensure that they hold the correct type of value. This helps catch errors during compilation.

```typescript
let character: string;  // 'character' must be a string
let ages: number;       // 'ages' must be a number
let isLoggedIn: boolean; // 'isLoggedIn' must be a boolean

ages = 40;  // Valid
ages = "dtr";  // Error: Type 'string' is not assignable to type 'number'
```

### Key Points:
- **Explicit types** make it clear what kind of values are expected, reducing errors.
- **Type safety** ensures variables hold only the specified types.

---

## 2. Arrays

In TypeScript, you can define arrays with specific types to ensure that all the elements inside the array are of the expected type.

### Defining Arrays with a Specific Type:
```typescript
let ninjas: string[] = [];  // 'ninjas' is an array of strings
ninjas.push("shaun");  // Allowed
ninjas.push(3);        // Error: Argument of type 'number' is not assignable to parameter of type 'string'
```

### Best Practice: Declare Arrays as Empty
It's a good practice to initialize arrays as empty to ensure type consistency throughout the program.

```typescript
let ninjas: string[] = [];  // Initialize an empty string array
ninjas.push("shaun");  // Allowed
```

---

## 3. Union Types

Union types allow a variable to hold more than one type. You can define a variable to hold a combination of types.

```typescript
let mixed: (string | number | boolean)[] = [];
mixed.push("MAN", true, 24); // Allowed
console.log(mixed);  // Output: ['MAN', true, 24]
```

### Key Points:
- **Union Types**: Let variables store multiple types, making your code more flexible.
- Always use parentheses to group multiple types when declaring union types, especially for arrays.

---

## 4. Object Types

You can define objects with specific structures by specifying the types of each property within the object.

### Using `object` Type:
```typescript
let ninjaOne: object;
ninjaOne = {
    name: "Amns",
    age: 40
};  // 'ninjaOne' can hold any object
```

### Using Type Aliases for Structured Objects:
```typescript
let ninjaTwo: {
    name: string;   // 'name' must be a string
    age: number;    // 'age' must be a number
    done: boolean;  // 'done' must be a boolean
};
ninjaTwo = {
    name: "Bob",
    age: 30,
    done: true
};  // Valid object assignment
```

### Key Points:
- **Explicit Object Types**: Helps you structure objects with defined properties and their types.
- **Type Aliases** can be used for repeated object structures.

---

## Additional Notes:

- **Array Type Safety**: Ensure the elements pushed into arrays are of the correct type.
- **Union Types**: Very useful when a value could be one of several types, such as numbers, strings, or booleans.
- **Object Structures**: Explicit object type definitions can help avoid mistakes when dealing with complex data structures.


## 5. `any` Type

In TypeScript, the `any` type allows a variable to be assigned any type of value, without TypeScript enforcing any type-checking. This can be useful in scenarios where you are unsure of the type or need flexibility. However, using `any` removes some of the benefits of TypeScript's type safety, so it should be used sparingly.

### Example with `any`:

```typescript
let age: any = 34;  // 'age' can hold any type of value
age = true;          // 'age' is now a boolean
console.log(age);    // Output: true
```

### Key Points:
- The `any` type is essentially a wildcard that disables type checking, allowing for more flexible, but less safe, code.
- It's often used when migrating JavaScript code to TypeScript or when working with dynamic content (e.g., data fetched from an API) that could be of any type.

### Caution:
- **Overuse of `any`** can defeat the purpose of TypeScript's static type checking.
- It's often better to use more specific types or `unknown` (which is safer than `any`) if you're unsure about the type.

---


# TypeScript Configuration and Code Example

## 1. Configuring `tsconfig.json`

### Folder Structure
To organize your TypeScript project, you can create a `src` folder to store your `.ts` files and a `public` folder for the compiled output. 

When you compile your TypeScript files, the output should go to the `public` folder, not the `src` folder. This can be achieved by configuring the `tsconfig.json` file properly.

### Steps to Configure `tsconfig.json`

1. **Create `src` and `public` folders**:
    - `src` will hold all your TypeScript files.
    - `public` will store the compiled `.js` files after running the TypeScript compiler.

2. **Configure `tsconfig.json`**:
    In your `tsconfig.json`, set the `rootDir` to `src` and the `outDir` to `public` to direct the compiled files to the correct folder.

Here’s an example of the `tsconfig.json` configuration:

```json
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs",
    "strict": true,
    "outDir": "./public",    // Output the compiled files to the 'public' folder
    "rootDir": "./src",      // The source folder containing the '.ts' files
  },
  "include": [
    "src/**/*"              // Only include files from the 'src' folder
  ],
  "exclude": [
    "node_modules"           // Exclude node_modules folder from compilation
  ]
}
```

This configuration ensures that:
- The source files are in the `src` folder.
- The compiled JavaScript files go to the `public` folder.
- Only files in the `src` folder are included for compilation (no files outside of `src` will be compiled).

## 2. Example Code: Avoiding Repetition with Types

Here’s an example showing how to avoid repetition when defining function signatures:

### Without Types (Repetitive Code)

```typescript
const logDetails = (user: { name: string, uid: string | number }) => {
    console.log(`${user.name} says hello`);
}

const greet = (user: { name: string, uid: string | number }) => {
    console.log(`${user.name} says hello`);
}
```

This approach works, but it’s repetitive because the type `{ name: string, uid: string | number }` is defined twice.

### Better Way: Using Types

To avoid repetition and improve code readability, we can define a reusable type for the object structure.

```typescript
// Defining a reusable type
type StringOrNum = string | number;
type ObjWithName = { name: string, uid: StringOrNum };

// Using the reusable type in functions
const logDetails = (user: ObjWithName) => {
    console.log(`${user.name} says hello`);
}

const greet = (user: ObjWithName) => {
    console.log(`${user.name} says hello`);
}
```

### Benefits:
- **Reusability**: The type `ObjWithName` can be reused in multiple functions.
- **Maintainability**: If you need to change the structure of `ObjWithName`, you only have to change it in one place, reducing the chance of errors.

## 3. Function Signatures

In TypeScript, function signatures allow you to define the types of parameters and return values explicitly. This makes your code more predictable and easier to maintain.

Here’s an example of how to define a function signature:

```typescript
type StringOrNum = string | number;

// Function with explicit signature
const greetUser: (user: { name: string, uid: StringOrNum }) => void = (user) => {
    console.log(`${user.name} says hello`);
}
```

### Explanation:
- `greetUser` is a function that takes an object with `name` (a string) and `uid` (either a string or number) as parameters and has no return value (`void`).
- The explicit signature makes it clear what type of argument the function expects, improving code readability and type safety.

## 4. Conclusion

By configuring your `tsconfig.json` file to specify the `rootDir` and `outDir`, you can organize your project better and ensure that compiled files are placed in the correct directory. Additionally, using types like `ObjWithName` helps to avoid repetition and makes your code cleaner and easier to maintain.



### Key Concepts Covered:
- **`tsconfig.json`**: How to configure the TypeScript project to manage source and output folders.
- **Function Signatures**: Demonstrating how to avoid repetition by using reusable types in function parameters.
- **`type` for Objects**: Creating reusable object types to simplify code and reduce redundancy.

---

### Function Signature

Function signatures in TypeScript define the shape of functions, specifying their parameters and return types. This is useful for enforcing type safety and making the code more predictable.

#### Example 3: Corrected Function Signature

```typescript
// Define the function signature
let logDetails: (obj: { name: string; age: number }) => void;

// Optionally, define a reusable type
type Person = { name: string; age: number };

// Assign a function matching the signature
logDetails = (ninja: Person) => {
    console.log(`${ninja.name} is ${ninja.age} years old`);
};

// Example usage
logDetails({ name: "John", age: 30 }); // Output: John is 30 years old
```

#### Explanation:
1. **Function Signature**:
   - `logDetails` is declared with a specific function signature: `(obj: { name: string; age: number }) => void`.
   - This ensures that `logDetails` accepts an object with `name` (string) and `age` (number) as parameters and does not return a value (`void`).

2. **Reusable Type**:
   - The `Person` type is defined to avoid repeating the object structure.

3. **Function Assignment**:
   - A function is assigned to `logDetails`, adhering to the declared signature.

---

### DOM Manipulation and Type Casting in TypeScript

When working with the DOM in TypeScript, you'll often need to narrow types or cast elements to a specific type (e.g., `HTMLInputElement`). TypeScript enforces stricter checks, which helps catch errors but may require explicit type assertions in some cases.

#### Example: Selecting and Manipulating DOM Elements

```typescript
// TypeScript infers this as 'HTMLElement | null'
const input = document.querySelector("input");

// Using a type assertion to specify that 'input' is an HTMLInputElement
const inputElement = document.querySelector("input") as HTMLInputElement;

// Adding an event listener with proper type checking
inputElement.addEventListener("input", () => {
    console.log(`User typed: ${inputElement.value}`);
});
```

#### Explanation:
1. **`document.querySelector`**:
   - TypeScript infers the type as `HTMLElement | null` because the element might not exist in the DOM.
   - Use a type assertion (`as HTMLInputElement`) to narrow the type.

2. **`HTMLInputElement`**:
   - When working with form inputs, explicitly casting them as `HTMLInputElement` allows access to properties like `.value`.

---

#### Example: Type Casting with Buttons

```typescript
// Selecting a button element
const button = document.querySelector("button") as HTMLButtonElement;

// Adding a click event listener
button.addEventListener("click", () => {
    console.log("Button clicked!");
});
```

---

### Tips for Type Casting:
- **Use `as` for Type Assertions**:
   - Example: `const element = document.querySelector("div") as HTMLDivElement;`
   - This helps access specific properties of the element type.

- **Non-Null Assertion**:
   - If you are certain that the element exists, you can use the non-null assertion operator (`!`).
   - Example: `const input = document.querySelector("input")!;`

- **Custom Types for Dynamic Data**:
   - Use union types or custom types for dynamic elements that could have multiple roles.


# TypeScript Basics with DOM Manipulation and Classes

### Selecting and Manipulating DOM Elements

In TypeScript, we use type assertions to ensure elements are of the expected type, enabling access to their specific properties and methods.

```typescript
// Selecting an anchor element with a non-null assertion
const anchor = document.querySelector('a')!;

console.log(anchor);        // Logs the anchor element
console.log(anchor.href);   // Logs the href property of the anchor
```

- **Non-Null Assertion (`!`)**: Ensures the compiler knows the element will exist at runtime, avoiding `null` type errors.

---

### Classes in TypeScript

Classes allow you to define the structure of objects, including properties and methods.

#### Example: `Invoice` Class

```typescript
class Invoice {
    client: string;
    details: string;
    amount: number;

    constructor(c: string, d: string, a: number) {
        this.client = c;
        this.details = d;
        this.amount = a;
    }

    format() {
        return `${this.client} owes $${this.amount} for ${this.details}`;
    }
}

const inOne = new Invoice("Maria", "work-log", 23);
const inTwo = new Invoice("Dan", "cater", 273);

let invoices: Invoice[] = [];
// invoices.push({ name: "shaun" }); // Not allowed - must match `Invoice` type

invoices.push(inOne, inTwo);

console.log(invoices);

// inOne.client = "Man"; // Possible but not recommended (client is public by default)
```

#### Explanation:
1. **Properties and Constructor**:
   - The class properties (`client`, `details`, `amount`) are defined with their types.
   - The constructor initializes these properties.

2. **Method**:
   - The `format()` method creates a string representation of the invoice.

3. **Array of Invoices**:
   - The `invoices` array is restricted to only accept objects of type `Invoice`.

---

### DOM Manipulation and Form Handling

Using type assertions, we can work effectively with form elements and ensure type safety.

#### Example: Selecting Form and Input Elements

```typescript
// Selecting the form with type assertion
const form = document.querySelector('.new-item-form') as HTMLFormElement;
console.log(form.children);

// Selecting input elements with type assertion
const type = document.querySelector('#type') as HTMLInputElement;
const tofrom = document.querySelector('#tofrom') as HTMLInputElement;
const details = document.querySelector('#details') as HTMLInputElement;
const amount = document.querySelector('#amount') as HTMLInputElement;

// Adding a form submit event listener
form.addEventListener('submit', (e: Event) => {
    e.preventDefault(); // Prevent form submission

    console.log(
        type.value,           // Logs the selected type
        tofrom.value,         // Logs the 'to/from' value
        details.value,        // Logs the details value
        amount.value,         // Logs the amount as a string
        amount.valueAsNumber  // Logs the amount as a number
    );
});
```

#### Explanation:
1. **Type Assertions**:
   - Used `as HTMLFormElement` and `as HTMLInputElement` to narrow the types of DOM elements.

2. **Event Handling**:
   - `form.addEventListener('submit', ...)` listens for the form submission.
   - `e.preventDefault()` prevents the default page refresh behavior.

3. **Accessing Input Values**:
   - `.value`: Retrieves the value as a string.
   - `.valueAsNumber`: Retrieves the numeric value, useful for number inputs.

---

### Key Takeaways:
1. Use **classes** to define the structure and behavior of objects.
2. TypeScript enforces strict typing for DOM elements, ensuring safer code.
3. Use **type assertions** to narrow types and access specific properties.
4. When working with forms, consider input types and use `.valueAsNumber` for numeric values.

```markdown
# Public, Private, and Readonly in TypeScript

In TypeScript, access modifiers like `public`, `private`, and `readonly` are used to control how properties and methods of a class can be accessed and modified. Let's explore these concepts using the `Invoice` class as an example.

---

## Original Class Definition

The `Invoice` class below has public properties by default, meaning they can be accessed and modified from anywhere.

```typescript
class Invoice {
    client: string;
    details: string;
    amount: number;

    constructor(c: string, d: string, a: number) {
        this.client = c;
        this.details = d;
        this.amount = a;
    }

    format() {
        return `${this.client} owes $${this.amount} for ${this.details}`;
    }
}

const inOne = new Invoice("Maria", "work-log", 23);
const inTwo = new Invoice("Dan", "cater", 273);

let invoices: Invoice[] = [];
invoices.push(inOne, inTwo);

console.log(invoices);
```

### Output:
```json
[
  {
    "client": "Maria",
    "details": "work-log",
    "amount": 23
  },
  {
    "client": "Dan",
    "details": "cater",
    "amount": 273
  }
]
```

---

## 1. Public Modifier

- **Default behavior in TypeScript**: Properties and methods are `public` if no modifier is specified.
- Accessible and modifiable from anywhere.

### Updated Code:
```typescript
class Invoice {
    public client: string;
    public details: string;
    public amount: number;

    constructor(c: string, d: string, a: number) {
        this.client = c;
        this.details = d;
        this.amount = a;
    }

    public format() {
        return `${this.client} owes $${this.amount} for ${this.details}`;
    }
}

const invoice = new Invoice("Anna", "consulting", 150);
console.log(invoice.client); // Accessible
invoice.client = "Updated Client"; // Modifiable
```

---

## 2. Private Modifier

- **Restricts access**: Properties or methods marked as `private` are only accessible within the class.
- Prevents modification or direct access from outside the class.

### Updated Code:
```typescript
class Invoice {
    private client: string;
    private details: string;
    private amount: number;

    constructor(c: string, d: string, a: number) {
        this.client = c;
        this.details = d;
        this.amount = a;
    }

    public format() {
        return `${this.client} owes $${this.amount} for ${this.details}`;
    }
}

const invoice = new Invoice("Anna", "consulting", 150);
// console.log(invoice.client); // Error: Property 'client' is private and only accessible within class 'Invoice'.
```

---

## 3. Readonly Modifier

- **Prevents reassignment**: Properties marked as `readonly` can only be set during initialization or within the constructor.
- They cannot be reassigned after being set.

### Updated Code:
```typescript
class Invoice {
    readonly client: string;
    public details: string;
    public amount: number;

    constructor(c: string, d: string, a: number) {
        this.client = c;
        this.details = d;
        this.amount = a;
    }

    public format() {
        return `${this.client} owes $${this.amount} for ${this.details}`;
    }
}

const invoice = new Invoice("Anna", "consulting", 150);
console.log(invoice.client); // Accessible
// invoice.client = "Updated Client"; // Error: Cannot assign to 'client' because it is a read-only property.
```

---

## Combining Modifiers

You can combine modifiers to create properties with specific behaviors. For example, a property can be `private` and `readonly`.

### Example: Private Readonly
```typescript
class Invoice {
    private readonly client: string;
    public details: string;
    public amount: number;

    constructor(c: string, d: string, a: number) {
        this.client = c;
        this.details = d;
        this.amount = a;
    }

    public format() {
        return `${this.client} owes $${this.amount} for ${this.details}`;
    }
}

const invoice = new Invoice("Anna", "consulting", 150);
// console.log(invoice.client); // Error: Property 'client' is private and only accessible within class 'Invoice'.
```

---

## Summary

| Modifier    | Accessibility                                      | Mutability          |
|-------------|----------------------------------------------------|---------------------|
| **Public**  | Accessible from anywhere                          | Can be changed      |
| **Private** | Accessible only within the class                  | Can be changed      |
| **Readonly**| Accessible from anywhere (if public)              | Cannot be changed after initialization |

Using `public`, `private`, and `readonly` effectively can help enforce encapsulation and prevent unintended modifications to your class properties.
```


Yes, that's correct! In TypeScript, you can declare and initialize class properties directly within the constructor using access modifiers like `public`, `private`, or `readonly`. If you don't use an access modifier in the constructor, the parameter will be treated as a regular local variable, and it won't automatically become a class property.

### Example: Declaring Properties in the Constructor

```typescript
class Invoice {
    constructor(
        public client: string,  // Declares and initializes a public property
        private details: string,  // Declares and initializes a private property
        readonly amount: number  // Declares and initializes a readonly property
    ) {}

    public format() {
        return `${this.client} owes $${this.amount} for ${this.details}`;
    }
}

const invoice = new Invoice("Maria", "consulting work", 150);

// Accessing properties
console.log(invoice.client); // Accessible because it's public
// console.log(invoice.details); // Error: 'details' is private
console.log(invoice.amount); // Accessible because it's readonly

// Modifying properties
invoice.client = "Anna"; // Allowed because it's public
// invoice.amount = 200; // Error: Cannot assign to 'amount' because it is a readonly property
```

### Key Points:
1. **Using Modifiers**: 
   - Without `public`, `private`, or `readonly`, the parameters in the constructor won't be automatically assigned as class properties.
   - You must explicitly use these modifiers to make the parameters class properties.

2. **Default Accessibility**:
   - If you use `public`, the property is accessible and modifiable from outside the class.
   - If you use `private`, the property is only accessible within the class.
   - If you use `readonly`, the property can only be read after initialization.

3. **Constructor Benefits**:
   - Using the constructor to declare properties is concise and eliminates redundancy (e.g., separate declarations and assignments). 

By using access modifiers in the constructor, you simplify your code while maintaining control over the accessibility and mutability of class properties.


### Interfaces in TypeScript

Interfaces in TypeScript are a powerful way to define the structure of an object, providing a contract for what properties and methods an object should have. They help ensure code consistency and improve type safety.

---

### Defining an Interface

An interface can be defined using the `interface` keyword.

```typescript
interface Person {
  name: string;
  age: number;
  speak(): void;
}
```

In this example:
- `name` and `age` are properties of type `string` and `number`, respectively.
- `speak()` is a method that returns `void`.

---

### Using an Interface

An object or class can implement an interface to ensure it adheres to the defined structure.

```typescript
const user: Person = {
  name: "Alice",
  age: 30,
  speak() {
    console.log(`${this.name} says hello!`);
  },
};

user.speak(); // Output: Alice says hello!
```

---

### Optional Properties

Properties in an interface can be optional by using the `?` modifier.

```typescript
interface Product {
  name: string;
  price: number;
  description?: string; // Optional property
}

const item: Product = {
  name: "Laptop",
  price: 1200,
};
```

---

### Readonly Properties

You can use the `readonly` modifier to make properties immutable after initialization.

```typescript
interface Car {
  readonly brand: string;
  model: string;
}

const myCar: Car = { brand: "Toyota", model: "Camry" };
// myCar.brand = "Honda"; // Error: Cannot assign to 'brand' because it is a read-only property
```

---

### Extending Interfaces

Interfaces can extend other interfaces, allowing you to build on existing structures.

```typescript
interface Animal {
  species: string;
}

interface Dog extends Animal {
  breed: string;
}

const myDog: Dog = {
  species: "Canine",
  breed: "Golden Retriever",
};
```

---

### Interface for Functions

Interfaces can describe the structure of functions.

```typescript
interface Add {
  (a: number, b: number): number;
}

const add: Add = (a, b) => a + b;
console.log(add(2, 3)); // Output: 5
```

---

### Interface vs Type

While both `interface` and `type` can define object shapes, interfaces are more extensible and better suited for defining APIs and contracts.

| Feature                | Interface      | Type Alias    |
|------------------------|----------------|---------------|
| Declaration Merging    | Yes            | No            |
| Extending              | Supported      | Supported     |
| Use for Objects/Classes| Preferred      | Supported     |
| Use for Primitives     | No             | Yes           |

<br>

In TypeScript, both `interface` and `type` are used to define the shape of objects or structures. However, they have differences in their usage and capabilities. Here's a comparison to help you understand:

---

## **1. Declaration**

### **Interface**
- Used specifically to define object shapes, contracts, or structures.
- Declared with the `interface` keyword.

```typescript
interface User {
  name: string;
  age: number;
}
```

### **Type**
- More versatile and can define **object shapes**, **unions**, **tuples**, **functions**, or **primitives**.
- Declared with the `type` keyword.

```typescript
type User = {
  name: string;
  age: number;
};
```

---

## **2. Extensibility**

### **Interface**
- Supports **declaration merging**, allowing multiple declarations with the same name to merge into a single interface.

```typescript
interface User {
  name: string;
}

interface User {
  age: number;
}

// Equivalent to:
// interface User {
//   name: string;
//   age: number;
// }
```

### **Type**
- Does **not support declaration merging**. If you declare the same `type` twice, it results in an error.
```typescript
type User = {
  name: string;
};

// Error: Duplicate identifier
type User = {
  age: number;
};
```

---

## **3. Extending**

### **Interface**
- Extended using the `extends` keyword for other interfaces.

```typescript
interface Person {
  name: string;
}

interface User extends Person {
  age: number;
}
```

### **Type**
- Extended using intersections (`&`).

```typescript
type Person = {
  name: string;
};

type User = Person & {
  age: number;
};
```

---

## **4. Function and Tuple Support**

### **Type**
- Can define **functions**, **tuples**, and **unions** directly.

```typescript
type Point = [number, number]; // Tuple
type Callback = (a: number, b: number) => number; // Function
type Status = "active" | "inactive"; // Union
```

### **Interface**
- Cannot define unions or tuples directly, but can define call signatures for functions.

```typescript
interface Callback {
  (a: number, b: number): number; // Function call signature
}
```

---

## **5. Use Cases**

| **Feature**                     | **Interface**               | **Type**                     |
|----------------------------------|-----------------------------|------------------------------|
| Object shapes                   | ✅ Yes                      | ✅ Yes                       |
| Function signatures             | ✅ Yes                      | ✅ Yes                       |
| Extending other types/interfaces| ✅ `extends`                | ✅ Intersection (`&`)       |
| Unions                          | ❌ No                       | ✅ Yes                       |
| Tuples                          | ❌ No                       | ✅ Yes                       |
| Declaration merging             | ✅ Yes                      | ❌ No                        |

---

## **When to Use What?**

### **Use `interface` when:**
1. You are defining object shapes or contracts.
2. You need to extend types through declaration merging.
3. You're working with class-based systems (e.g., using `implements` with classes).

### **Use `type` when:**
1. You need more flexibility, like defining unions, intersections, or tuples.
2. You want to use advanced type manipulation (e.g., conditional types).
3. You’re working with primitive types or aliases.

---

## **Practical Example: Combining Both**

```typescript
interface Person {
  name: string;
}

type Status = "active" | "inactive";

type User = Person & {
  age: number;
  status: Status;
};
```

Here, `interface` is used to define the base structure, while `type` is used for more advanced constructs like unions and intersections.

---

### Example: Using Interfaces with Classes

```typescript
interface Logger {
  log(message: string): void;
}

class ConsoleLogger implements Logger {
  log(message: string): void {
    console.log(message);
  }
}

const logger = new ConsoleLogger();
logger.log("Hello, Interface!"); // Output: Hello, Interface!
```

---

Interfaces are a foundational concept in TypeScript, widely used to define consistent object shapes, ensure type safety, and make code more predictable and maintainable.

### Explanation of the Code Snippets

#### 1. **Defining an Interface**

```typescript
export interface HasFormatter {
    format(): string;
}
```

- The `HasFormatter` interface ensures that any implementing class must have a `format` method that returns a string.
- Interfaces provide a contract that the implementing classes must follow.

---

#### 2. **Class `Payment` Implementing `HasFormatter`**

```typescript
export class Payment implements HasFormatter {
    constructor(
        public recipient: string,  // Accessible from outside the class
        private details: string,  // Accessible only within the class
        readonly amount: number   // Cannot be modified after initialization
    ) {}

    public format() {
        return `${this.recipient} owed $${this.amount} for ${this.details}`;
    }
}
```

- **Properties with Modifiers**:
  - `public recipient`: Accessible from outside the class.
  - `private details`: Accessible only within the class. External code cannot directly modify or access it.
  - `readonly amount`: Cannot be modified after initialization. Ensures immutability.
- **Method `format`**:
  - Implements the `format` method required by the `HasFormatter` interface.
  - Returns a formatted string describing the payment details.

---

#### 3. **Importing and Using Multiple Classes**

```typescript
import { Invoice } from "./classes/Invoices.js";
import { Payment } from "./classes/Payment.js";
import { HasFormatter } from "./interfaces/HasFormatter.js";
```

- Importing:
  - `Invoice` and `Payment` are classes.
  - `HasFormatter` is an interface.
  - These imports enable modular code, separating concerns into distinct files.

---

#### 4. **Using `HasFormatter` for Type Checking**

```typescript
let docOne: HasFormatter;
let docTwo: HasFormatter;

docOne = new Invoice("Maria", "work-log", 23);
docTwo = new Payment("John", "website design", 300);
```

- The variable `docOne` and `docTwo` are typed as `HasFormatter`. This means:
  - They can hold instances of any class that implements the `HasFormatter` interface.
  - Ensures type safety and consistency.

---

#### 5. **Using an Array of `HasFormatter`**

```typescript
let doc: HasFormatter[] = [];
doc.push(docOne);
doc.push(docTwo);

console.log(doc);
```

- **Array of `HasFormatter`**:
  - The `doc` array is typed as an array of `HasFormatter`.
  - This array can only store instances of classes that implement `HasFormatter`.
- **Usage**:
  - `docOne` (an `Invoice`) and `docTwo` (a `Payment`) are added to the array.
  - The `console.log` outputs all objects in the array, showing their `format` method implementation if accessed.

---

### **Advantages of Using Interfaces Here**

1. **Consistency**:
   - Ensures all classes implementing `HasFormatter` provide a `format` method with the same signature.

2. **Flexibility**:
   - You can add multiple types of objects (`Invoice`, `Payment`, etc.) to a single array if they implement `HasFormatter`.

3. **Type Safety**:
   - TypeScript prevents errors by ensuring only classes that adhere to the `HasFormatter` interface can be used where it's required.

---

### Example Output

```typescript
console.log(doc.map((item) => item.format()));
```

If the `doc` array contains:
- `docOne = Invoice("Maria", "work-log", 23)`
- `docTwo = Payment("John", "website design", 300)`

The output will be:
```
[
  "Maria owes $23 for work-log",
  "John owed $300 for website design"
]
```

> class like this already has HasFormatter implement

why need seperate type for doc?

The reason for creating a separate `HasFormatter` type for the `doc` variable in your code, even though your `Invoice` class already implements the `HasFormatter` interface, is to ensure **type safety** and to restrict the types that `doc` can hold.

### Why use `HasFormatter`?

- **Consistency**: Using the `HasFormatter` interface ensures that only objects that implement the `format()` method can be assigned to `doc`. This enforces consistency across the types you use in this section of the code.
- **Abstraction**: You want to work with objects that have the `format()` method, regardless of whether it's an `Invoice`, `Payment`, or potentially any other class that implements `HasFormatter`. The `HasFormatter` interface serves as an abstraction to ensure you can call `format()` without worrying about the specific class the object is from.
- **Type Safety**: By declaring `doc: HasFormatter`, you are telling TypeScript that `doc` can only hold objects that implement the `HasFormatter` interface. Without this, you might accidentally assign an object that doesn’t implement `format()`, which would cause runtime errors.

### Your Example

```typescript
form.addEventListener('submit', (e: Event) => {
    e.preventDefault();
    
    let doc: HasFormatter; // Only objects implementing HasFormatter can be assigned here
    
    if (type.value === "invoice") {
        doc = new Invoice(tofrom.value, details.value, amount.valueAsNumber);  // Invoice implements HasFormatter
    } else {
        doc = new Payment(tofrom.value, details.value, amount.valueAsNumber);  // Payment implements HasFormatter
    }

    console.log(doc);
})
```

Here, by declaring `doc` as `HasFormatter`, you're ensuring that:
- If `type.value` is `"invoice"`, you create an `Invoice` object that implements `HasFormatter`, which has a `format()` method.
- If `type.value` is `"payment"`, you create a `Payment` object, which also implements `HasFormatter`, ensuring the same `format()` method is available.

This guarantees that you can call `doc.format()` later in the code, knowing that `doc` will always be an object that has this method.

### **Benefits**:
- **Flexibility**: By using `HasFormatter` on `doc`, you can later add more classes that implement the interface (e.g., a `Receipt` class) without needing to modify your event listener logic. `doc` will be able to handle any future class that implements the `HasFormatter` interface.
- **Code Safety**: TypeScript will provide compile-time checks, ensuring that only objects implementing `HasFormatter` can be assigned to `doc`, thus avoiding runtime errors.

### Without `HasFormatter`

If you remove the `HasFormatter` type for `doc`, TypeScript won't be able to enforce that `doc` has the `format()` method, and you could run into issues later when trying to call `format()` on `doc`.

```typescript
let doc; // No type annotation, can be any type
```

This would make `doc` a generic `any` type, and TypeScript wouldn't be able to check that it has the `format()` method, potentially leading to runtime errors when trying to use `doc.format()`.

### Summary

Even though both `Invoice` and `Payment` implement `HasFormatter`, the type `HasFormatter` on `doc` is important because it ensures that only objects with the `format()` method can be assigned to `doc`, making your code safer and more maintainable.


# **Generics in TypeScript**

Generics allow you to write reusable, type-safe code by defining a placeholder (type parameter) for the type that can be used later. This makes your code more flexible while still maintaining type safety.

---

## **Why Use Generics?**

- To write reusable code.
- To ensure type safety across different data types.
- To reduce duplication.

---

## **Generic Function**

You can create a function that works with multiple data types.

```typescript
function identity<T>(value: T): T {
    return value;
}

// Example usage
console.log(identity<number>(5));  // Output: 5
console.log(identity<string>("Hello"));  // Output: Hello
```

- `<T>`: A type parameter placeholder.
- `identity<number>`: Specifies `T` as `number`.
- `identity<string>`: Specifies `T` as `string`.

---

## **Generic Classes**

Generic classes allow you to define the type of properties or methods dynamically.

```typescript
class DataStorage<T> {
    private data: T[] = [];

    addItem(item: T): void {
        this.data.push(item);
    }

    removeItem(item: T): void {
        this.data = this.data.filter((i) => i !== item);
    }

    getItems(): T[] {
        return this.data;
    }
}

// Example usage
const textStorage = new DataStorage<string>();
textStorage.addItem("Apple");
textStorage.addItem("Banana");
textStorage.removeItem("Apple");
console.log(textStorage.getItems());  // Output: ["Banana"]

const numberStorage = new DataStorage<number>();
numberStorage.addItem(10);
numberStorage.addItem(20);
console.log(numberStorage.getItems());  // Output: [10, 20]
```

---

## **Generic Interfaces**

Generic interfaces can be used to enforce a structure while allowing type flexibility.

```typescript
interface ApiResponse<T> {
    status: number;
    data: T;
}

const userResponse: ApiResponse<{ name: string; age: number }> = {
    status: 200,
    data: { name: "John", age: 25 },
};

console.log(userResponse);
```

---

## **Generic Constraints**

You can restrict the types that a generic can accept using constraints.

```typescript
function printLength<T extends { length: number }>(item: T): void {
    console.log(item.length);
}

// Example usage
printLength("Hello");  // Output: 5
printLength([1, 2, 3]);  // Output: 3

// Error: Type 'number' does not satisfy the constraint '{ length: number }'
// printLength(123);
```

- `T extends { length: number }`: Restricts `T` to types that have a `length` property.

---

## **Default Type Parameters**

You can provide a default type for a generic parameter.

```typescript
function merge<T = string, U = number>(a: T, b: U): [T, U] {
    return [a, b];
}

console.log(merge("Hello", 42));  // Output: ["Hello", 42]
console.log(merge());  // Output: ["", 0]
```

---

## **Utility with Generics**

### Generic with `Promise`

```typescript
const fetchData = async <T>(url: string): Promise<T> => {
    const response = await fetch(url);
    return response.json();
};

// Example usage
fetchData<{ name: string; age: number }>("https://api.example.com/user").then((data) => {
    console.log(data.name);
    console.log(data.age);
});
```

---

## **Advantages of Generics**

1. **Type Safety**: Errors are caught at compile-time, reducing runtime bugs.
2. **Reusability**: Write code once and use it for multiple types.
3. **Clarity**: Ensures data type consistency across the code.

---

## **Real-World Use Case**

A **Generic Stack Class**:

```typescript
class Stack<T> {
    private items: T[] = [];

    push(item: T): void {
        this.items.push(item);
    }

    pop(): T | undefined {
        return this.items.pop();
    }

    peek(): T | undefined {
        return this.items[this.items.length - 1];
    }

    isEmpty(): boolean {
        return this.items.length === 0;
    }
}

// Example usage
const numberStack = new Stack<number>();
numberStack.push(10);
numberStack.push(20);
console.log(numberStack.peek());  // Output: 20
console.log(numberStack.pop());  // Output: 20
console.log(numberStack.isEmpty());  // Output: false
```

---

Generics make TypeScript code more robust, reusable, and maintainable while keeping it type-safe.


# **Enums in TypeScript**

Enums are a way to define a set of named constants in TypeScript. They help organize your code by providing descriptive names for sets of related values. Enums improve code readability and maintainability by ensuring that related constants are grouped together and referenced meaningfully.

---

## **Why Use Enums?**

- To define a set of named constants.
- To improve code clarity by using meaningful names instead of raw values.
- To reduce errors from using magic numbers or strings.

---

## **Types of Enums**

### **1. Numeric Enums**

Numeric enums are the default in TypeScript. The values are automatically incremented starting from `0` unless specified otherwise.

```typescript
enum Direction {
    Up,    // 0
    Down,  // 1
    Left,  // 2
    Right  // 3
}

console.log(Direction.Up);    // Output: 0
console.log(Direction.Right); // Output: 3
```

You can customize the starting value:

```typescript
enum Direction {
    Up = 1,
    Down,    // 2
    Left,    // 3
    Right    // 4
}
```

---

### **2. String Enums**

String enums allow you to associate custom string values with the names.

```typescript
enum Status {
    Active = "ACTIVE",
    Inactive = "INACTIVE",
    Pending = "PENDING"
}

console.log(Status.Active);  // Output: "ACTIVE"
```

---

### **3. Heterogeneous Enums**

Heterogeneous enums combine both string and numeric values, but this approach is generally discouraged due to potential confusion.

```typescript
enum Mixed {
    No = 0,
    Yes = "YES"
}

console.log(Mixed.No);  // Output: 0
console.log(Mixed.Yes); // Output: "YES"
```

---

## **Reverse Mapping in Numeric Enums**

In numeric enums, TypeScript provides a reverse mapping. You can use the value to get the key.

```typescript
enum Direction {
    Up = 1,
    Down,
    Left,
    Right
}

console.log(Direction[1]); // Output: "Up"
```

> **Note:** Reverse mapping is not available for string enums.

---

## **Using Enums**

### **Enums as Function Parameters**

Enums can be used to ensure only valid values are passed to a function.

```typescript
enum LogLevel {
    Error,
    Warn,
    Info,
    Debug
}

function logMessage(level: LogLevel, message: string): void {
    console.log(`[${LogLevel[level]}]: ${message}`);
}

logMessage(LogLevel.Warn, "This is a warning."); // Output: "[Warn]: This is a warning."
```

---

### **Enums in Conditional Statements**

Enums can make conditional logic more readable.

```typescript
enum UserRole {
    Admin,
    User,
    Guest
}

function checkPermission(role: UserRole): void {
    if (role === UserRole.Admin) {
        console.log("Full access granted.");
    } else if (role === UserRole.User) {
        console.log("Limited access granted.");
    } else {
        console.log("No access granted.");
    }
}

checkPermission(UserRole.User); // Output: "Limited access granted."
```

---

## **Computed and Constant Members**

Enums can have both constant and computed values.

```typescript
enum Colors {
    Red,                // Constant (0)
    Green = 5,          // Constant (5)
    Blue = 5 + 3,       // Computed (8)
    Yellow = "YELLOW"   // String value
}

console.log(Colors.Blue);    // Output: 8
console.log(Colors.Yellow);  // Output: "YELLOW"
```

---

## **Enums with Type Annotations**

Enums can be used to enforce type safety.

```typescript
enum Days {
    Monday,
    Tuesday,
    Wednesday
}

let today: Days = Days.Monday;
// today = 3; // Error: Type '3' is not assignable to type 'Days'
```

---

## **Advantages of Enums**

1. **Readability**: Provides descriptive names instead of raw numbers or strings.
2. **Maintainability**: Changes in enum values propagate automatically.
3. **Type Safety**: Ensures only valid values are used.
4. **Convenience**: Reverse mapping for numeric enums makes debugging easier.

---

## **When Not to Use Enums**

- If you’re working in a codebase shared with JavaScript (use `const` objects instead for compatibility).
- When simple `union` types or `literal` types can achieve the same goal with less overhead.

```typescript
// Alternative using union types
type Direction = "Up" | "Down" | "Left" | "Right";

let move: Direction = "Up";  // Valid
// move = "Forward"; // Error: Type '"Forward"' is not assignable to type 'Direction'
```


Enums in TypeScript are a powerful tool for organizing related constants. Use them judiciously to improve your code’s clarity, maintainability, and type safety.

---

# Tuples in TypeScript

Tuples in TypeScript are a special kind of array that allow you to define the **types** and **order** of elements. Unlike regular arrays, where all elements must be of the same type, tuples let you define a fixed sequence of types.

---

## **Features of Tuples**
1. **Fixed Length**: The number of elements in a tuple is fixed.
2. **Typed Elements**: Each position in a tuple has a specific type.
3. **Order Matters**: The order of elements in a tuple must match the defined types.

---

## **Syntax**
```typescript
let tupleName: [type1, type2, ...];
```

---

## **Examples**

### 1. **Simple Tuple**
```typescript
let user: [string, number];
user = ["Alice", 30]; // ✅ Correct
// user = [30, "Alice"]; // ❌ Error: Types are out of order
```

### 2. **Accessing Tuple Elements**
You can access tuple elements using array indexing:
```typescript
console.log(user[0]); // "Alice"
console.log(user[1]); // 30
```

### 3. **Optional Elements**
Tuples can have optional elements using `?`:
```typescript
let user: [string, number?];
user = ["Alice"]; // ✅ Optional second element
```

### 4. **Rest Elements**
Tuples can have a rest element to allow flexibility:
```typescript
let colors: [string, ...string[]];
colors = ["red", "green", "blue"]; // ✅ Additional elements allowed
```

---

## **Tuples with Destructuring**
You can destructure tuples into individual variables:
```typescript
let person: [string, number] = ["Bob", 40];
let [name, age] = person;

console.log(name); // "Bob"
console.log(age);  // 40
```

---

## **Real-World Use Cases**

1. **Returning Multiple Values from a Function**
   ```typescript
   function getUser(): [string, number] {
       return ["Alice", 30];
   }
   const [name, age] = getUser();
   console.log(name, age); // "Alice", 30
   ```

2. **Key-Value Pairs**
   ```typescript
   let keyValue: [string, string];
   keyValue = ["username", "Alice"];
   ```

3. **Event Handlers**
   ```typescript
   let eventData: [string, Date];
   eventData = ["click", new Date()];
   ```

---

## **Common Operations**

### Updating Elements
```typescript
let user: [string, number] = ["Alice", 30];
user[1] = 31; // ✅ Update is allowed
```

### Pushing to Tuples
Tuples are arrays under the hood, so you can push new elements, but TypeScript won’t enforce type checking for elements beyond the fixed length:
```typescript
let user: [string, number] = ["Alice", 30];
user.push("extra"); // ✅ Allowed, but not part of the tuple definition
console.log(user); // ["Alice", 30, "extra"]
```

---

## **Advantages of Tuples**
1. **Strict Type Checking**: Ensures the correct type and order of elements.
2. **Improved Readability**: Makes the intent of data structures clearer.
3. **Destructuring Support**: Works seamlessly with ES6 destructuring.

---

## **Limitations of Tuples**
1. **Limited Beyond Fixed Length**: TypeScript can’t enforce types for elements added beyond the defined length.
2. **Less Flexible Than Arrays**: Tuples have fixed types and order, so they are less dynamic.

---

## **Summary**
Tuples in TypeScript provide a powerful way to define arrays with fixed types and order. They are especially useful when working with structured data, such as function return values or key-value pairs. By using tuples, you can improve type safety and readability in your code.


TypeScript enforces a set of strict rules to ensure type safety and better code quality. Here's a list of TypeScript's strict features and their explanations, with examples where necessary:

---

## **1. Strict Type Checking**
### **Description**: Variables must match the declared type.
```typescript
let name: string = "John";
// name = 123; // Error: Type 'number' is not assignable to type 'string'.
```

---

## **2. Strict Null and Undefined Checking (`strictNullChecks`)**
### **Description**: Prevents assigning `null` or `undefined` to variables unless explicitly allowed.
```typescript
let name: string = "John";
// name = null; // Error: Type 'null' is not assignable to type 'string'.

let optionalName: string | null = "John";
optionalName = null; // Allowed because of union type.
```

---

## **3. Strict Function Parameter Types**
### **Description**: Every parameter in a function must match its type.
```typescript
function greet(name: string) {
  console.log(`Hello, ${name}`);
}
// greet(123); // Error: Argument of type 'number' is not assignable to parameter of type 'string'.
```

---

## **4. Strict Return Types**
### **Description**: Functions must return values matching their declared type.
```typescript
function add(a: number, b: number): number {
  return a + b;
  // return "sum"; // Error: Type 'string' is not assignable to type 'number'.
}
```

---

## **5. Excess Property Checks**
### **Description**: Objects can only have the declared properties, unless explicitly allowed.
```typescript
interface User {
  name: string;
  age: number;
}

const user: User = { name: "John", age: 30 };
// const user: User = { name: "John", age: 30, role: "admin" }; // Error: Object literal may only specify known properties.
```

---

## **6. Strict `this` Context**
### **Description**: Ensures correct usage of `this` in functions.
```typescript
class Person {
  name = "John";

  greet() {
    console.log(`Hello, ${this.name}`);
  }
}

const person = new Person();
const greet = person.greet;
// greet(); // Error: 'this' is undefined in strict mode.
```

---

## **7. Strict Function Call Signatures**
### **Description**: Function arguments must match the declared type, both in number and type.
```typescript
function multiply(a: number, b: number) {
  return a * b;
}

// multiply(2); // Error: Expected 2 arguments but got 1.
```

---

## **8. Strict Index Signature Types**
### **Description**: Prevents assigning non-matching keys or values to objects with index signatures.
```typescript
interface Dictionary {
  [key: string]: string;
}

const dict: Dictionary = {
  key1: "value1",
  key2: "value2",
  // key3: 123 // Error: Type 'number' is not assignable to type 'string'.
};
```

---

## **9. `Readonly` Property Enforcement**
### **Description**: Ensures that `readonly` properties cannot be modified after initialization.
```typescript
class Car {
  readonly brand: string;

  constructor(brand: string) {
    this.brand = brand;
  }

  changeBrand(newBrand: string) {
    // this.brand = newBrand; // Error: Cannot assign to 'brand' because it is a read-only property.
  }
}
```

---

## **10. Enforcing Enum Exhaustiveness**
### **Description**: All cases of an enum must be handled.
```typescript
enum Status {
  Active,
  Inactive,
}

function handleStatus(status: Status) {
  switch (status) {
    case Status.Active:
      console.log("Active");
      break;
    case Status.Inactive:
      console.log("Inactive");
      break;
    // No default case needed because all enums are handled.
  }
}
```

---

## **11. Type Assertions Are Checked**
### **Description**: Type assertions (`as`) are limited to compatible types.
```typescript
let value: unknown = "hello";
let str: string = value as string;
// let num: number = value as number; // Error: Conversion from 'string' to 'number' may be an issue.
```

---

## **12. `never` Type Enforcement**
### **Description**: Ensures that functions with the `never` return type cannot return any value.
```typescript
function throwError(message: string): never {
  throw new Error(message);
}
```

---

## **13. Strict Type Aliases**
### **Description**: Type aliases cannot be mixed unless explicitly allowed.
```typescript
type ID = string | number;

let userId: ID = 123;
// userId = true; // Error: Type 'boolean' is not assignable to type 'ID'.
```

---

## **14. Generics Type Safety**
### **Description**: Generics enforce type consistency across usages.
```typescript
function identity<T>(value: T): T {
  return value;
}

identity<number>(123); // OK
// identity<number>("hello"); // Error: Argument of type 'string' is not assignable to parameter of type 'number'.
```

---

## **15. No Implicit `any`**
### **Description**: Variables or function parameters without types default to `any` only if explicitly allowed.
```typescript
// Without strict mode:
let data; // Implicitly 'any'
data = "hello"; // Allowed

// With strict mode:
// let data; // Error: Variable 'data' implicitly has an 'any' type.
```

---

## **16. Implicit `this` Typing**
### **Description**: Ensures methods have a properly defined `this` context.
```typescript
interface User {
  name: string;
  greet(): void;
}

const user: User = {
  name: "John",
  greet() {
    console.log(this.name); // 'this' is correctly inferred as 'User'.
  }
};
```

---

## **17. Union and Intersection Types Strictness**
### **Description**: Ensures that types in unions and intersections are correctly handled.
```typescript
type A = { x: number };
type B = { y: string };
type C = A & B;

const obj: C = { x: 123, y: "hello" };
// obj.z = true; // Error: Object literal may only specify known properties.
```

---

These strict checks ensure that TypeScript provides a robust and predictable development experience, reducing bugs and enhancing code quality.