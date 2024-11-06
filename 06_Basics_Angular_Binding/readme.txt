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


5. ngStyle And ngClaass Binding

In Angular, ngClass and ngStyle are structural directives used to dynamically add or remove classes and styles to/from elements in your templates.


1. ngClass (Adding/Removing CSS Classes Dynamically)
The ngClass directive allows you to conditionally apply CSS classes to an HTML element. This is useful when you want to change the appearance of an element based on certain conditions.


Example:
html:

<div [ngClass]="{ 'active': isActive, 'highlighted': isHighlighted }">
  This div will have dynamic classes.
</div>

typeScript:

export class MyComponent {
  isActive: boolean = true;
  isHighlighted: boolean = false;
}

Explanation:

1. ngClass takes an object where the keys are class names and the values are boolean expressions.
2. If the value is true, the class will be applied to the element.

In this example:

1. If isActive is true, the active class is added to the <div>.
2. If isHighlighted is false, the highlighted class is not applied.

Other Ways to Use ngClass:

1. Array Syntax:

html:

<div [ngClass]="['class1', 'class2']">This div will have multiple classes</div>

2. String Syntax:

html:

<div [ngClass]="'active'">This div will have the 'active' class</div>


2. ngStyle (Adding/Removing Inline Styles Dynamically)
The ngStyle directive allows you to apply inline styles dynamically to an element. It is useful when you want to adjust the style properties (like width, color, etc.) of an element based on conditions in your component.


Example:

html:

<div [ngStyle]="{ 'background-color': bgColor, 'font-size': fontSize + 'px' }">
  This div has dynamic styles.
</div>

typeScript:

export class MyComponent {
  bgColor: string = 'lightblue';
  fontSize: number = 20;
}

Explanation:

1. ngStyle takes an object where the keys are CSS property names and the values are expressions that determine their values.

In this example:

1. The background-color of the div is set to lightblue.
2. The font-size is dynamically set to 20px.


Other Ways to Use ngStyle:
Object Syntax:

html:

<div [ngStyle]="styles">This div has dynamic inline styles</div>

typeScript:

export class MyComponent {
  styles = {
    'background-color': 'yellow',
    'color': 'red'
  };
}

Binding with a Variable:

html:

<div [ngStyle]="{'color': color}">Text with dynamic color</div>

typeScript:

export class MyComponent {
  color: string = 'green';
}

Summary:

ngClass is used for adding or removing CSS classes dynamically based on conditions in your component.
ngStyle is used for adding or modifying inline styles dynamically based on conditions.

Both directives allow Angular developers to bind data to the UI and make the appearance of elements more dynamic based on the component's state.



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