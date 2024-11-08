// Let's see what is components communication


What is Components Communication?
    -> In Angular, component communication refers to how different components interact with each other. Since Angular applications are often made up of multiple components, it’s important to understand how to share data and trigger actions across them. There are several ways components can communicate:



1. Parent to Child Communication

This is done using Input properties. A parent component can pass data to a child component through property binding.    

Example:

Parent Component:

import { Component } from '@angular/core';

@Component({
  selector: 'app-parent',
  templateUrl: './parent.component.html'  // Parent's HTML template
})
export class ParentComponent {
  // Data to pass to child component
  parentData = 'Hello from Parent Component!';
}

Parent Component HTML (parent.component.html):

<div>
  <h1>Parent Component</h1>
  <!-- Passing data to the child component via input binding -->
  <app-child [data]="parentData"></app-child>
</div>

Explanation:
The parentData variable in the ParentComponent holds the string "Hello from Parent Component!".
The [data]="parentData" binding passes this string down to the data property of the ChildComponent.

2. Child Component: Receiving Data from Parent Component
In the child component, you define an @Input() property that will accept data from the parent component.

import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html'  // Child's HTML template
})
export class ChildComponent {
  // Declare an input property to receive data from the parent
  @Input() data: string | undefined;
}

Child Component HTML (child.component.html):

<div>
  <h2>Child Component</h2>
  <!-- Displaying the data received from the parent -->
  <p>{{ data }}</p>
</div>

Explanation:
The @Input() decorator allows the child component to receive the data passed from the parent component.
The data property in the ChildComponent holds the value passed from the parent (parentData).
The HTML template of the child component uses Angular's interpolation ({{ data }}) to display the data received from the parent.

2. Child to Parent Communication

This is done using Output properties and EventEmitter. A child component can send data back to a parent component when an event occurs.

Example:

Child Component:

import { Component, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `<button (click)="sendData()">Send Data to Parent</button>`,
})
export class ChildComponent {
  @Output() dataEmitter = new EventEmitter<string>();

  sendData() {
    this.dataEmitter.emit('Hello from Child!');
  }
}

Parent Component:

import { Component } from '@angular/core';

@Component({
  selector: 'app-parent',
  template: `
    <h1>Parent Component</h1>
    <app-child (dataEmitter)="receiveData($event)"></app-child>
    <p>Data from Child: {{ childData }}</p>
  `,
})
export class ParentComponent {
  childData: string;

  receiveData(data: string) {
    this.childData = data;
  }
}

Explanation:

The child component has an @Output() property that emits data using EventEmitter.
The parent component listens for the emitted event with (dataEmitter)="receiveData($event)", and when the event occurs, it calls receiveData() to capture the data.


Summary
Component communication in Angular can be done in several ways:

Parent to Child: Using @Input() to pass data.
Child to Parent: Using @Output() and EventEmitter to emit events.