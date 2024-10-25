// Let's see what is data binding in Angular

1 Data binding
    -> Data binding in AngularJS is the synchronization between the model and the view. When data in the model changes, the view reflects the change, and when data in the view changes, the model is updated as well.


Types of data binding
    -> 1 One-way data binding
    2 Two-way data binding  


1 One-way data binding
    -> One-way data binding is a simple type of data binding where you're allowed to manipulate the views through the models. This implies, making changes to the Typescript code will be reflected in the corresponding HTML.

    In Angular, One-way data binding is achieved through:

    1. Interpolation or String Concatination
    2. Property binding
    3. Event binding
    4. Class and style binding


Let's see the types of one-way data binding    

1. Interpolation or String Concatination
    -> Interpolation and string concatenation are techniques in Angular for binding data from your component class to your HTML template.

=> Interpolation
Interpolation uses double curly braces {{ }} to embed expressions and variables directly in your HTML. It’s the most common form of data binding in Angular. 

Example : export class MyComponent {
  title = 'Hello, Angular!';
}
<p>{{ title }}</p>

Output: <p>Hello, Angular!</p>

=> String Concatenation
String concatenation is another way to bind data to the template. You use the + operator to combine strings with variables or expressions.

Example : export class MyComponent {
  firstName = 'John';
  lastName = 'Doe';
}
<p>{{ 'Hello, ' + firstName + ' ' + lastName + '!' }}</p>

Output: <p>Hello, John Doe!</p>


2. Property binding
    -> Property data binding in Angular is a powerful technique that allows you to dynamically update your HTML properties with values from your component class. It's done using square brackets [] around the property you want to bind to.

How It Works
    With property binding, you can set the property of an element to the value of an expression in your component. This keeps your view updated automatically when the component's data changes.

Example : 
Here's a simple example using an img element to demonstrate property binding:    
Component Class (TypeScript) :

import { Component } from '@angular/core';

@Component({
  selector: 'app-image',
  templateUrl: './image.component.html',
  styleUrls: ['./image.component.css']
})
export class ImageComponent {
  imageUrl = 'https://via.placeholder.com/150';
}

Template HTML :
<img [src]="imageUrl" alt="Image">

In this example:

[src]: Binds the src attribute of the img element to the imageUrl property in the component.

imageUrl: Holds the URL of the image to be displayed.


3. Event binding
    -> Event data binding in Angular allows you to listen for and respond to user actions in the DOM. It’s done using parentheses () around the event you want to bind to, connecting your component’s logic to the user interface.

How It Works
    With event binding, you can bind an event, such as click, input, or submit, to a method in your component. This method gets executed whenever the event occurs.

Example
Here’s a simple example using a button click event:

Component Class (TypeScript) :

import { Component } from '@angular/core';

@Component({
  selector: 'app-clicker',
  templateUrl: './clicker.component.html',
  styleUrls: ['./clicker.component.css']
})
export class ClickerComponent {
  count = 0;

  increment() {
    this.count++;
  }
}

Template HTML :

<button (click)="increment()">Click me!</button>
<p>Button clicked {{ count }} times.</p>

In this example:

(click): Binds the click event of the button to the increment method in the component.

increment(): Method defined in the component that increments the count property.

count: Property in the component that tracks the number of button clicks.


4. Class and style binding

1. Class Binding 
    -> Class binding allows you to add or remove classes to HTML elements dynamically based on your component’s data or state.

Example :
Component Class (TypeScript) :

import { Component } from '@angular/core';

@Component({
  selector: 'app-my-component',
  templateUrl: './my-component.component.html',
  styleUrls: ['./my-component.component.css']
})
export class MyComponent {
  isActive = true;
}

Template (HTML) : 

<p [class.active]="isActive">This text will be styled based on isActive.</p>

Styles (CSS) : 

.active {
  color: green;
  font-weight: bold;
}


2. Style Binding
    -> Style binding allows you to set inline CSS styles dynamically based on your component’s data or state.

Example :
Component Class (TypeScript) :

import { Component } from '@angular/core';

@Component({
  selector: 'app-my-component',
  templateUrl: './my-component.component.html',
  styleUrls: ['./my-component.component.css']
})
export class MyComponent {
  fontSize = '20px';
}

Template (HTML) :

<p [style.font-size]="fontSize">This text will be styled based on fontSize.</p>



2 Two-way data binding
    -> Two-way data binding in Angular is a powerful feature that allows for automatic synchronization of data between the model (component class) and the view (template). It ensures that any change in the model updates the view and vice versa, keeping both in sync effortlessly.

    The syntax of two way binding is – [( )}. As you can see, it is a combination of the property binding syntax i.e. [ ] and the event binding syntax ( ). According to Angular, this syntax resembles “Banana in a Box”.

How It Works
Two-way binding is achieved using the [(ngModel)] directive in Angular. This combines both property binding and event binding in a single directive.

Example :
Let's go through an example where we bind a text input to a component property:

Component Class (TypeScript) :

import { Component } from '@angular/core';

@Component({
  selector: 'app-two-way-binding',
  templateUrl: './two-way-binding.component.html',
  styleUrls: ['./two-way-binding.component.css']
})
export class TwoWayBindingComponent {
  name: string = '';
}

Template (HTML) :

<input [(ngModel)]="name" placeholder="Enter your name">
<p>Your name is: {{ name }}</p>

In this example:

[(ngModel)]: This directive binds the input element to the name property in the component. The [(...)] syntax is shorthand for combining property binding ([ngModel]) and event binding ((ngModelChange)).

name: This property holds the value entered in the input field.

<p>...</p>: Displays the current value of the name property, automatically updating as the input changes.