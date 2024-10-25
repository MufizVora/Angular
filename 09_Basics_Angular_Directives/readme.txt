// Let's see what is Directive in angular

What is Directive?
    -> Directives in Angular are a fundamental feature that allow you to manipulate the DOM in various ways. They extend the power of HTML by giving it new syntax and capabilities.Directives are classes that add additional behavior to elements in your Angular applications. Use Angular's built-in directives to manage forms, lists, styles, and what users see.There are three main types of directives:

Types of Directives
    1.Component Directives	-- Used with a template. This type of directive is the most common directive type.
    2.Attribute Directives --	Change the appearance or behavior of an element, component, or another directive.
    3.Structural Directives --	Change the DOM layout by adding and removing DOM elements.    


1. Component Directives
    -> Components are actually a type of directive with a template. They allow you to create reusable UI elements. 

Example :

Component Class (TypeScript) :

import { Component } from '@angular/core';

@Component({
  selector: 'app-my-component',
  template: `<p>Hello, I'm a component!</p>`
})
export class MyComponent {}

Template (HTML) : <app-my-component></app-my-component>


2. Structural Directives
    -> These directives alter the structure of the DOM, adding or removing elements.

1. *ngIf: Conditionally includes or excludes an element.
Example : 
<div *ngIf="isVisible">This is conditionally visible</div>

2. *ngFor: Repeats an element for each item in a collection.
Example : 
<ul>
  <li *ngFor="let item of items">{{ item }}</li>
</ul>

3. *ngSwitch: Conditionally selects one of several possible elements.
    -> *ngSwitch is a structural directive in Angular used to display one element from a list of possible elements based on a matching condition. It works similar to the switch statement in many programming languages. Here’s how it works and why it’s useful:


How It Works
*ngSwitch: The container directive that holds the value to switch on.

*ngSwitchCase: Used to define the possible cases.

*ngSwitchDefault: Defines the default case when none of the other cases match.

Example :
Let's say we want to display different messages based on a user's status:

Component Class (TypeScript) :

import { Component } from '@angular/core';

@Component({
  selector: 'app-user-status',
  templateUrl: './user-status.component.html',
  styleUrls: ['./user-status.component.css']
})
export class UserStatusComponent {
  status = 'guest';
}

Template (HTML) :

<div [ngSwitch]="status">
  <p *ngSwitchCase="'admin'">Welcome, Admin!</p>
  <p *ngSwitchCase="'user'">Welcome, User!</p>
  <p *ngSwitchCase="'guest'">Welcome, Guest!</p>
  <p *ngSwitchDefault>Unknown Status</p>
</div>

In this example:

[ngSwitch]="status": The status property determines which case to display.

*ngSwitchCase="'admin'": Displays "Welcome, Admin!" if status is 'admin'.

*ngSwitchCase="'user'": Displays "Welcome, User!" if status is 'user'.

*ngSwitchCase="'guest'": Displays "Welcome, Guest!" if status is 'guest'.

*ngSwitchDefault: Displays "Unknown Status" if status doesn’t match any case.


3. Attribute Directives
    -> These directives change the appearance or behavior of an element.

ngClass: Adds or removes a set of CSS classes.
Example :
<div [ngClass]="{ 'active': isActive }">This div can be active</div>

ngStyle: Adds or removes a set of styles.
Example :
<div [ngStyle]="{ 'color': color }">This div's color changes</div>
