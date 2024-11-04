// Let's understand what is interface in angular?


What is Interface?
    -> In Angular (and TypeScript), an interface is a way to define the structure of an object. It helps ensure that objects have specific properties and types, making your code more predictable and easier to understand.


Example of an Interface
Let’s say we want to represent a simple User object. We can define an interface for it like this:

Example :

interface User {
  id: number;
  name: string;
  email: string;
}

Explanation :
1. Structure: The User interface specifies that any object of type User must have:

id: a number
name: a string
email: a string

2. Usage: You can then use this interface to ensure that objects you create follow this structure:

const user1: User = {
  id: 1,
  name: "Alice",
  email: "alice@example.com"
};

const user2: User = {
  id: 2,
  name: "Bob",
  email: "bob@example.com"
};


If you try to create a User without all required properties, TypeScript will give you an error:

const user3: User = {
  id: 3,
  // name is missing
  email: "charlie@example.com" // Error: Property 'name' is missing
};


Why Use Interfaces?

Type Safety: They help catch errors at compile time rather than at runtime.
Clarity: They make your code easier to understand and maintain.
Code Reusability: You can define the interface once and reuse it across your application.