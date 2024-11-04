// Let's see what is template driven form


What is Template Driven Form?
    -> A template-driven form in Angular is a way to create forms using HTML templates with Angular directives. This approach is straightforward and lets you build forms quickly without much coding.


Key Features : 
    1. Simple Syntax: You mainly use Angular directives in your HTML.
    2. Two-Way Data Binding: It automatically synchronizes the form input and the model.
    3. Easy Validation: You can easily add validation rules in your template.


Example of a Template-Driven Form :
Let’s create a simple form to collect a user’s name and email.

1. Import FormsModule: First, ensure you import FormsModule in your app module:    

import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule } from '@angular/forms';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule, FormsModule],
  bootstrap: [AppComponent],
})
export class AppModule {}


2. Create the Form in the Component: In your component, you don’t need much setup. Just define a model object.

import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
})
export class AppComponent {
  user = {
    name: '',
    email: '',
  };

  onSubmit() {
    console.log('Form submitted:', this.user);
  }
}

3. Create the Template: Now, create the form in your HTML file.

<form #userForm="ngForm" (ngSubmit)="onSubmit()">
  <div>
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" [(ngModel)]="user.name" required>
  </div>

  <div>
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" [(ngModel)]="user.email" required>
  </div>

  <button type="submit" [disabled]="!userForm.valid">Submit</button>
</form>


Explanation :
1. ngForm: The #userForm="ngForm" creates a reference to the form, allowing you to track its validity.

2. Two-Way Binding: The [(ngModel)] directive binds the input fields to the user object in your component. When the user types in the input fields, the user object updates automatically.

3. Validation: The required attribute ensures that the input fields are filled before submission. The submit button is disabled until the form is valid.

4. Submit Handler: The (ngSubmit) directive calls the onSubmit() method when the form is submitted, allowing you to handle the form data.


Summary

Template-driven forms are easy to use, especially for simple forms. You define the structure in HTML, and Angular takes care of binding and validation. This makes it a great choice for straightforward applications where you want to quickly create forms without writing too much code.