// Let's understand what is Template Reference


What is Template Reference?
    -> Template reference variables in Angular allow you to reference DOM elements or Angular components within your template. You declare a template reference variable using the # symbol and then you can use it within the same template to access the element or component it references.


How It Works
You can create a reference to an element by using the # symbol followed by the variable name. This allows you to interact with the element directly in your template or pass it to component methods.

Example :
Let’s look at an example where we reference an input field and a button to clear the input field:

Template (HTML) :

<div>
  <input #inputBox type="text" placeholder="Enter text here">
  <button (click)="clearInput(inputBox)">Clear</button>
  <p>The input value is: {{ inputBox.value }}</p>
</div>

Component Class (TypeScript) :

import { Component } from '@angular/core';

@Component({
  selector: 'app-input-clearer',
  templateUrl: './input-clearer.component.html',
  styleUrls: ['./input-clearer.component.css']
})
export class InputClearerComponent {
  clearInput(input: HTMLInputElement) {
    input.value = '';
  }
}

Explanation :

Template Reference Variable: The #inputBox creates a reference to the <input> element.

Access in Template: You can use inputBox.value to display the current value of the input field.

Pass to Method: The clearInput method is called when the button is clicked, and it receives the inputBox reference as an argument. This method then clears the input field.