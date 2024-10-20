# Angular Basics

```md

# Starting a New Angular Project

Before starting a new project, Node.js must be installed on your machine. Next, Angular has an official CLI tool for managing projects. It can be installed with NPM or Yarn.

```bash
# NPM
npm install -g @angular/cli
# Yarn
yarn global add @angular/cli
```

Afterward, we can create a new project with the following command:

```bash
ng new my-app
```

Angular will prompt you to configure the project. For the default settings, you can press the Enter or Return keys. During the installation process, Angular will scaffold a default project with packages for running Angular.

You can run a project with either command:

```bash
# Development
ng serve
# Production
ng build --prod
```

## Installing a Library

You'll likely install third-party libraries from other developers. Packages optimized for Angular may be installed with a special command that will install and configure a package with your project.

```bash
# Installation + Configuration
ng add @angular/material
# Installation
npm install @angular/material
```

## Creating Components

Components are the building blocks of an application. You can think of them as features that teach browsers new HTML tags with custom behavior.

```bash
# Common
ng generate component MyComponent
# Shorthand
ng g c MyComponent
```

Angular will generate the component files in a directory of the same name:

- `*.component.html` - The template that gets displayed.
- `*.component.css` - The encapsulated CSS of the component.
- `*.component.ts` - The business logic of the component.
- `*.component.spec.ts` - The test file for validating the behavior.

### Useful Command Options:

| Option           | Example                             | Description                                             |
| ---------------- | ----------------------------------- | ------------------------------------------------------- |
| `--dryrun`     | `ng g c MyComponent -d`           | Does not output the result, keeps CLI clean.            |
| `--export`     | `ng g c MyComponent --export`     | Exports the component in the module's exports.          |
| `--force`      | `ng g c MyComponent --f`          | Forces the creation of the component even if it exists. |
| `--skip-tests` | `ng g c MyComponent --skip-tests` | Skips creating the test file.                           |
| `--style`      | `ng g c MyComponent --style=scss` | Specifies a preprocessor for styles.                    |

## Lifecycle Hooks

Components emit events during their lifecycle. Here are the lifecycle hooks:

- **ngOnChanges**: Runs after input/output binding changes.
- **ngOnInit**: Runs after the component is initialized.
- **ngDoCheck**: Custom actions during change detection.
- **ngAfterContentInit**: Runs after content is initialized.
- **ngAfterContentChecked**: Runs after every content check.
- **ngAfterViewInit**: Runs after the view is initialized.
- **ngAfterViewChecked**: Runs after every view check.
- **ngOnDestroy**: Runs before the component is destroyed.

## Services

Services are objects for outsourcing logic that can be injected into components, commonly used for code reuse.

```bash
# Common
ng generate service MyService
# Shorthand
ng g s MyService
```

To make a service injectable, you must decorate it with `@Injectable()`. You can make a service injectable in:

1. **The Root Module**:

   ```typescript
   @Injectable({ providedIn: 'root' })
   export class MyService { }
   ```
2. **A Specific Module**:

   ```typescript
   @NgModule({
     providers: [MyService],
   })
   ```
3. **A Specific Component**:

   ```typescript
   @Component({
     providers: [MyService]
   })
   ```

Inject the service into a component:

```typescript
export class ExampleComponent {
 constructor(private myService: MyService) { }
}
```

## Modules

Angular modules (`@NgModule`) register components, services, directives, and pipes. The `NgModule` can include options like:

- **declarations** - List of components, directives, and pipes.
- **imports** - List of modules to import.
- **exports** - Components, directives, and pipes to export.
- **providers** - Services for dependency injection.
- **bootstrap** - Root component to bootstrap.

Example `AppModule`:

```typescript
@NgModule({
 declarations: [AppComponent],
 imports: [BrowserModule, AppRoutingModule],
 bootstrap: [AppComponent]
})
export class AppModule { }
```

## Angular Directives

### Component Directives

1. A component is completely a form of Component Directive, and it is a simple directive with its templates. These are like custom HTML elements that encapsulate their behavior and appearance, making them reusable components.

2) One of the main jobs of a component is to specify the HTML template that should be displayed when the component is used. This template defines how the component will look and what content it will display.
3) Component directives are the most commonly used type of directive in Angular projects because they allow you to create reusable and modular pieces of your web page
4) @component decorator provides additional metadata that determines how the component should be processed, instantiated, and used at runtime

### Attribute Directives

- **NgClass**: Adds/removes CSS classes.
  ```html
  <div [ngClass]="isSpecial ? 'special' : ''">This div is special</div>
  ```
- **NgStyle**: Adds/removes inline styles.
  ```html
  <div [ngStyle]="{'font-weight': 'bold'}">This is bold</div>
  ```
- **NgModel**: Adds two-way data binding.
  ```html
  <input [(ngModel)]="currentItem.name">
  ```

### Structural Directives

- **NgIf**: Conditionally includes/removes elements.
  ```html
  <p *ngIf="isActive">Hello World!</p>
  ```
- **NgFor**: Loops through arrays.
  ```html
  <div *ngFor="let item of items">{{item.name}}</div>
  ```
- **NgSwitch**: Alternative for conditional rendering.
  ```html
  <ul [ngSwitch]="food">
    <li *ngSwitchCase="'Burger'">Burger</li>
    <li *ngSwitchDefault>French Fries</li>
  </ul>
  ```

## Custom Directives

Custom directives can be created via:

```bash
# Common
ng generate directive MyDirective
# Shorthand
ng g d MyDirective
```

Example directive:

```typescript
@Directive({
 selector: '[appMyDirective]'
})
export class MyDirective {
 constructor(private elRef: ElementRef) {
   elRef.nativeElement.style.background = 'red';
 }
}
```

## Pipes

Pipes transform template data. Common pipes:

- **DatePipe**: Formats a date.
  ```html
  {{ value | date:'short' }}
  ```
- **UpperCasePipe**: Transforms text to uppercase.
  ```html
  {{ 'hello' | uppercase }}
  ```
- **CurrencyPipe**: Formats a number as currency.
  ```html
  {{ amount | currency:'USD' }}
  ```

## Decorators

Angular provides many decorators:

| Decorator                 | Example                                     | Description                                     |
| ------------------------- | ------------------------------------------- | ----------------------------------------------- |
| **@Input()**        | `@Input() myProperty`                     | Property binding.                               |
| **@Output()**       | `@Output() myEvent = new EventEmitter();` | Event binding.                                  |
| **@HostBinding()**  | `@HostBinding('class.valid') isValid;`    | Binds a host property to a directive/component. |
| **@HostListener()** | `@HostListener('click', ['$event'])`      | Subscribes to events on a host element.         |
| **@ContentChild()** | `@ContentChild(myPredicate)`              | Binds the first query result.                   |
| **@ViewChild()**    | `@ViewChild(myPredicate)`                 | Binds the first view query result.              |

```mermaid

