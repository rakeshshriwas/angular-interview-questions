# Angular Interview Questions & Answers

---

### Table of Contents

| No. | Questions |
|---- | ---------
|1 | [What is pipe?](#)|

79. ### What Is Angular
    Angular is a framework for building dynamic, single-page web applications (SPAs) using TypeScript, HTML, and CSS. Developed and maintained by Google, Angular provides a complete toolkit for developers to create complex, feature-rich applications efficiently.

    **Key Features of Angular:**
    1. **Component-Based Architecture**: Applications are built using reusable and modular components, which makes the codebase more organized and maintainable.
    2. **Two-Way Data Binding**: This feature synchronizes data between the model (business logic) and the view (UI) automatically, so changes in the UI are reflected in the data and vice versa.
    3. **Dependency Injection**: Angular has a built-in dependency injection system, making it easier to manage services and components.
    4. **Routing**: Angular provides a powerful router for navigating between different views or pages in a single-page application.
    5. **Directives**: Angular offers structural and attribute directives (like ngFor, ngIf) to manipulate DOM elements and create custom behaviors
    6. **Forms**: Angular provides robust form handling with validation, making it easier to work with user input.
    7. **HttpClient**: Angular includes a service for making HTTP requests to APIs, handling asynchronous operations efficiently

79. ### What Is dev dependencies vs dependencies
    The main difference between dependencies and devDependencies in Angular is that dependencies are required for an application to run in production, while devDependencies are only needed for development and testing.

    **Dependencies**:
    Packages that are required to run the application in production. For example, React, Vue, or Firebase.
    
    **DevDependencies**:
    Packages that are only needed for local development and testing. For example, a testing framework like Jest, or other utilities like ESLint.


79. ### What is angular.json
    angular.json is a configuration file in Angular that provides project-level settings and build configurations for an Angular application. It defines how your Angular app is structured, what libraries are used, and how to run, build, or test the app.

79. ### Diffrance between package.json vs package-lock.json
    **package.json**: This file is primarily used for managing and documenting metadata about the project, including its name, version, author, dependencies, scripts, and other configuration details. It acts as a manifest for the project.
    
    **package-lock.json**: This file is generated and updated automatically by npm when installing or updating packages. It is used to lock the exact versions of dependencies installed in the project. It ensures that the same versions of packages are installed consistently across different environments.

79. ### What is standalone component?
    A standalone component is a type of component which is not part of any Angular module. It provides a simplified way to build Angular applications.
79. ### What is a bootstrapped component?
    A bootstrapped component is an entry component that Angular loads into the DOM during the bootstrap process or application launch time. Generally, this bootstrapped or root component is named as AppComponent in your root module using bootstrap property as below.
    ```javascript
    @NgModule ({
       imports:      [ BrowserModule ],
       declarations: [ AppComponent ],
       bootstrap:    [ AppComponent ],
       providers: []
    })
    ```
    The bootstrap process begins in main.ts, which is the entry point of the Angular application. This file contains code to bootstrap the root module (typically AppModule)
    
    ```javascript
    import { platformBrowserDynamic } from '@angular/platform-browser-dynamic'; import { AppModule } from './app/app.module'; 
    
    platformBrowserDynamic().bootstrapModule(AppModule) .catch(err => console.error(err)); //Bootstrap the root module 
    ```
    **Explanation:**
    platformBrowserDynamic(): Creates a platform that is suitable for running Angular in a browser.
    bootstrapModule(AppModule): Loads the root module (AppModule) and kicks off the application.
    
    The root module (usually AppModule) defines the entry point of the application. It declares which components, services, and other dependencies are part of the application.
    ```javascript
    import { NgModule } from '@angular/core';
    import { BrowserModule } from '@angular/platform-browser';
    import { AppComponent } from './app.component';
    
    @NgModule({
      declarations: [AppComponent], // Declare the root component
      imports: [BrowserModule],    // Import necessary modules
      providers: [],               // Declare application-wide services
      bootstrap: [AppComponent],   // Specify the root component to bootstrap
    })
    export class AppModule {}
    ```
    **Explanation:**
    bootstrap: [AppComponent]: Specifies the root component that will be inserted into the index.html file.
    Angular uses this component to render the initial view.
    The root component (AppComponent) is the entry point to the application UI. It is linked to the DOM using a selector.
    ```javascript
    import { Component } from '@angular/core';
    
    @Component({
      selector: 'app-root', // Matches the <app-root> tag in index.html
      template: `<h1>Welcome to Angular!</h1>`,
    })
    export class AppComponent {}
    ```
    The index.html file contains the root component selector (e.g., <app-root>), which Angular replaces with the application content during the bootstrap process.

79. ### What is change dedication strategy in angular?
    In Angular, change detection strategy determines how the framework tracks and updates the component's view in response to changes in data or inputs. Angular provides two primary change detection strategies

    **1. Default Change Detection Strategy**

	This is the default strategy for all components.
	Angular checks the entire component tree starting from the root to ensure that all changes in the application are reflected in the view.

	```javascript
	 @Component({
	  selector: 'app-example',
	  templateUrl: './example.component.html',
	  changeDetection: ChangeDetectionStrategy.Default
	})
	export class ExampleComponent {
	  // Component logic here
	}
	```


    **2. OnPush Change Detection Strategy**

	Angular skips checking the component and its children unless:
	- The component's @Input properties have changed.
	- An event bound to the component is triggered.
	- A manual trigger (ChangeDetectorRef) is used.
	- Suitable for scenarios where the data flow is predictable and primarily driven by immutable inputs.

	```javascript
	 @Component({
	  selector: 'app-example',
	  templateUrl: './example.component.html',
	  changeDetection: ChangeDetectionStrategy.OnPush
	})
	export class ExampleComponent {
	  // Component logic here
	}
	```

	**How to Choose Between Default and OnPush?**

	**Use Default when:**
	- Your application has small or medium complexity.
	- You don't want to manage change detection explicitly.
	- The performance is acceptable without extra optimizations.

	**Use OnPush when:**
	- Your application has large, complex component trees.
	- You are optimizing performance and can manage immutability or manually trigger updates when needed.
	- Your components rely heavily on @Input() bindings for updates.

79. ### What is standalone component?
    A standalone component is a type of component which is not part of any Angular module. It provides a simplified way to build Angular applications.
79. ### What is host property in css?
    The :host pseudo-class selector is used to target styles in the element that hosts the component.
    
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
256. ### What are reactive forms?
     Reactive forms is a model-driven approach for creating forms in a reactive style(form inputs changes over time). These are built around observable streams, where form inputs and values are provided as streams of input values. Let's follow the below steps to create reactive forms,
     1. Register the reactive forms module which declares reactive-form directives in your app
         ```js
         import { ReactiveFormsModule } from '@angular/forms';

         @NgModule({
           imports: [
             // other imports ...
             ReactiveFormsModule
           ],
         })
         export class AppModule { }
         ```
     2. Create a new FormControl instance and save it in the component.
         ```js
         import { Component } from '@angular/core';
         import { FormControl } from '@angular/forms';

         @Component({
           selector: 'user-profile',
           styleUrls: ['./user-profile.component.css']
         })
         export class UserProfileComponent {
           userName = new FormControl('');
         }
         ```
     3. Register the FormControl in the template.
         ```js
         <label>
           User name:
           <input type="text" [formControl]="userName">
         </label>
         ```
     Finally, the component with reactive form control appears as below,
     ```js
     import { Component } from '@angular/core';
     import { FormControl } from '@angular/forms';
	
     @Component({
       selector: 'user-profile',
       styleUrls: ['./user-profile.component.css'],
       template: `
         <label>
           User name:
           <input type="text" [formControl]="userName">
         </label>
       `
     })
     export class UserProfileComponent {
       userName = new FormControl('');
     }
     ```


257. ### What are dynamic forms?
     Dynamic forms is a pattern in which we build a form dynamically based on metadata that describes a business object model. You can create them based on reactive form API.


258. ### What are template driven forms?
     Template driven forms are model-driven forms where you write the logic, validations, controls etc, in the template part of the code using directives. They are suitable for simple scenarios and uses two-way binding with [(ngModel)] syntax.
     For example, you can create register form easily by following the below simple steps,

     1. Import the FormsModule into the Application module's imports array
         ```js
            import { BrowserModule } from '@angular/platform-browser';
            import { NgModule } from '@angular/core';
            import {FormsModule} from '@angular/forms'
            import { RegisterComponent } from './app.component';
            @NgModule({
              declarations: [
                RegisterComponent,
              ],
              imports: [
                BrowserModule,
                FormsModule
              ],
              providers: [],
              bootstrap: [RegisterComponent]
            })
            export class AppModule { }
         ```
     2. Bind the form from template to the component using ngModel syntax
         ```html
         <input type="text" class="form-control" id="name"
           required
           [(ngModel)]="model.name" name="name">
         ```
     3.  Attach NgForm directive to the <form> tag in order to create FormControl instances and register them
         ```js
         <form #registerForm="ngForm">
         ```
     4. Apply the validation message for form controls
         ```html
         <label for="name">Name</label>
         <input type="text" class="form-control" id="name"
                required
                [(ngModel)]="model.name" name="name"
                #name="ngModel">
         <div [hidden]="name.valid || name.pristine"
              class="alert alert-danger">
           Please enter your name
         </div>
         ```
     5. Let's submit the form with ngSubmit directive and add type="submit" button at the bottom of the form to trigger form submit.
         ```html
         <form (ngSubmit)="onSubmit()" #heroForm="ngForm">
         // Form goes here
         <button type="submit" class="btn btn-success" [disabled]="!registerForm.form.valid">Submit</button>
         ```
     Finally, the completed template-driven registration form will be appeared as follow.
     ```html
     <div class="container">
       <h1>Registration Form</h1>
       <form (ngSubmit)="onSubmit()" #registerForm="ngForm">
         <div class="form-group">
           <label for="name">Name</label>
             <input type="text" class="form-control" id="name"
                    required
                    [(ngModel)]="model.name" name="name"
                    #name="ngModel">
             <div [hidden]="name.valid || name.pristine"
                  class="alert alert-danger">
               Please enter your name
             </div>
         </div>
         <button type="submit" class="btn btn-success" [disabled]="!registerForm.form.valid">Submit</button>
         </form>
     </div>
     ```

259. ### What are the differences between reactive forms and template driven forms?
     Below are the main differences between reactive forms and template driven forms

     | Feature | Reactive | Template-Driven |
     |---- |---- | --------- |
     | Form model setup | Created(FormControl instance) in component explicitly | Created by directives  |
     | Data updates | Synchronous | Asynchronous |
     | Form custom validation | Defined as Functions | Defined as Directives |
     | Testing | No interaction with change detection cycle | Need knowledge of the change detection process |
     | Mutability | Immutable(by always returning new value for FormControl instance) | Mutable(Property always modified to new value) |
     | Scalability | More scalable using low-level APIs | Less scalable using due to abstraction on APIs|


260. ### What are the different ways to group form controls?
     Reactive forms provide two ways of grouping multiple related controls.
     1. **FormGroup**: It defines a form with a fixed set of controls those can be managed together in an one object. It has same properties and methods similar to a FormControl instance.
        This FormGroup can be nested to create complex forms as below.
        ```js
        import { Component } from '@angular/core';
        import { FormGroup, FormControl } from '@angular/forms';

        @Component({
          selector: 'user-profile',
          templateUrl: './user-profile.component.html',
          styleUrls: ['./user-profile.component.css']
        })
        export class UserProfileComponent {
          userProfile = new FormGroup({
            firstName: new FormControl(''),
            lastName: new FormControl(''),
            address: new FormGroup({
                  street: new FormControl(''),
                  city: new FormControl(''),
                  state: new FormControl(''),
                  zip: new FormControl('')
                })
          });

          onSubmit() {
            // Store this.userProfile.value in DB
          }
        }
        ```
        ```html
        <form [formGroup]="userProfile" (ngSubmit)="onSubmit()">

          <label>
            First Name:
            <input type="text" formControlName="firstName">
          </label>

          <label>
            Last Name:
            <input type="text" formControlName="lastName">
          </label>

          <div formGroupName="address">
            <h3>Address</h3>

            <label>
              Street:
              <input type="text" formControlName="street">
            </label>

            <label>
              City:
              <input type="text" formControlName="city">
            </label>

            <label>
              State:
              <input type="text" formControlName="state">
            </label>

            <label>
              Zip Code:
              <input type="text" formControlName="zip">
            </label>
           </div>
            <button type="submit" [disabled]="!userProfile.valid">Submit</button>

        </form>
        ```
     2. **FormArray:** It defines a dynamic form in an array format, where you can add and remove controls at run time. This is useful for dynamic forms when you don’t know how many controls will be present within the group.
           ```js
            import { Component } from '@angular/core';
            import { FormArray, FormControl } from '@angular/forms';

            @Component({
              selector: 'order-form',
              templateUrl: './order-form.component.html',
              styleUrls: ['./order-form.component.css']
            })
            export class OrderFormComponent {
              constructor () {
                this.orderForm = new FormGroup({
                  firstName: new FormControl('John', Validators.minLength(3)),
                  lastName: new FormControl('Rodson'),
                  items: new FormArray([
                    new FormControl(null)
                  ])
                });
              }

              onSubmitForm () {
                // Save the items this.orderForm.value in DB
              }

              onAddItem () {
                this.orderForm.controls
                .items.push(new FormControl(null));
              }

              onRemoveItem (index) {
                this.orderForm.controls['items'].removeAt(index);
              }
            }
           ```
           ```html
           <form [formGroup]="orderForm" (ngSubmit)="onSubmit()">

             <label>
               First Name:
               <input type="text" formControlName="firstName">
             </label>

             <label>
               Last Name:
               <input type="text" formControlName="lastName">
             </label>

             <div>
             <p>Add items</p>
             <ul formArrayName="items">
               <li *ngFor="let item of orderForm.controls.items.controls; let i = index">
                 <input type="text" formControlName="{{i}}">
                 <button type="button" title="Remove Item" (click)="onRemoveItem(i)">Remove</button>
               </li>
             </ul>
             <button type="button" (click)="onAddItem">
               Add an item
             </button>
            </div>
           ```

261. ### How do you update specific properties of a form model?
     You can use `patchValue()` method to update specific properties defined in the form model. For example,you can update the name and street of certain profile on click of the update button as shown below.
     ```js
     updateProfile() {
       this.userProfile.patchValue({
         firstName: 'John',
         address: {
           street: '98 Crescent Street'
         }
       });
     }
     ```
     ```html
       <button (click)="updateProfile()">Update Profile</button>
     ```

     You can also use `setValue` method to update properties.

     **Note:** Remember to update the properties against the exact model structure.

     **[⬆ Back to Top](#table-of-contents)**

262. ### What is the purpose of FormBuilder?
     FormBuilder is used as syntactic sugar for easily creating instances of a FormControl, FormGroup, or FormArray. This is helpful to reduce the amount of boilerplate needed to build complex reactive forms. It is available as an injectable helper class of the `@angular/forms` package.

     For example, the user profile component creation becomes easier as shown here.
     ```js
     export class UserProfileComponent {
       profileForm = this.formBuilder.group({
         firstName: [''],
         lastName: [''],
         address: this.formBuilder.group({
           street: [''],
           city: [''],
           state: [''],
           zip: ['']
         }),
       });
       constructor(private formBuilder: FormBuilder) { }
       }
     ```
     
263. ### How do you verify the model changes in forms?
     You can add a getter property(let's say, diagnostic) inside component to return a JSON representation of the model during the development. This is useful to verify whether the values are really flowing from the input box to the model and vice versa or not.
     ```js
     export class UserProfileComponent {

       model = new User('John', 29, 'Writer');

       // TODO: Remove after the verification
       get diagnostic() { return JSON.stringify(this.model); }
     }
     ```
     and add `diagnostic` binding near the top of the form
     ```html
     {{diagnostic}}
     <div class="form-group">
       // FormControls goes here
     </div>
     ```

264. ### What are the state CSS classes provided by ngModel?
     The ngModel directive updates the form control with special Angular CSS classes to reflect it's state. Let's find the list of classes in a tabular format,

     | Form control state | If true | If false |
     |---- | --------- | --- |
     | Visited | ng-touched | ng-untouched |
     | Value has changed | ng-dirty	 | ng-pristine |
     | Value is valid| 	ng-valid | ng-invalid |

     **[⬆ Back to Top](#table-of-contents)**

265. ### How do you reset the form?
     In a model-driven form, you can reset the form just by calling the function `reset()` on our form model.
     For example, you can reset the form model on submission as follows,
     ```js
     onSubmit() {
       if (this.myform.valid) {
         console.log("Form is submitted");
         // Perform business logic here
         this.myform.reset();
       }
     }
     ```
     Now, your form model resets the form back to its original pristine state.

266. ### What are the types of validator functions?
     In reactive forms, the validators can be either synchronous or asynchronous functions,
     1. **Sync validators:** These are the synchronous functions which take a control instance and immediately return either a set of validation errors or null. Also, these functions passed as second argument while instantiating the form control. The main use cases are simple checks like whether a field is empty, whether it exceeds a maximum length etc.
     2. **Async validators:** These are the asynchronous functions which take a control instance and return a Promise or Observable that later emits a set of validation errors or null. Also, these functions passed as second argument while instantiating the form control. The main use cases are complex validations like hitting a server to check the availability of a username or email.

     The representation of these validators looks like below
     ```js
     this.myForm = formBuilder.group({
         firstName: ['value'],
         lastName: ['value', *Some Sync validation function*],
         email: ['value', *Some validation function*, *Some asynchronous validation function*]
     });
     ```

267. ### Can you give an example of built-in validators?
     In reactive forms, you can use built-in validator like `required` and `minlength` on your input form controls. For example, the registration form can have these validators on name input field
     ```js
     this.registrationForm = new FormGroup({
         'name': new FormControl(this.hero.name, [
           Validators.required,
           Validators.minLength(4),
         ])
       });
     ```
     Whereas in template-driven forms, both `required` and `minlength` validators available as attributes.

76. ### What are different types of compilation in Angular?
     Angular offers two ways to compile your application,
     1. Just-in-Time (JIT)
     2. Ahead-of-Time (AOT)

77. ### What is JIT?
     Just-in-Time (JIT) is a type of compilation that compiles your app in the browser at runtime. JIT compilation was the default until Angular 8, now default is AOT. When you run the ng build (build only) or ng serve (build and serve locally) CLI 
     commands, the type of compilation (JIT or AOT) depends on the value of the aot property in your build configuration specified in angular.json. By default, aot is set to true.

78. ### What is AOT?
     Ahead-of-Time (AOT) is a type of compilation that compiles your app at build time. This is the default starting in Angular 9. When you run the ng build (build only) or ng serve (build and serve locally) CLI commands, the type of compilation (JIT 
     or AOT) depends on the value of the aot property in your build configuration specified in angular.json. By default, aot is set to true.
    
    ```cmd
    ng build
    ng serve
    ```

79. ### Why do we need compilation process?
     The Angular components and templates cannot be understood by the browser directly. Due to that Angular applications require a compilation process before they can run in a browser. For example, In AOT compilation, both Angular HTML and TypeScript 
     code converted into efficient JavaScript code during the build phase before browser runs it.

5. ### What is Angular Universal?
    Angular Universal is a server-side rendering module for Angular applications in various scenarios. This is a community driven project and available under @angular/platform-server package. Recently Angular Universal is integrated with Angular CLI.

79. ### What is SSR in angular
     SSR (Server-Side Rendering) in Angular refers to the process of rendering Angular applications on the server rather than in the browser. This technique generates the HTML content on the server before sending it to the client's browser.
     **The key benefits of SSR include:**
    
     - Improved Performance: By delivering pre-rendered HTML, the initial load time can be faster.
     - Better SEO: Search engines can more easily index server-rendered content
     - Enhanced User Experience: Users see a fully rendered page faster
     - In Angular, SSR is typically implemented using Angular Universal, a platform that allows for server-side rendering of Angular applications.

79. ### What is difference between shadow Dom & Dom
    The DOM (Document Object Model) represents the entire structure of an HTML document, where all elements are globally accessible and can be influenced by external styles and scripts. 
    Utilizes the Browser's built-in Shadow DOM API to encapsulate styles, creating a boundary between the shadow dom and the rest of the document.

79. ### What is micro frontend
     A Micro Frontend in Angular is an architectural approach where a large application is split into smaller, independent frontend pieces (micro apps), which can be developed, deployed, and maintained separately. Each micro frontend is         
     responsible for a specific feature or module and works like its own mini application, but together, they form a larger application.
     **Example:**
     Imagine an e-commerce website. The homepage, product page, and shopping cart could each be a separate micro frontend. Each one can be developed and deployed separately, and they work together as one large website. 

79. ### What is memory leak
    A memory leak in Angular occurs when your application retains memory that is no longer needed, which can cause performance issues over time.

    **Example**:

    If a component subscribes to an observable but doesn’t unsubscribe when the component is destroyed, the observable keeps the reference, causing a memory leak.

    Fix: Always unsubscribe in ngOnDestroy() or use takeUntil or async pipe to automatically handle subscriptions.
    ```javascript
    @Component({...})
    export class MyComponent implements OnInit, OnDestroy {
      private subscription: Subscription;
    
      ngOnInit() {
        this.subscription = someObservable.subscribe(data => {
          // handle data
        });
      }
    
      ngOnDestroy() {
        this.subscription.unsubscribe(); // Without this, memory leak happens
      }
    }
    ```
79. ### What is npm and yrn
    **NPM (Node Package Manager)** is a package manager for JavaScript and is widely used with Node.js to manage and install libraries and dependencies. It allows developers to easily install, update, and manage packages of code that can be used in their projects.

    **Yarn** is another package manager for JavaScript, designed as an alternative to NPM. It aims to address some of the performance and consistency issues found in NPM. Yarn provides features like faster installation, deterministic dependency resolution, and offline capability. 

79. ### Why do we need compilation process?
79. ### Why do we need compilation process?

