// Let's understand what is Ng-Container?


What is Ng-Container?
    -> ng-container is an Angular directive used as a grouping element in your template without adding extra DOM elements. It helps in situations where you want to apply structural directives (like ngIf, ngFor, etc.) but don't want to introduce additional elements to your layout.


How It Works
    ng-container itself doesn’t render anything in the DOM. Instead, it acts as a placeholder for directives and helps keep your markup clean.

Example : 
Here's a scenario where you want to conditionally render elements without wrapping them in an additional div or span.    

Template (HTML) :

<ng-container *ngIf="isLoggedIn; else notLoggedIn">
  <p>Welcome back, user!</p>
</ng-container>

<ng-template #notLoggedIn>
  <p>Please log in to continue.</p>
</ng-template>


Explanation : 

<ng-container *ngIf="isLoggedIn; else notLoggedIn">: If isLoggedIn is true, it displays the content inside ng-container. Otherwise, it renders the template referenced by #notLoggedIn.

<ng-template #notLoggedIn>: Defines a template that gets displayed when isLoggedIn is false.

Usage in Component Class : 

Make sure you have the isLoggedIn property in your component:

import { Component } from '@angular/core';

@Component({
  selector: 'app-login-status',
  templateUrl: './login-status.component.html'
})
export class LoginStatusComponent {
  isLoggedIn = false;
}

Why Use ng-container?
Avoid Extra Markup: Prevents adding unnecessary elements to the DOM, keeping your HTML clean and lightweight.

Structural Directives: Allows the use of structural directives without altering the DOM structure.

Template Organization: Helps in organizing conditional rendering and complex templates more elegantly.

ng-container is a neat tool to have in your Angular toolkit for managing clean, efficient templates. Pretty neat, right?