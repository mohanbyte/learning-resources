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

A component is completely a form of Component Directive, and it is a simple directive with its templates. These are like custom HTML elements that encapsulate their behavior and appearance, making them reusable components.

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

```

```
