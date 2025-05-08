What Is Type Inference in TypeScript and Why Is It Helpful?

What Is Type Inference?

Type inference is the process by which TypeScript automatically deduces the type of a variable based on its value or the context in which it's used.

For example:
let message = "Hello, TypeScript!";

In the above code, TypeScript infers that message is of type string because it’s initialized with a string value. You don’t have to explicitly declare let message: string = “Something”


How Type Inference Works:

TypeScript uses inference in several scenarios:

Variable Declarations:

let age = 30; // inferred as number

Function Return Types:

function multiply(a: number, b: number) {
 return a * b; // inferred as number
}

Array and Object Literals:

let colors = ["red", "green", "blue"]; // inferred as string[]

Contextual Typing:

When a variable’s usage in a certain context allows TypeScript to infer its type.

window.addEventListener("click", (event) => {
  // event is inferred as MouseEvent
});


Why Is Type Inference Helpful?

1.	Reduces Boilerplate:
Developers don’t need to write out obvious types, leading to cleaner and more concise code.
2.	Maintains Strong Typing:
Even without explicit annotations, the code is still type-checked. This helps catch errors early.
3.	Improves Developer Productivity:
Inferred types enhance IDE features like autocomplete and inline documentation without requiring manual type declarations.
4.	Encourages Readability:
Code becomes easier to read and maintain, as unnecessary type annotations can clutter simple logic.
5.	Balances Flexibility and Safety:
TypeScript provides the flexibility of dynamic JavaScript with the safety net of static typing through inference.



.....................
.....................



Explain the difference between any, unknown, and never types in TypeScript:

any:
The any type in TypeScript essentially turns off type checking for a variable. It can hold any kind of value, and you can perform any operation on it.

Example with any

let something: any = true;

something = "string"; // no error as it can be "any" type

Math.round(something); // no error as it can be "any" type

Example without any

let something = true;

something = "string"; // Error: Type 'string' is not assignable to type 'boolean'.

Math.round(something); // Error: Argument of type 'boolean' is not assignable to parameter of type 'number'.


unknown:

unknown is Introduced to provide a safer alternative to any,unknown represents a value that could be anything, just like any. However, the key difference lies in how you can interact with it.
You cannot perform any operations on an unknown value without first performing a type check or assertion. This forces you to be explicit about the type you expect before you can work with the value.

Example:

let Something: unknown = "World";

Something = 456;

Something = { message: "A message" };

// Error: Object is of type 'unknown'.(2571)
// console.log(Something.toUpperCase());

if (typeof Something === 'string') {
  	console.log(Something.toUpperCase()); // Safe to call toUpperCase() here
} 
else if (typeof Something === 'number') {
  	console.log(Something + 10);
} 
else if (typeof Something === 'object' && Something !== null && 'message' in Something) {
  	console.log(Something.message);
}



never:

never effectively throws an error whenever it is defined. never is rarely used, its primary use is in advanced generics. 

let something: never = true; 
// Error: Type 'boolean' is not assignable to type 'never'.

