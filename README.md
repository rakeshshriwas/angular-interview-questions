# Angular Interview Questions & Answers

---

### Table of Contents

| No. | Questions |
|---- | ---------
|1 | [What is pipe?](#)|


1. ### What is pipe?
    In Angular, pipes are functions that accept input data and transform it to a desired output format. we apply them within templates using the | (pipe) symbol.

    - **Percent Pipe**: Formats numbers into percentages.
    - **Decimal Pipe:** Formats numbers to have a specified decimal precision.
    - **UpperCase / LowerCase Pipe:** Converts strings to upper or lower case.
    - **Json Pipe:** Converts an object into a JSON string.

2. ### What is parameters pipe?
    A pipe can accept any number of optional parameters to fine-tune its output. The parameterized pipe can be created by declaring the pipe name with a colon ( : ) and then the parameter value. If the pipe accepts multiple parameters, separate the 
    values with colons.

3. ### What is pure and impure pipe?
    **Pure pipe:** A pure pipe is only called when Angular detects a change in the value or the parameters passed to a pipe.For example, any changes to a primitive input value (String, Number, Boolean, Symbol) or a changed object reference (Date,          Array, Function, Object).

    **Impure pipe:** An impure pipe is called for every change detection cycle no matter whether the value or parameter(s) changes. i.e, An impure pipe is called often, as often as every keystroke or mouse-move.
    
4. ### What is a custom pipe?
    When the built-in pipes don’t meet your requirements, Angular allows you to create custom pipes.To create a custom pipe, we’ll implement a new class that implements the PipeTransform interface and defines the transformation logic.

    ```javascript
    import { Pipe, PipeTransform } from '@angular/core';
    
    @Pipe({
     name: ‘titleCase’,
    })
    export class TitleCasePipe implements PipeTransform {
     transform(value: string): string {
       if (!value) return ‘’;
         return value
         .toLowerCase()
         .split(‘ ‘)
         .map(word => word.charAt(0).toUpperCase() + word.slice(1))
         .join(‘ ‘);
       }
    }
    ```

    ```Html
    <!-- Applying the custom TitleCasePipe -->
    <p>{{ ‘hello world from angular’ | titleCase }}</p> <!-- Outputs ‘Hello World From Angular’ >
    ```
5. ### What is the purpose of async pipe?
    The AsyncPipe subscribes to an observable or promise and returns the latest value it has emitted. When a new value is emitted, the pipe marks the component to be checked for changes. When the component is destroyed, the async pipe automatically unsubscribes to prevent memory leaks.

    Let's take a time observable which continuously updates the view for every 2 seconds with the current time.

   ```javascript
   @Component({
      selector: 'async-observable-pipe',
      template: `<div><code>observable|async</code>:
           Time: {{ time | async }}</div>`
    })
    export class AsyncObservablePipeComponent {
      time: Observable<string>;
      constructor() {
        this.time = new Observable((observer) => {
          setInterval(() => {
            observer.next(new Date().toString());
          }, 2000);
        });
      }
    }
   ```
6. ### How would you handle errors within a custom pipe? Provide a code example.
    When creating a custom pipe, it is important to handle potential errors to ensure that the application remains stable and provides meaningful feedback to the user. Error handling within a custom pipe can be achieved by using try-catch blocks to       catch exceptions and handle them gracefully.

   ```javascript
   import { Pipe, PipeTransform } from '@angular/core';

    @Pipe({
      name: 'safeTransform'
    })
    export class SafeTransformPipe implements PipeTransform {
      transform(value: any, ...args: any[]): any {
        try {
          // Perform the transformation logic
          if (!value) {
            throw new Error('Invalid value');
          }
          return value.toUpperCase();
        } catch (error) {
          console.error('Error in SafeTransformPipe:', error);
          return 'Error';
        }
      }
    }
   ```
7. ### What is directives in angular
   In angular, directives are classes that add behaviour to an existing DOM element or an existing component instance in Angular applications.

   - Directives modify the DOM and control its behavior.
   - There are three main types: Components, Structural, and Attribute directives.
   - Custom directives allow you to implement reusable DOM manipulation logic.

   **Types of Directives:**

   1. **Component Directives:** A component is essentially a directive with a template.

   
    ```javascript
   @Component({
      selector: 'app-example',
      template: '<p>Hello World</p>'
    })
    export class ExampleComponent {}
   ```
      
   2. **Structural Directives:** Used to change the structure of the DOM by adding or removing elements.
      - *ngIf: Adds or removes elements based on a condition.
      - *ngFor: Iterates over a collection and renders elements for each item.
      - *ngSwitch: Displays one of multiple elements based on a condition.

        ```html
        <div *ngIf="isVisible">This is visible</div>
        ```
        
   3. **Attribute Directives:** Used to modify the appearance or behavior of an element, component, or another directive.
      - ngClass: Dynamically applies CSS classes.
      - ngStyle: Dynamically applies inline styles.
        
        ```html
        <div [ngClass]="{'active': isActive}">Styled Div</div>
        ```
   4. **Custom Directives:** We can also create custom directives to encapsulate reusable behavior.
  
      ```javascript
      import { Directive, ElementRef, Renderer2, HostListener } from '@angular/core';

      @Directive({
         selector: '[appHighlight]'
      })
      export class HighlightDirective {
          constructor(private el: ElementRef, private renderer: Renderer2) {}
    
          @HostListener('mouseenter') onMouseEnter() {
            this.renderer.setStyle(this.el.nativeElement, 'color', 'blue');
          }
    
          @HostListener('mouseleave') onMouseLeave() {
            this.renderer.setStyle(this.el.nativeElement, 'color', 'black');
          }
      }
      ```
      
      ```html
      <p appHighlight>Hover over me!</p>
      ```
8. ### When to use a directive?
    Consider an application, where multiple components need to have similar functionalities. The norm thing to do is by adding this functionality individually to every component but, this task is tedious to perform. In such a situation, one can     
    create a directive having the required functionality and then, import the directive to components which require this functionality.

9. ### How does angular finds components, directives and pipes?
    The Angular compiler finds a component or directive in a template when it can match the selector of that component or directive in that template. Whereas it finds a pipe if the pipe's name appears within the pipe syntax of the template HTML.
