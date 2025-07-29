# Angular Interview Questions & Answers

---

### Table of Contents

| No. | Questions |
|---- | ---------
|1 | [What is pipe?](#)|

1. ### What Is Angular
    Angular is a framework for building dynamic, single-page web applications (SPAs) using TypeScript, HTML, and CSS. Developed and maintained by Google, Angular provides a complete toolkit for developers to create complex, feature-rich applications efficiently.

    **Key Features of Angular:**
    1. **Component-Based Architecture**: Applications are built using reusable and modular components, which makes the codebase more organized and maintainable.
    2. **Two-Way Data Binding**: This feature synchronizes data between the model (business logic) and the view (UI) automatically, so changes in the UI are reflected in the data and vice versa.
    3. **Dependency Injection**: Angular has a built-in dependency injection system, making it easier to manage services and components.
    4. **Routing**: Angular provides a powerful router for navigating between different views or pages in a single-page application.
    5. **Directives**: Angular offers structural and attribute directives (like ngFor, ngIf) to manipulate DOM elements and create custom behaviors
    6. **Forms**: Angular provides robust form handling with validation, making it easier to work with user input.
    7. **HttpClient**: Angular includes a service for making HTTP requests to APIs, handling asynchronous operations efficiently

2. ### What is angular CLI?
    The Angular CLI (Command Line Interface) is a powerful tool provided by the Angular team that simplifies the development, testing, and deployment of Angular applications. It provides a set of commands that help developers streamline and automate 
    various tasks associated with Angular projects.

3. ### What is Lifecycle hooks
   Lifecycle hooks are a set of methods in Angular that are executed at specific moments during the lifecycle of a component. These methods provide a way to tap into the Angular component lifecycle and perform custom logic or operations at specific points in time.

   **There are eight lifecycle hooks in Angular:**

	1. **ngOnChanges:** This lifecycle hook is executed whenever the component's input properties change
    
	3. **ngOnInit:** This lifecycle hook is executed after the component's constructor method and is a good place to perform initial setup for the component.
	
 	4. **ngDoCheck:** This lifecycle hook is executed during every change detection cycle and is a good place to perform custom change detection.
	
  	5. **ngAfterContentInit:** This lifecycle hook is executed after the component's content has been initialized and is a good place to perform additional setup for the component's content.
	
 	6. **ngAfterContentChecked:** This lifecycle hook is executed after the component's content has been checked and is a good place to perform additional operations based on the component's content.
	
 	7. **ngAfterViewInit:** This lifecycle hook is executed after the component's view has been initialized and is a good place to perform additional setup for the component's view.
	
 	8. **ngAfterViewChecked:** This lifecycle hook is executed after the component's view has been checked and is a good place to perform additional operations based on the component's view.
	
 	9. **ngOnDestroy:** This lifecycle hook is executed just before the component is destroyed and is a good place to perform cleanup operations for the component.
    
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

81. ### What is a template?
    A template is a HTML view where you can display data by binding controls to properties of an Angular component. You can store your component's template in one of two places. You can define it inline using the template property, or you can define the template in a separate HTML file and link to it in the component metadata using the @Component decorator's templateUrl property.

   	**Using inline template with template syntax**
    
	    ```javascript
	    import { Component } from '@angular/core';
	
	    @Component ({
	       selector: 'my-app',
	       template: '
	          <div>
	             <h1>{{title}}</h1>
	             <div>Learn Angular</div>
	          </div>
	       '
	    })
	
	    export class AppComponent {
	       title: string = 'Hello World';
	    }
	    ```
    
       **Using separate template file such as app.component.html**
    
	    ```javascript
	    import { Component } from '@angular/core';
	
	    @Component ({
	       selector: 'my-app',
	       templateUrl: 'app/app.component.html'
	    })
	
	    export class AppComponent {
	       title: string = 'Hello World';
	    }
	    ```

81. ### What is a module?
	Modules are logical boundaries in your application and the application is divided into separate modules to separate the functionality of your application. Lets take an example of app.module.ts root module declared with @NgModule decorator as below,

	   ```javascript
		import { NgModule }      from '@angular/core';
		import { BrowserModule } from '@angular/platform-browser';
		import { AppComponent }  from './app.component';
		
		@NgModule ({
		   imports:      [ BrowserModule ],
		   declarations: [ AppComponent ],
		   bootstrap:    [ AppComponent ],
		   providers: []
		})
		export class AppModule { }
	   ```
225. ### What are feature modules?
     Feature modules are NgModules, which are used for the purpose of organizing code. The feature module can be created with Angular CLI using the below command in the root directory,
     ```javascript
     ng generate module MyCustomFeature //
     ```
     Angular CLI creates a folder called `my-custom-feature` with a file inside called `my-custom-feature.module.ts` with the following contents
     ```javascript
     import { NgModule } from '@angular/core';
     import { CommonModule } from '@angular/common';

     @NgModule({
       imports: [
         CommonModule
       ],
       declarations: []
     })
     export class MyCustomFeature { }
     ```
238. ### What is a shared module?
     The Shared Module is the module in which you put commonly used directives, pipes, and components into one module that is shared(import it) throughout the application.

     For example, the below shared module imports CommonModule, FormsModule for common directives and components, pipes and directives based on the need,
     ```js
     import { CommonModule } from '@angular/common';
     import { NgModule } from '@angular/core';
     import { FormsModule } from '@angular/forms';
     import { UserComponent } from './user.component';
     import { NewUserDirective } from './new-user.directive';
     import { OrdersPipe } from './orders.pipe';

     @NgModule({
      imports:      [ CommonModule ],
      declarations: [ UserComponent, NewUserDirective, OrdersPipe ],
      exports:      [ UserComponent, NewUserDirective, OrdersPipe,
                      CommonModule, FormsModule ]
     })
     export class SharedModule { }
     ```
99. ### What is the purpose of common module?
    The commonly-needed services, pipes, and directives provided by @angular/common module. Apart from these HttpClientModule is available under @angular/common/http.

226. ### What are the imported modules in CLI generated feature modules?
     In the CLI generated feature module, there are two JavaScript import statements at the top of the file
     1. **NgModule:** InOrder to use the `@NgModule` decorator
     2. **CommonModule:** It provides many common directives such as `ngIf` and `ngFor`.

34. ### What is a bootstrapping module?
    Every application has at least one Angular module, the root module that you bootstrap to launch the application is called as bootstrapping module. It is commonly known as `AppModule`. The default structure of `AppModule` generated by AngularCLI would be as follows:
	
	```javascript
        import { BrowserModule } from '@angular/platform-browser';
        import { NgModule } from '@angular/core';
        import { FormsModule } from '@angular/forms';
        import { HttpClientModule } from '@angular/common/http';

        import { AppComponent } from './app.component';

        /* the AppModule class with the @NgModule decorator */
        @NgModule({
          declarations: [
            AppComponent
          ],
          imports: [
            BrowserModule,
            FormsModule,
            HttpClientModule
          ],
          providers: [],
          bootstrap: [AppComponent]
        })
        export class AppModule { }
	```

81. ### What is a data binding?
    Data binding is a core concept in Angular and allows to define communication between a component and the DOM, making it very easy to define interactive applications without worrying about pushing and pulling data. There are four forms of data binding(divided as 3 categories) which differ in the way the data is flowing.
    
    1. **From the Component to the DOM:**

        **Interpolation:** {{ value }}: Adds the value of a property from the component
        ```html
        <li>Name: {{ user.name }}</li>
        <li>Address: {{ user.address }}</li>
        ```
        **Property binding:** [property]=”value”: The value is passed from the component to the specified property or simple HTML attribute
        ```html
        <input type="email" [value]="user.email">
        ```
    2. **From the DOM to the Component:**
        **Event binding: (event)=”function”:** When a specific DOM event happens (eg.: click, change, keyup), call the specified method in the component
        ```html
        <button (click)="logout()"></button>
        ```
    3. **Two-way binding:**
        **Two-way data binding:** [(ngModel)]=”value”: Two-way data binding allows to have the data flow both ways. For example, in the below code snippet, both the email DOM input and component email property are in sync
        ```html
        <input type="email" [(ngModel)]="user.email">
        ```
13. ### What is metadata?
    Metadata is used to decorate a class so that it can configure the expected behavior of the class. The metadata is represented by decorators
    1. **Class decorators**, e.g. @Component and @NgModule
        ```typescript
        import { NgModule, Component } from '@angular/core';

        @Component({
          selector: 'my-component',
          template: '<div>Class decorator</div>',
        })
        export class MyComponent {
          constructor() {
            console.log('Hey I am a component!');
          }
        }

        @NgModule({
          imports: [],
          declarations: [],
        })
        export class MyModule {
          constructor() {
            console.log('Hey I am a module!');
          }
        }
        ```
    2. **Property decorators** Used for properties inside classes, e.g. @Input and @Output
        ```typescript
        import { Component, Input } from '@angular/core';

        @Component({
            selector: 'my-component',
            template: '<div>Property decorator</div>'
        })

        export class MyComponent {
            @Input()
            title: string;
        }
        ```
    3. **Method decorators** Used for methods inside classes, e.g. @HostListener
        ```typescript
        import { Component, HostListener } from '@angular/core';

        @Component({
            selector: 'my-component',
            template: '<div>Method decorator</div>'
        })
        export class MyComponent {
            @HostListener('click', ['$event'])
            onHostClick(event: Event) {
                // clicked, `event` available
            }
        }
        ```
    4. **Parameter decorators** Used for parameters inside class constructors, e.g. @Inject, @Optional
        ```typescript
        import { Component, Inject } from '@angular/core';
        import { MyService } from './my-service';

        @Component({
            selector: 'my-component',
            template: '<div>Parameter decorator</div>'
        })
        export class MyComponent {
            constructor(@Inject(MyService) myService) {
                console.log(myService); // MyService
            }
        }
        ```

15. ### What is the difference between constructor and ngOnInit?
    The **Constructor** is a default method of the class that is executed when the class is instantiated and ensures proper initialisation of fields in the class and its subclasses. Angular, or better Dependency Injector (DI), analyses the constructor parameters and when it creates a new instance by calling new MyClass() it tries to find providers that match the types of the constructor parameters, resolves them and passes them to the constructor.  
    **ngOnInit** is a life cycle hook called by Angular to indicate that Angular is done creating the component.  
    Mostly we use ngOnInit for all the initialization/declaration and avoid stuff to work in the constructor. The constructor should only be used to initialize class members but shouldn't do actual "work".
    So you should use constructor() to setup Dependency Injection and not much else. ngOnInit() is better place to "start" - it's where/when components' bindings are resolved.

    ```typescript
    export class App implements OnInit{
      constructor(private myService: MyService){
         //called first time before the ngOnInit()
      }

      ngOnInit(){
         //called after the constructor and called  after the first ngOnChanges()
         //e.g. http call...
      }
    }
    ```

108. ### What is a service worker and its role in Angular?
     A Service Worker is a script that runs in the background of a web application, separate from the main browser thread. It enables powerful features like:
	- Offline support
	- Background sync
	- Push notifications
	- Caching for performance

Role of Service Worker in Angular:
In Angular, the Service Worker is part of the Progressive Web App (PWA) capabilities, provided via the @angular/service-worker package.

16. ### What is a service?
    A service is used when a common functionality needs to be provided to various modules. Services allow for greater separation of concerns for your application and better modularity by allowing you to extract common functionality out of components.

    Let's create a repoService which can be used across components,

    ```typescript
    import { Injectable } from '@angular/core';
    import { Http } from '@angular/http';

    @Injectable({ // The Injectable decorator is required for dependency injection to work
      // providedIn option registers the service with a specific NgModule
      providedIn: 'root',  // This declares the service with the root app (AppModule)
    })
    export class RepoService{
      constructor(private http: Http){
      }

      fetchAll(){
        return this.http.get('https://api.github.com/repositories');
      }
    }
    ```
    The above service uses Http service as a dependency.

140. ### How do you pass headers for HTTP client?
     You can directly pass object map for http client or create HttpHeaders class to supply the headers.

     ```javascript
     constructor(private _http: HttpClient) {}
     this._http.get('someUrl',{
        headers: {'header1':'value1','header2':'value2'}
     });

     (or)
     let headers = new HttpHeaders().set('header1', headerValue1); // create header object
     headers = headers.append('header2', headerValue2); // add a new header, creating a new object
     headers = headers.append('header3', headerValue3); // add another header

     let params = new HttpParams().set('param1', value1); // create params object
     params = params.append('param2', value2); // add a new param, creating a new object
     params = params.append('param3', value3); // add another param

     return this._http.get<any[]>('someUrl', { headers: headers, params: params })
     ```


18. ### What is dependency injection in Angular?
    Dependency injection (DI), is an important application design pattern in which a class asks for dependencies from external sources rather than creating them itself. Angular comes with its own dependency injection framework for resolving dependencies( services or objects that a class needs to perform its function).So you can have your services depend on other services throughout your application.

23. ### What happens if you use script tag inside template?

    Angular recognizes the value as unsafe and automatically sanitizes it, which removes the `script` tag but keeps safe content such as the text content of the `script` tag. This way it eliminates the risk of script injection attacks. If you still use it then it will be ignored and a warning appears in the browser console.

    Let's take an example of innerHtml property binding which causes XSS vulnerability,
    ```typescript
    export class InnerHtmlBindingComponent {
      // For example, a user/attacker-controlled value from a URL.
      htmlSnippet = 'Template <script>alert("0wned")</script> <b>Syntax</b>';
    }
    ```
107. ### How to inject the dynamic script in angular?
     Using DomSanitizer we can inject the dynamic Html,Style,Script,Url.

     ```
     import { Component, OnInit } from '@angular/core';
     import { DomSanitizer } from '@angular/platform-browser';
     @Component({
        selector: 'my-app',
        template: `
            <div [innerHtml]="htmlSnippet"></div>
        `,
     })
     export class App {
            constructor(protected sanitizer: DomSanitizer) {}
            htmlSnippet: string = this.sanitizer.bypassSecurityTrustScript("<script>safeCode()</script>");
        }
     ```
     
24. ### What is interpolation?

    Interpolation is a special syntax that Angular converts into property binding. It’s a convenient alternative to property binding. It is represented by double curly braces({{}}). The text between the braces is often the name of a component property. Angular replaces that name with the string value of the corresponding component property.

    Let's take an example,
    ```html
    <h3>
      {{title}}
      <img src="{{url}}" style="height:30px">
    </h3>
    ```
    In the example above, Angular evaluates the title and url properties and fills in the blanks, first displaying a bold application title and then a URL.

36. ### What is HttpClient and its benefits?
    Most of the Front-end applications communicate with backend services over `HTTP` protocol using either `XMLHttpRequest` interface or the `fetch()` API. Angular provides a simplified client HTTP API known as `HttpClient` which is based on top of `XMLHttpRequest` interface. This client is available from `@angular/common/http` package.
    You can import in your root module as below:

    ```javascript
    import { HttpClientModule } from '@angular/common/http';
    ```

    The major advantages of HttpClient can be listed as below,
    1. Contains testability features
    2. Provides typed request and response objects
    3. Intercept request and response
    4. Supports Observable APIs
    5. Supports streamlined error handling

37. ### Explain on how to use `HttpClient` with an example?
    Below are the steps need to be followed for the usage of `HttpClient`.
    1. Import `HttpClient` into root module:
        ```javascript
        import { HttpClientModule } from '@angular/common/http';
        @NgModule({
          imports: [
            BrowserModule,
            // import HttpClientModule after BrowserModule.
            HttpClientModule,
          ],
          ......
          })
         export class AppModule {}
        ```
    2. Inject the `HttpClient` into the application:
        Let's create a userProfileService(`userprofile.service.ts`) as an example. It also defines get method of `HttpClient`:
        ```javascript
        import { Injectable } from '@angular/core';
        import { HttpClient } from '@angular/common/http';

        const userProfileUrl: string = 'assets/data/profile.json';

        @Injectable()
        export class UserProfileService {
          constructor(private http: HttpClient) { }

          getUserProfile() {
            return this.http.get(this.userProfileUrl);
          }
        }
        ```
    3. Create a component for subscribing service:
        Let's create a component called UserProfileComponent(`userprofile.component.ts`), which injects `UserProfileService` and invokes the service method:
        ```javascript
        fetchUserProfile() {
          this.userProfileService.getUserProfile()
            .subscribe((data: User) => this.user = {
                id: data['userId'],
                name: data['firstName'],
                city:  data['city']
            });
        }
        ```
    Since the above service method returns an Observable which needs to be subscribed in the component.

81. ### What are components?
	Components are the most basic UI building block of an Angular app, which form a tree of Angular components. These components are a subset of directives. Unlike directives, components always have a template, and only one component can be instantiated per element in a template. Let's see a simple example of Angular component.

	```javascript
	import { Component } from '@angular/core';
	
	@Component ({
	   selector: 'my-app',
	   template: ` <div>
	      <h1>{{title}}</h1>
	      <div>Learn Angular6 with examples</div>
	   </div> `,
	})
	
	export class AppComponent {
	   title: string = 'Welcome to Angular world';
	}
	```
59. ### What are dynamic components?
    Dynamic components are the components in which the component's location in the application is not defined at build time i.e. they are not used in any angular template. Instead, the component is instantiated and placed in the application at runtime.

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
202. ### What is slice pipe?
     The slice pipe is used to create a new Array or String containing a subset (slice) of the elements. The syntax looks like as below,
     ```javascript
     {{ value_expression | slice : start [ : end ] }}
     ```
     For example, you can provide 'hello' list based on a greeting array,
     ```javascript
     @Component({
       selector: 'list-pipe',
       template: `<ul>
         <li *ngFor="let i of greeting | slice:0:5">{{i}}</li>
       </ul>`
     })
     export class PipeListComponent {
       greeting: string[] = ['h', 'e', 'l', 'l', 'o', 'm','o', 'r', 'n', 'i', 'n', 'g'];
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

138. ### How do you select an element with in a component template?
     You can use `@ViewChild` directive to access elements in the view directly. Let's take input element with a reference,

     ```html
     <input #uname>
     ```
     and define view child directive and access it in ngAfterViewInit lifecycle hook

     ```javascript
     @ViewChild('uname') input;

     ngAfterViewInit() {
       console.log(this.input.nativeElement.value);
     }
     ```
     
138. ### What is View Encapsulation
     View Encapsulation is a concept that helps developers manage styles and avoid style conflicts in their applications. It ensures the isolation of styles defined within a component.
Angular supports three types of view encapsulation: Emulated, Shadow DOM, and None.

	**Emulated:** Dynamically generates unique attributes to isolate styles within a component, ensuring they don't affect or get affected by styles in other components.

	**Shadow DOM:** Utilizes the Browser's built-in Shadow DOM API to encapsulate styles, creating a boundary between the component and the rest of the document.

	**None:** Disables view encapsulation, Styles defined in a component can affect the entire application.

275. ### What is ng-content and its purpose.
     
     The ng-content is used to insert the content dynamically inside the component that helps to increase component reusability. 

     ```html
	<div class="card">
	 <div class="card-header">
	   <ng-content select="[header]"></ng-content>
	 </div>
	 <div class="card-body">
	   <ng-content></ng-content>
	 </div>
	</div>
	
	<my-card>
	 <h2 header>My Card Header</h2>
	 <p>This is the body content of my card.</p>
	</my-card>
      ```
     
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

79. ### What is interceptors?
    In Angular, interceptors are a powerful mechanism used to intercept and modify HTTP requests and responses globally. They allow you to customize or transform HTTP requests before they are sent to the server and responses before they are processed by the application. This is especially useful for tasks like adding authentication tokens, logging, or handling errors centrally.

    **How Interceptors Works:** Interceptors are implemented by creating a service that implements the HttpInterceptor interface. They are registered as providers in the Angular module and automatically intercept requests.
    **Common Use Cases:**
	- Authentication: Add JWT tokens or API keys to requests.
	- Logging: Log all outgoing requests and incoming responses for debugging.
	- Error Handling: Handle global errors, such as unauthorized access (401) or server errors (500).
	- Caching: Cache certain responses to reduce unnecessary server requests.
	
 	The syntax of HttpInterceptor interface looks like as below,
	
	```javascript
	     interface HttpInterceptor {
	       intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>>
	     }
	```
 
	     You can use interceptors by declaring a service class that implements the intercept() method of the HttpInterceptor interface.
	
	     ```javascript
	     @Injectable()
	     export class MyInterceptor implements HttpInterceptor {
	         constructor() {}
	         intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
	             ...
	         }
	     }
	     ```
	     After that you can use it in your module,
	
	     ```javascript
	     @NgModule({
	         ...
	         providers: [
	             {
	                 provide: HTTP_INTERCEPTORS,
	                 useClass: MyInterceptor,
	                 multi: true
	             }
	         ]
	         ...
	     })
	     export class AppModule {}
	     ```
174. ### What are the applications of HTTP interceptors?
     The HTTP Interceptors can be used for different variety of tasks,

     1. Authentication
     2. Logging
     3. Caching
     4. Fake backend
     5. URL transformation
     6. Modifying headers

175. ### Is multiple interceptors supported in Angular?
     Yes, Angular supports multiple interceptors at a time. You could define multiple interceptors in providers property:
     ```javascript
     providers: [
       { provide: HTTP_INTERCEPTORS, useClass: MyFirstInterceptor, multi: true },
       { provide: HTTP_INTERCEPTORS, useClass: MySecondInterceptor, multi: true }
     ],
     ```
     The interceptors will be called in the order in which they were provided. i.e, MyFirstInterceptor will be called first in the above interceptors configuration.

176. ### How can I use interceptor for an entire application?
     You can use same instance of `HttpInterceptors` for the entire app by importing the `HttpClientModule` only in your AppModule, and add the interceptors to the root application injector.
     For example, let's define a class that is injectable in root application.
      ```javascript
      @Injectable()
      export class MyInterceptor implements HttpInterceptor {
        intercept(
          req: HttpRequest<any>,
          next: HttpHandler
        ): Observable<HttpEvent<any>> {

          return next.handle(req).do(event => {
            if (event instanceof HttpResponse) {
                 // Code goes here
            }
          });

        }
      }
      ```
     After that import HttpClientModule in AppModule
     ```javascript
     @NgModule({
       declarations: [AppComponent],
       imports: [BrowserModule, HttpClientModule],
       providers: [
         { provide: HTTP_INTERCEPTORS, useClass: MyInterceptor, multi: true }
       ],
       bootstrap: [AppComponent]
     })
     export class AppModule {}
     ```

79. ### ⁠How can handel error in angular
    You can handle responses and errors using RxJS operators like map() and catchError().
    
    ```javascript
	@Injectable({
	  providedIn: 'root'
	})
	export class ApiService {
	  private apiUrl = 'https://api.example.com/data'; // Replace with your API URL
	  constructor(private http: HttpClient) { }
	
	  getData(): Observable<any> {
	    return this.http.get<any>(this.apiUrl).pipe(
	      catchError(this.handleError)
	    );
	  }
	
	  private handleError(error: any) {
	    // Handle the error here (e.g., log it, show a user-friendly message, etc.)
	    console.error('An error occurred:', error);
	    return throwError(() => new Error('Something went wrong; please try again later.'));
	  }
	}
    ```

63. ### What is Angular Router?
    Angular Router is a mechanism in which navigation happens from one view to the next as users perform application tasks. It borrows the concepts or model of browser's application navigation. It enables developers to build Single Page Applications with multiple views and allow navigation between these views.
    
12. ### What is router outlet
    In Angular, a router-outlet is a directive that acts as a placeholder in a component’s template. It’s used to dynamically load different components based on the current URL route. When the Angular Router matches a URL to a route, it dynamically loads the corresponding component into the <router-outlet> location within your application's layout.

12. ### What is Angular router
    Angular Router is an important feature of the Angular framework that helps you to build rich and interactive single-page applications (SPAs) with multiple views.

67. ### What are router links?
    The RouterLink is a directive on the anchor tags give the router control over those elements. Since the navigation paths are fixed, you can assign string values to router-link directive as below,

    ```html
    <h1>Angular Router</h1>
    <nav>
      <a routerLink="/todosList" >List of todos</a>
      <a routerLink="/completed" >Completed todos</a>
    </nav>
    <router-outlet></router-outlet>
    ```

68. ### What are active router links?
    RouterLinkActive is a directive that toggles css classes for active RouterLink bindings based on the current RouterState. i.e, The Router will add CSS classes when this link is active and remove when the link is inactive. For example, you can add them to RouterLinks as below.

    ```html
    <h1>Angular Router</h1>
    <nav>
      <a routerLink="/todosList" routerLinkActive="active">List of todos</a>
      <a routerLink="/completed" routerLinkActive="active">Completed todos</a>
    </nav>
    <router-outlet></router-outlet>
    ```
    
71. ### What is activated route?
    ActivatedRoute contains the information about a route associated with a component loaded in an outlet. It can also be used to traverse the router state tree. The ActivatedRoute will be injected as a router service to access the information. In the below example, you can access route path and parameters,

    ```javascript
    @Component({...})
    class MyComponent {
      constructor(route: ActivatedRoute) {
        const id: Observable<string> = route.params.pipe(map(p => p.id));
        const url: Observable<string> = route.url.pipe(map(segments => segments.join('')));
        // route.data includes both `data` and `resolve`
        const user = route.data.pipe(map(d => d.user));
      }
    }
    ```

72. ### How do you define routes?
     A router must be configured with a list of route definitions. You configures the router with routes via the `RouterModule.forRoot()` method, and adds the result to the AppModule's `imports` array.

    ```javascript
     const appRoutes: Routes = [
      { path: 'todo/:id',      component: TodoDetailComponent },
      {
        path: 'todos',
        component: TodosListComponent,
        data: { title: 'Todos List' }
      },
      { path: '',
        redirectTo: '/todos',
        pathMatch: 'full'
      },
      { path: '**', component: PageNotFoundComponent }
    ];

    @NgModule({
      imports: [
        RouterModule.forRoot(
          appRoutes,
          { enableTracing: true } // <-- debugging purposes only
        )
        // other imports here
      ],
      ...
    })
    export class AppModule { }
    ```

73. ### What is the purpose of Wildcard route?
    If the URL doesn't match any predefined routes then it causes the router to throw an error and crash the app. In this case, you can use wildcard route. A wildcard route has a path consisting of two asterisks to match every URL.

    For example, you can define PageNotFoundComponent for wildcard route as below
    ```javascript
    { path: '**', component: PageNotFoundComponent }
    ```

74. ### Do I need a Routing Module always?
    No, the Routing Module is a design choice. You can skip routing Module (for example, AppRoutingModule) when the configuration is simple and merge the routing configuration directly into the companion module (for example, AppModule). But it is recommended when the configuration is complex and includes specialized guard and resolver services.

12. ### Route Guards in Angular
    In Angular, guards are special classes used to control and manage access to different parts of an application. They decide whether a user can navigate to a particular route or perform certain actions based on specific conditions, like checking if the user is logged in or has the necessary permissions.

    **CanActivate:** Determines if a route can be activated and allows navigation based on certain conditions
	
	```javascript
	@Injectable({
	  providedIn: 'root',
	})
	export class ActivateGuard implements CanActivate {
	  public isAllowed: boolean = false;
	
	  constructor(private router: Router) {}
	  canActivate(route: ActivatedRouteSnapshot, state: RouterStateSnapshot) {
	    if (this.isAllowed) {
	      return true;
	    } else {
	      alert('No Permission');
	      this.router.navigate(['home', 'home-settings', 1], {
	        queryParams: { isActive: true },
	      });
	      return false;
	    }
	  }
	}
	```
 
   **CanActivateChild:** Similar to CanActivate but controls the activation of child routes.
   **CanDeactivate:** Checks if a route can be deactivated, often used to confirm navigation away from a route.
   **CanLoad:** Prevents a module from being loaded lazily until certain conditions are met.

282. ### What are the Route Parameters? Could you explain each of them?.
      Route parameters are used to pass dynamic values in the URL of a route. They allow you to define variable segments in the route path, which can be accessed and used by components and services. Path parameters are represented by a colon (":") followed by the parameter name.

      There are three types of route parameters in Angular:

      **Path parameters:** Path parameters are used to define dynamic segments in the URL path. They are specified as part of the route's path and are extracted from the actual URL when navigating to that route. Path parameters are represented by a colon (":") followed by the parameter name. For example:

      ```typescript
      { path: 'users/:id', component: UserComponent }
      ```

      In this example, ":id" is the path parameter. When navigating to a URL like "/users/123", the value "123" will be extracted and can be accessed in the UserComponent.

      **Query parameters:** Query parameters are used to pass additional information in the URL as key-value pairs. They are appended to the URL after a question mark ("?") and can be accessed by components and services. Query parameters are not part of the route path, but they provide additional data to the route. For example:

      ```typescript
      { path: 'search', component: SearchComponent }
      ```

      In this example, a URL like "/search?query=angular" contains a query parameter "query" with the value "angular". The SearchComponent can retrieve the value of the query parameter and use it for searching.

      **Optional parameters:** Optional parameters are used when you want to make a route parameter optional. They are represented by placing a question mark ("?") after the parameter name. Optional parameters can be useful when you have routes with varying parameters. For example:

      ```typescript
      { path: 'products/:id/:category?', component: ProductComponent }
      ```

      In this example, the ":category" parameter is optional. The ProductComponent can be accessed with URLs like "/products/123" or "/products/123/electronics". If the ":category" parameter is present in the URL, it will be available in the component, otherwise, it will be undefined.

      Route parameters provide a flexible way to handle dynamic data in your Angular application. They allow you to create routes that can be easily customized and provide a seamless user experience by reflecting the current state of the application in the URL.

79. ### What is lazy loading?
    Lazy loading in Angular is a design pattern and technique used to improve the performance of an application by loading modules and components only when they are needed. Instead of loading all modules at the start, lazy loading defers the loading 
    of certain modules until they are required, reducing the initial load time and improving the user experience.

    ```javascript
	const routes: Routes = [
	  {
	    path: 'customers',
	    loadChildren: () => import('./customers/customers.module').then(module => module.CustomersModule)
	  },
	  {
	    path: 'orders',
	    loadChildren: () => import('./orders/orders.module').then(module => module.OrdersModule)
	  },
	  {
	    path: '',
	    redirectTo: '',
	    pathMatch: 'full'
	  }
	];
    ```
	- Reduces the initial load time of the application by loading only the necessary modules at the start.
	- Makes the application more scalable by allowing you to add more features without significantly impacting the initial load time.
    
79. ### What is authentication and authorization?

    In simple terms, authentication is the process of verifying who a user is, while authorization is the process of verifying what they have access to. Comparing these processes to a real-world example, when you go through security in an airport, you show your ID to authenticate your identity.

    In summary, authentication confirms the user's identity, while authorization determines their level of access within the system.

166. ### What is the purpose of innerHTML?
     The innerHtml is a property of HTML-Elements, which allows you to set it's html-content programmatically. Let's display the below html code snippet in a `<div>` tag as below using innerHTML binding,

     ```html
     <div [innerHTML]="htmlSnippet"></div>
     ```
     and define the htmlSnippet property from any component
     ```javascript
     export class myComponent {
       htmlSnippet: string = '<b>Hello World</b>, Angular';
     }
     ```
     Unfortunately this property could cause Cross Site Scripting (XSS) security bugs when improperly handled.

232. ### What is a provider?
     A provider is an instruction to the Dependency Injection system on how to obtain a value for a dependency(aka services created). The service can be provided using Angular CLI as below,
     ```javascript
     ng generate service my-service
     ```
     The created service by CLI would be as below,
     ```js
     import { Injectable } from '@angular/core';

     @Injectable({
       providedIn: 'root', //Angular provide the service in root injector
     })
     export class MyService {
     }
     ```
233. ### What is the recommendation for provider scope?
     You should always provide your service in the root injector unless there is a case where you want the service to be available only if you import a particular @NgModule.

234. ### How do you restrict provider scope to a module?
     It is possible to restrict service provider scope to a specific module instead making available to entire application. There are two possible ways to do it.
     1. **Using providedIn in service:**
        
         ```js
         import { Injectable } from '@angular/core';
         import { SomeModule } from './some.module';

         @Injectable({
           providedIn: SomeModule,
         })
         export class SomeService {
         }
         ```
         
     3. **Declare provider for the service in module:**
        
         ```js
         import { NgModule } from '@angular/core';

         import { SomeService } from './some.service';

         @NgModule({
           providers: [SomeService],
         })
         export class SomeModule {
         }
         ```
243. ### What is NgZone?
     Angular provides a service called NgZone which creates a zone named `angular` to automatically trigger change detection when the following conditions are satisfied.
     1. When a sync or async function is executed.
     2. When there is no microTask scheduled.
