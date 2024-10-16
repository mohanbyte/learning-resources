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

This guide now covers a more comprehensive range of Angular concepts, including deeper insights into critical areas like services, lifecycle hooks, RxJS, and performance optimization. Let me know if any specific topics need further expansion or examples!
