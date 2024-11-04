// Let's see what is reactive form


What is Reactive Form?
    -> A reactive form in Angular is a way to create forms using a more programmatic approach. Instead of defining the form directly in the template, you build it in your component class using FormGroup and FormControl. This approach offers greater flexibility and is well-suited for complex forms.


Key Features
1. Explicit Management: You have full control over the form's structure and validation.
2. Dynamic Forms: Easily add or remove controls based on user actions.
3. Reactive Patterns: Changes in the form state can be observed and reacted to in real-time.    


Example of a Reactive Form :

1. Import ReactiveFormsModule: First, import ReactiveFormsModule in your app module:

import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { ReactiveFormsModule } from '@angular/forms';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule, ReactiveFormsModule],
  bootstrap: [AppComponent],
})
export class AppModule {}

2. Create the Form in the Component: In your component, define the form using FormGroup and FormControl.

import { Component, OnInit } from '@angular/core';
import { FormGroup, FormControl, Validators } from '@angular/forms';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
})
export class AppComponent implements OnInit {
  userForm: FormGroup;

  ngOnInit() {
    this.userForm = new FormGroup({
      name: new FormControl('', [Validators.required]),
      email: new FormControl('', [Validators.required, Validators.email]),
    });
  }

  onSubmit() {
    console.log('Form submitted:', this.userForm.value);
  }
}


3. Create the Template: Now, create the form in your HTML file.

<form [formGroup]="userForm" (ngSubmit)="onSubmit()">
  <div>
    <label for="name">Name:</label>
    <input id="name" formControlName="name">
    <div *ngIf="userForm.get('name')?.invalid && userForm.get('name')?.touched">
      Name is required.
    </div>
  </div>

  <div>
    <label for="email">Email:</label>
    <input id="email" formControlName="email">
    <div *ngIf="userForm.get('email')?.invalid && userForm.get('email')?.touched">
      Valid email is required.
    </div>
  </div>

  <button type="submit" [disabled]="userForm.invalid">Submit</button>
</form>


Explanation
1. FormGroup: In the component, we create a FormGroup called userForm that groups related controls (in this case, name and email).

2. FormControl: Each form control is defined using FormControl, where we can specify initial values and validation rules (like Validators.required).

3. Binding in Template: The template uses [formGroup]="userForm" to bind the form to the userForm in the component. Each input uses formControlName to link to its corresponding control.

4. Validation Messages: We show validation messages conditionally based on the state of the controls, ensuring users receive feedback.

5. Submit Handler: The (ngSubmit) directive calls the onSubmit() method when the form is submitted, allowing you to access the form values.


Summary

Reactive forms offer a more structured and scalable way to manage form data and validation. They provide full control over the form's behavior and are particularly useful for complex forms where dynamic changes are needed. This approach might require more setup than template-driven forms, but it pays off in flexibility and maintainability for larger applications.