// Let's see what is TypeScript?


What is TypeScript?
    -> TypeScript is a superset of JavaScript that adds static typing, allowing you to catch errors early during development rather than at runtime. It was developed by Microsoft to improve JavaScript’s capabilities, especially for large-scale applications.


Key Features of TypeScript

    1.Static Typing: Unlike JavaScript, TypeScript allows you to define types for variables, functions, and properties. This helps catch type-related errors early.

Example : let message: string = "Hello, TypeScript!";

    2.Interfaces and Classes: TypeScript supports advanced features like interfaces and classes, which enhance object-oriented programming and code organization.

Example : interface Person {
    name: string;
    age: number;
}

class Employee implements Person {
    constructor(public name: string, public age: number, public designation: string) {}
}

    3.Modern JavaScript Features: TypeScript includes support for the latest JavaScript features (such as ES6/ES7) before they are widely available in browsers.

Example : const add = (a: number, b: number): number => a + b;
        