```

## Lifecycle Hooks (Important)

Angular components have lifecycle hooks that allow you to tap into key moments of a component’s life. This is essential for handling initialization, cleanup, and dynamic changes.

1. **Key Lifecycle Hooks**:
   - **ngOnInit()**: Called once, after the component is initialized. Best for data fetching.

     ```typescript
     ngOnInit() {
       // Component initialization logic
     }
     ```
   - **ngOnChanges()**: Responds to changes in `@Input` properties.

     ```typescript
     ngOnChanges(changes: SimpleChanges) {
       // React to changes in input properties
     }
     ```
   - **ngDoCheck()**: Runs with every change detection cycle (manual change detection logic).
   - **ngAfterViewInit()**: Called after Angular fully initializes the component's view.
   - **ngOnDestroy()**: Cleanup logic (unsubscribe from observables, destroy timers, etc.).

     ```typescript
     ngOnDestroy() {
       // Cleanup logic
     }
     ```

### Focus:

- **ngOnInit** and **ngOnDestroy** are the most frequently used hooks in practical development.

---

## Services and Dependency Injection (DI)

Angular services are classes that contain business logic, data access, or state management, and they are injected into components using DI.

1. **Creating a Service**:

   ```bash
   ng generate service my-service
   ```
2. **Injecting Services**:

   - To make a service globally available, provide it in the `root` injector:

     ```typescript
     @Injectable({ providedIn: 'root' })
     export class MyService { }
     ```
   - Inject the service into a component:

     ```typescript
     constructor(private myService: MyService) { }
     ```
3. **RxJS and Services**:
   Services frequently use **RxJS Observables** for asynchronous data streams. Common patterns include:

   - `HttpClient` usage:
     ```typescript
     this.httpClient.get('/api/data').subscribe(data => {
       console.log(data);
     });
     ```
   - Sharing data between components using a **Subject** or **BehaviorSubject**:
     ```typescript
     private dataSubject = new BehaviorSubject<string>('initial data');
     currentData = this.dataSubject.asObservable();

     changeData(data: string) {
       this.dataSubject.next(data);
     }
     ```

---

## Routing and Navigation

Routing is crucial for Single Page Applications (SPA). Angular uses the **RouterModule** for navigation.

1. **Setting Up Routing**:

   - Define routes in a module using `RouterModule`:
     ```typescript
     const routes: Routes = [
       { path: '', component: HomeComponent },
       { path: 'about', component: AboutComponent },
       { path: '**', component: PageNotFoundComponent } // Wildcard route
     ];

     @NgModule({
       imports: [RouterModule.forRoot(routes)],
       exports: [RouterModule]
     })
     export class AppRoutingModule { }
     ```
2. **Router Outlet**:

   - Place `<router-outlet></router-outlet>` in your template to render the routed component.
3. **Navigation**:

   - Programmatic navigation:

     ```typescript
     this.router.navigate(['/about']);
     ```
   - Passing parameters to routes:

     ```typescript
     this.router.navigate(['/details', id]);
     ```

---

## Angular Forms

There are two main types of forms in Angular:

1. **Template-driven Forms**:

   - Relies on Angular directives in the template.

   ```html
   <form #myForm="ngForm">
     <input name="email" ngModel>
   </form>
   ```
2. **Reactive Forms**:

   - Allows programmatic control of form structure and validation using `FormGroup` and `FormControl`.

   ```typescript
   this.myForm = new FormGroup({
     email: new FormControl('', Validators.required)
   });
   ```

### Validation:

- **Built-in Validators**: `Validators.required`, `Validators.email`, etc.
- **Custom Validators**: Create reusable validation logic for forms.

---

## Observables and RxJS

Angular heavily uses **RxJS** for handling asynchronous operations such as HTTP requests, user input, or timers.

1. **Observable Creation**:

   ```typescript
   const observable = new Observable(observer => {
     observer.next('Hello');
     observer.complete();
   });
   ```
2. **Operators**:

   - **map**: Transforms the data emitted by an observable.

     ```typescript
     this.httpClient.get('/api/data')
       .pipe(map(data => data.value))
       .subscribe(result => console.log(result));
     ```
   - **switchMap**: Switches to a new observable stream (often used in HTTP calls).
3. **Subscription Management**:

   - Always **unsubscribe** from observables in `ngOnDestroy` to avoid memory leaks:
     ```typescript
     this.mySubscription = this.observable$.subscribe();

     ngOnDestroy() {
       this.mySubscription.unsubscribe();
     }
     ```

---

## HTTP Client

Angular’s `HttpClientModule` is the primary way to communicate with a backend API.

1. **Basic GET request**:

   ```typescript
   this.http.get('/api/items').subscribe(data => console.log(data));
   ```
2. **POST Request**:

   ```typescript
   this.http.post('/api/items', itemData).subscribe();
   ```
3. **Error Handling**:

   - Use the **catchError** operator to handle errors:
     ```typescript
     this.http.get('/api/items')
       .pipe(catchError(error => {
         console.error('Error:', error);
         return throwError(error);
       }));
     ```

---

## Angular Directives (Expanded)

1. **Attribute Directives**:

   - Dynamically modify the behavior or appearance of elements.
   - **NgClass**: Add/remove classes dynamically.
   - **NgStyle**: Add/remove styles dynamically.
2. **Structural Directives**:

   - **NgIf**: Add or remove DOM elements conditionally.
   - **NgFor**: Iterate over lists to dynamically generate DOM elements.

---

## Angular Testing

1. **Unit Testing with Jasmine and Karma**:

   - Unit testing is an essential part of Angular development. Angular CLI generates **spec.ts** files for components and services.

   Example:

   ```typescript
   it('should create the component', () => {
     expect(component).toBeTruthy();
   });
   ```
2. **Testing Services**:

   - Mock dependencies using `TestBed`.

   ```typescript
   beforeEach(() => {
     TestBed.configureTestingModule({
       providers: [MyService]
     });
   });
   ```

---

## Performance Optimization Tips

1. **Lazy Loading**: Load feature modules only when needed, reducing the initial load time.
   ```typescript
   { path: 'admin', load

   ```

Children: () => import('./admin/admin.module').then(m => m.AdminModule) }

```

2. **OnPush Change Detection**: Optimize performance by using `ChangeDetectionStrategy.OnPush` for components that don’t frequently change.
   ```typescript
   @Component({
     changeDetection: ChangeDetectionStrategy.OnPush
   })
```

3. **AOT (Ahead of Time) Compilation**: Use AOT for faster rendering and smaller bundles:

   ```bash
   ng build --prod --aot
   ```
4. **Preloading Modules**: Use Angular’s `PreloadAllModules` strategy to preload lazy-loaded modules after the initial load:

   ```typescript
   RouterModule.forRoot(routes, { preloadingStrategy: PreloadAllModules })
   ```

---


**## 1. What are custom elements in Angular?

Answer: Custom elements in Angular are a way to create reusable components that can be used as native HTML elements. They are based on the Web Components standard and can be used outside of Angular applications. Custom elements are created using Angular’s @angular/elements package, which allows you to convert Angular components into custom elements. This is useful for integrating Angular components into non-Angular applications or libraries.

---

## 2. What is view encapsulation in Angular?

Answer: View encapsulation in Angular controls how styles defined in a component affect the component’s view and other components. Angular provides three types of view encapsulation:

* Emulated (default): Styles are scoped to the component using attributes. Styles are applied only to the component, but they don’t affect the global styles or other components.
* ShadowDom/Native: Uses the Shadow DOM to encapsulate styles. Styles are completely isolated from the global scope and other components.
  * This mode strictly guarantees that only that component's styles apply to elements in the component's template. Global styles cannot affect elements in a shadow tree and styles inside the shadow tree cannot affect elements outside of that shadow tree.
* None: No encapsulation is applied. Styles defined in the component affect the entire application and global styles affect the component.

---

## 3. What is @ViewChild in Angular?

Answer: @ViewChild is a decorator in Angular that allows you to access and interact with a child component or element in the template. It is used to get a reference to a child component, directive, or DOM element. This is useful for performing operations on child elements, such as calling methods or accessing properties.

Example:

| import{ Component, ViewChild, ElementRef }from'@angular/core';``@Component({``selector:'app-example',``template: `<input #myInput>`})``exportclassExampleComponent{``@ViewChild('myInput') inputElement!: ElementRef;``ngAfterViewInit() {`` this.inputElement.nativeElement.focus();``}``} |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

---

## 4. What are Angular directives?

Answer: Angular directives are classes that allow you to add behavior to elements in your Angular applications. There are three main types of directives:

* Components: Directives with a template. They are the most common type and define a view and behavior.
* Structural Directives: Modify the structure of the DOM, such as *ngIf and *ngFor.
* Attribute Directives: Change the appearance or behavior of an element, such as ngClass or ngStyle.

---

## 5. What is trackBy in Angular?

Answer: trackBy is used with *ngFor to improve performance when rendering lists. It helps Angular identify which items in the list have changed, been added, or removed by providing a unique identifier for each item. This helps Angular efficiently update the DOM without re-rendering the entire list.

Example:

| `<ul>` <li *ngFor="let item of items; trackBy: trackById">{{ item.name }}`</li>``</ul>` |
| ------------------------------------------------------------------------------------------------------- |

In the Component:

| trackById(index:number,item: any):number{``returnitem.id;``} |
| -------------------------------------------------------------------------- |

---

## 6. What is Renderer2 in Angular?

Answer: Renderer2 is a service in Angular used for manipulating the DOM in a platform-independent way. It provides methods for creating, updating, and removing DOM elements, and is useful for performing DOM operations that should work across different platforms, such as server-side rendering. It helps keep your code clean and platform-agnostic.

Example:

| import{ Renderer2, ElementRef, AfterViewInit }from'@angular/core';``@Component({``selector:'app-example',``template:`<div #myDiv></div>`})``exportclassExampleComponentimplementsAfterViewInit {`` @ViewChild('myDiv') divElement!: ElementRef;`` constructor(privaterenderer: Renderer2) {}``ngAfterViewInit() {`` this.renderer.setStyle(this.divElement.nativeElement,'color','blue');``}``} |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

---

## 7. What is @HostListener in Angular?

Answer: @HostListener is a decorator in Angular that allows you to listen to events on the host element of a directive or component. It is used to handle events such as clicks, mouse movements, or any other DOM events directly on the element where the directive or component is applied.

Example:

| import{ Directive, HostListener }from'@angular/core';``@Directive({``selector:'[appHover]'``})``exportclassHoverDirective{``@HostListener('mouseover') onMouseOver() {`` console.log('Mouse is over the element');``}``} |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

---

## 8. What is @HostBinding in Angular?

Answer: @HostBinding is a decorator used in Angular to bind a property or attribute of the host element to a property of the directive or component. It allows you to dynamically set properties or attributes on the host element based on component or directive state.

Example:

| import{ Directive, HostBinding }from'@angular/core';``@Directive({`` selector:'[appHighlight]'``})``exportclassHighlightDirective{``@HostBinding('style.backgroundColor')backgroundColor:string='yellow';``} |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

---

## 9. What are inbuilt pipes in Angular?

Answer: Inbuilt pipes in Angular are built-in functions that transform data for display in templates. Some common inbuilt pipes are:

* DatePipe: Formats dates.
* CurrencyPipe: Formats numbers as currency.
* DecimalPipe: Formats numbers with decimal points.
* PercentPipe: Formats numbers as percentages.
* JsonPipe: Converts objects to JSON strings.

Example:

| `<p>`{{ today |date:'shortDate' }}`</p><br/>``<p>`{{ amount | currency:'USD' }}`</p>` |
| --------------------------------------------------------------------------- |

---

## 10. What is the async pipe in Angular?

Answer: The async pipe in Angular subscribes to an observable or promise and returns the latest value it has emitted. It also handles unsubscribing automatically when the component is destroyed. It simplifies working with asynchronous data by directly binding to the observable or promise in the template.

Example:

| <div*ngIf="data$ | async as data">`<br/>`{{ data.name }}`<br/></div>` |
| ----------------------------------------------------------- |

---

## 11. What is the need for services in Angular?

Answer: Services in Angular are used to encapsulate and share business logic, data, and functionality across components. They provide a way to separate concerns, making code more modular, reusable, and testable. Services can be injected into components and other services, allowing you to maintain a single source of truth for data and logic.

---

## 12. What is an Angular module and what are its features?

Answer: An Angular module is a container for a cohesive block of code that performs a specific task. It is defined using the @NgModule decorator and helps organize an Angular application into logical units. Features of Angular modules include:

* Declarations: Declares components, directives, and pipes that belong to the module.
* Imports: Imports other modules needed by the module.
* Exports: Makes components, directives, and pipes available to other modules.
* Providers: Registers services that can be injected throughout the module.
* Bootstrap: Defines the root component to bootstrap the application (usually used in the root module).

---

## 13. What are eagerly loaded modules and lazy-loaded modules in Angular?

Answer:

* Eagerly Loaded Modules: These modules are loaded at the application startup. They are included in the main bundle and are available immediately when the application starts.
* Lazy-Loaded Modules: These modules are loaded on demand, only when the user navigates to a route that requires them. This improves the initial load time of the application by splitting it into smaller chunks that are loaded as needed.

Example of Lazy Loading:

| constroutes: Routes = [``{ path:'admin', loadChildren: () =>import('./admin/admin.module').then(m => m.AdminModule) }``]; |
| --------------------------------------------------------------------------------------------------------------------------------------- |

---

## 14. What are different types of subjects in RxJS?

Answer: RxJS subjects are special types of observables that allow values to be multicasted to multiple observers. Types of subjects include:

* Subject: Basic implementation of a subject. It does not store values and new subscribers only receive values emitted after they subscribe.
* BehaviorSubject: Stores the latest value and emits it to new subscribers immediately. It requires an initial value.
* ReplaySubject: Stores a buffer of values and emits them to new subscribers. You can configure how many values to buffer.
* AsyncSubject: Emits the last value only when the source observable completes.

---

## 15. What are interceptors for requests and responses in Angular?

Answer: HTTP interceptors in Angular are used to modify or handle HTTP requests and responses globally. They act as middleware in the HTTP pipeline:

* Request Interceptors: Modify or add headers, authentication tokens, or other settings to outgoing HTTP requests.
* Response Interceptors: Handle or transform responses before they are returned to the application, such as logging or error handling.

Example:

| import{ Injectable }from'@angular/core';``import{ HttpInterceptor, HttpRequest, HttpHandler, HttpEvent }from'@angular/common/http';``import{ Observable }from'rxjs';``@Injectable()``exportclassAuthInterceptorimplementsHttpInterceptor {``intercept(req: HttpRequest`<any>`, next: HttpHandler): Observable<HttpEvent`<any>`> {`` constauthReq = req.clone({``headers: req.headers.set('Authorization','Bearer my-token')``});`` returnnext.handle(authReq);``}``} |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

---

## 16. What is test setup in Angular and how do you achieve code coverage for testing components and services?

Answer: Test setup in Angular involves configuring the testing environment to run unit tests for components and services. This typically includes setting up TestBed, which is Angular's testing utility that allows you to configure and instantiate components and services for testing.

Code Coverage: Code coverage tools such as Istanbul (integrated with Karma) measure how much of the code is tested by the test cases. It helps ensure that your tests cover a significant portion of your application code. Angular CLI includes built-in support for code coverage.

Example:

| import{ TestBed }from'@angular/core/testing';``import{ MyService }from'./my-service.service';``describe('MyService', () => {``let service: MyService;``beforeEach(() => {``TestBed.configureTestingModule({});``service = TestBed.inject(MyService);``});``it('should be created', () => {``expect(service).toBeTruthy();``});``}); |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Running Tests with Code Coverage:

| ng test--code-coverage |
| ---------------------- |

---

## 17. What is CanActivate, CanDeactivate, and Resolve in Angular?

Answer:

* CanActivate: Determines if a route can be activated. Used to restrict access based on conditions like authentication. It returns true or false, or an observable/promise that resolves to true or false.
* CanDeactivate: Determines if a route can be deactivated. Useful for preventing navigation away from a route with unsaved changes. It returns true or false, or an observable/promise that resolves to true or false.
* Resolve: Pre-fetches data before a route is activated. Ensures the required data is available when the component is loaded. It returns data as an observable, promise, or direct value.

Examples:

CanActivate Example:

| import{ Injectable }from'@angular/core';`<br/>`import{ CanActivate, Router }from'@angular/router';`<br/>`import{ Observable }from'rxjs';`<br/>`import{ AuthService }from'./auth.service';`<br/><br/>`@Injectable({`<br/>`providedIn:'root'`<br/>`})`<br/>`exportclassAuthGuardimplementsCanActivate {`<br/>` constructor(privateauthService: AuthService,privaterouter: Router) {}`<br/><br/>`canActivate(): Observable`<boolean>` |Promise`<boolean>` |boolean{`<br/>` if(this.authService.isAuthenticated()) {`<br/>` returntrue;`<br/>`}else{`<br/>` this.router.navigate(['/login']);`<br/>` returnfalse;`<br/>`}`<br/>`}`<br/>`} |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

CanDeactivate Example:

| import{ Injectable }from'@angular/core';`<br/>`import{ CanDeactivate }from'@angular/router';`<br/>`import{ Observable }from'rxjs';`<br/>`import{ MyComponent }from'./my.component';`<br/><br/>`@Injectable({`<br/>`providedIn:'root'`<br/>`})`<br/>`exportclassCanDeactivateGuardimplementsCanDeactivate`<MyComponent>` {`<br/>`canDeactivate(component: MyComponent): Observable`<boolean>` |Promise`<boolean>` |boolean{`<br/>` returncomponent.canDeactivate ? component.canDeactivate() :true;`<br/>`}`<br/>`} |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Resolve Example:

| import{ Injectable }from'@angular/core';``import{ Resolve, Router, ActivatedRouteSnapshot, RouterStateSnapshot }from'@angular/router';``import{ Observable, of }from'rxjs';``import{ DataService }from'./data.service';``@Injectable({``providedIn:'root'``})``exportclassDataResolverimplementsResolve`<any>` {`` constructor(privatedataService: DataService,privaterouter: Router) {}``resolve(route: ActivatedRouteSnapshot, state: RouterStateSnapshot): Observable`<any>` {`` returnthis.dataService.getData().pipe(``catchError(() => {`` this.router.navigate(['/error']);`` returnof([]);``})``);``}``} |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

**
