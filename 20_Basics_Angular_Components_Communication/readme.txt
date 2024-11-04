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
  template: `
    <h1>Parent Component</h1>
    <app-child [childData]="parentData"></app-child>
  `,
})
export class ParentComponent {
  parentData = 'Hello from Parent!';
}

Child Component:

import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `<p>Child Component: {{ childData }}</p>`,
})
export class ChildComponent {
  @Input() childData: string;
}

Explanation:

The parent component defines a property parentData and passes it to the child component using [childData]="parentData".
The child component receives this data with the @Input() decorator and can use it in its template.


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