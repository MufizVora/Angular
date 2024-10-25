// Let's see what is component

What is component?
    -> In Angular, a component is a fundamental building block for creating user interfaces. Components encapsulate the logic, data, and views, allowing you to build modular, reusable, and maintainable code.


Key Parts of a Component:
    1.Class: Defines the logic and data. This is where you manage state, handle user inputs, and call services.    

Example : import { Component } from '@angular/core';

@Component({
  selector: 'app-my-component',
  templateUrl: './my-component.component.html',
  styleUrls: ['./my-component.component.css']
})
// This is called class
export class MyComponent {
  title = 'Hello, Angular!';
}

    2.Template: Defines the HTML structure and binds it with data from the class using Angular's data-binding syntax.

Example: <h1>{{ title }}</h1>

    3.Styles: Defines the CSS styles for the component, scoped to only affect this component.

Example: h1 {
  color: blue;
}        