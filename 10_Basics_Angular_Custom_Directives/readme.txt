// Let's understand what is Custom Directive?


What is Custom Directive?
    -> Custom directives in Angular allow you to create reusable functionality that can be applied to DOM elements. They help encapsulate behavior and make your code more modular and maintainable.


Types of Custom Directives
    1. Attribute Directives: Change the appearance or behavior of an element.
    2. Structural Directives: Alter the DOM layout by adding or removing elements.

Example: 
Attribute Directive :
Let's create a custom directive that changes the background color of an element when it is hovered over.

Step 1: Generate the Directive
    -> CLI command to generate custom directive : ng generate directive highlight
This command will create two files: highlight.directive.ts and highlight.directive.spec.ts.

Step 2: Define the Directive Logic
highlight.directive.ts : 

import { Directive, ElementRef, Renderer2, HostListener } from '@angular/core';

@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {

  constructor(private el: ElementRef, private renderer: Renderer2) { }

  @HostListener('mouseenter') onMouseEnter() {
    this.changeColor('yellow');
  }

  @HostListener('mouseleave') onMouseLeave() {
    this.changeColor(null);
  }

  private changeColor(color: string) {
    this.renderer.setStyle(this.el.nativeElement, 'backgroundColor', color);
  }
}

Explanation
@Directive: The decorator that defines the directive and its selector.

ElementRef: Accesses the DOM element the directive is applied to.

Renderer2: Allows safe and efficient DOM manipulation.

@HostListener: Listens for events on the host element and triggers the corresponding methods.

changeColor: A helper method to change the background color of the element.


Step 3: Use the Directive
Apply the directive to an element in your template: app.component.html

<p appHighlight>Hover over this text to see the highlight effect!</p>

This example shows how to create and use a custom attribute directive that changes the background color of an element when it is hovered over. By encapsulating this behavior in a directive, you make it reusable and easy to apply to multiple elements.