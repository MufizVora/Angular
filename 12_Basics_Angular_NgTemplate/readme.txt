// Let's understand what is Ng Template?


What is Ng-Template?
    -> ng-template in Angular is a directive that allows you to define a template for structural directives, dynamic views, and reusable templates. It doesn’t render anything to the DOM by itself but serves as a placeholder for content that will be rendered conditionally.

Example :
Let's use ng-template to create a dynamic view based on a condition.

Component Class (TypeScript) :

import { Component } from '@angular/core';

@Component({
  selector: 'app-ng-template-example',
  templateUrl: './ng-template-example.component.html'
})
export class NgTemplateExampleComponent {
  isLoggedIn = false;
}

Template (HTML) :

<button (click)="isLoggedIn = !isLoggedIn">
  Toggle Login Status
</button>

<ng-container *ngIf="isLoggedIn; else notLoggedIn">
  <p>Welcome back, user!</p>
</ng-container>

<ng-template #notLoggedIn>
  <p>Please log in to continue.</p>
</ng-template>

Explanation :
<button (click)="isLoggedIn = !isLoggedIn">: A button to toggle the isLoggedIn state.

<ng-container *ngIf="isLoggedIn; else notLoggedIn">: If isLoggedIn is true, the content inside ng-container is rendered.

<ng-template #notLoggedIn>: Defines a template with the #notLoggedIn reference. This content is displayed when isLoggedIn is false.

Key Points
Placeholder: ng-template acts as a placeholder for content that will be conditionally rendered.

Reusability: Allows you to create reusable templates for different parts of your application.

No Extra Markup: Prevents adding unnecessary elements to the DOM, keeping your HTML clean and efficient.

ng-template is a powerful tool for creating dynamic and reusable templates, making your Angular applications more flexible and maintainable. Handy, right?