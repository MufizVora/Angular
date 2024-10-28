// Let's understand what are Pipes in angular?


What is Pipes?
    -> In Angular, pipes are a way to transform data in templates. They allow you to format or modify data before displaying it in your application. Pipes are very useful for tasks like formatting dates, currency, or filtering lists.


Key Points:
    1. Transform Data: Pipes take in data as input and return a modified version of that data.
    2. Used in Templates: You use pipes in your HTML templates with the pipe (|) symbol.    


In Angular, there are two main types of pipes: built-in pipes and custom pipes. Let’s explore both with examples.


1. Built-in Pipes
Angular provides several built-in pipes that you can use to transform data in your templates. Here are some commonly used built-in pipes:

a. Date Pipe
Formats dates based on locale.
Example : 
    <p>Today’s date: {{ today | date:'fullDate' }}</p>

b. Currency Pipe
Formats a number as currency.
Example:
    <p>Price: {{ price | currency:'USD' }}</p>

c. UpperCase Pipe
Converts a string to uppercase.
Example:
    <p>{{ name | uppercase }}</p>



2. Custom Pipes
If you need a specific transformation that isn’t covered by the built-in pipes, you can create your own custom pipes. Here’s how to create one:


Creating a Custom Pipe
    1. Generate a Pipe: Use the Angular CLI to generate a new pipe.
    Here, is the command to create custom pipe : ng generate pipe myCustomPipe


2. Implement the Pipe: Open the generated file and implement the pipe logic.
Example:
// my-custom-pipe.pipe.ts
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'exclamation'
})
export class ExclamationPipe implements PipeTransform {
  transform(value: string): string {
    return value + '!';
  }
}
In this example, the ExclamationPipe appends an exclamation mark to any string.

You can use your custom pipe in a template like this:
Example: 
    <p>{{ 'Hello World' | exclamation }}</p>

Output:
    Hello World!
