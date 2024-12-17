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
    When creating a custom pipe, it is important to handle potential errors to ensure that the application remains stable and provides meaningful feedback to the user. Error handling within a custom pipe can be achieved by using try-catch blocks to        catch exceptions and handle them gracefully.

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
