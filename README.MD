# [Angular Style Guide Summary](https://angular.io/guide/styleguide)
Most of the recommendations of the angular style guide are used when using `angular-cli`.

## [Single responsibility](https://angular.io/guide/styleguide#single-responsibility)
- **[Rule of One](https://angular.io/guide/styleguide#rule-of-one)**
    - **Do** define one thing, such as a service or component, per file.
    - *Consider* limiting files to 400 lines of code.
- **[Small functions](https://angular.io/guide/styleguide#small-functions)**
    - **Do** define small functions
    - *Consider* limiting to no more than 75 lines.
    
## [Naming](https://angular.io/guide/styleguide#naming)
- **[Separate file names with dots and dashes](https://angular.io/guide/styleguide#separate-file-names-with-dots-and-dashes)**
    - **Do** use dashes to separate words in the descriptive name.
    - **Do** use dots to separate the descriptive name from the type.
    - **Do** use consistent type names for all components following a pattern that describes the component's feature then its type. A recommended pattern is `feature.type.ts`.
    - **Do** use conventional type names including `.service`, `.component`, `.pipe`, `.module`, and `.directive`. Invent additional type names if you must but take care not to create too many.
- **[Symbols and file names](https://angular.io/guide/styleguide#symbols-and-file-names)**
    - **Do** use upper camel case for class names.
    - **Do** match the name of the symbol to the name of the file.
    - **Do** append the symbol name with the conventional suffix (such as `Component`, `Directive`, `Module`, `Pipe`, or `Service`) for a thing of that type.
- **[Bootstrapping](https://angular.io/guide/styleguide#bootstrapping)**
    - **Do** put bootstrapping and platform logic for the app in a file named `main.ts`.
    - **Do** include error handling in the bootstrapping logic.
- **[Components](https://angular.io/guide/styleguide#custom-prefix-for-components)**
    - **Do** use a hyphenated, lowercase element selector value (e.g. `admin-users`).
    - **Do** use a custom prefix for a component selector. For example, the prefix `toh` represents from Tour of Heroes and the prefix `admin` represents an admin feature area.
    - **Do** use a prefix that identifies the feature area or the app itself.
- **[Directives](https://angular.io/guide/styleguide#custom-prefix-for-directives)**
    - **Do** spell non-element selectors in lower camel case unless the selector is meant to match a native HTML attribute (e.g. `tohValidate`).
    - **Do** use a custom prefix for the selector of directives (e.g, the prefix toh from Tour of Heroes).
- **[Pipes](https://angular.io/guide/styleguide#pipe-names)**
    - **Do** use a lower camel case pipe name (e.g. `initCaps`).
- **[Modules](https://angular.io/guide/styleguide#angular-ngmodule-names)**
    - **Do** name the module after the feature and folder it resides in.
    - **Do** suffix a RoutingModule class name with `RoutingModule`. A `RoutingModule` is a module dedicated exclusively to configuring the Angular router. 
    - **Do** end the filename of a RoutingModule with -routing.module.ts`.
    
## [Code conventions](https://angular.io/guide/styleguide#coding-conventions)
- **[Classes](https://angular.io/guide/styleguide#classes)**
    - **Do** use upper camel case when naming classes.
- **[Constants](https://angular.io/guide/styleguide#constants)**
    - **Do** declare variables with `const` if their values should not change during the application lifetime.
    - *Consider* spelling const variables in lower camel case.
    - **Do** tolerate existing const variables that are spelled in `UPPER_SNAKE_CASE`.
- **[Interfaces](https://angular.io/guide/styleguide#interfaces)**
    - **Do** name an interface using upper camel case.
    - *Consider* naming an interface without an I prefix.
    - *Consider* using a class instead of an interface for services and declarables (components, directives, and pipes).
    - *Consider* using an interface for data models.
- **[Properties and methods](https://angular.io/guide/styleguide#properties-and-methods)**
    - **Do** use lower camel case to name properties and methods.
    - ~~Avoid~~ prefixing private properties and methods with an underscore.
- **[Import line spacing](https://angular.io/guide/styleguide#import-line-spacing)**
    - *Consider* leaving one empty line between third party imports and application imports.
    - *Consider* listing import lines alphabetized by the module.
    - *Consider* listing destructured imported symbols alphabetically.
    
## [Application structure and NgModules](https://angular.io/guide/styleguide#application-structure-and-ngmodules)
- **[LIFT](https://angular.io/guide/styleguide#lift)**
    - **Do** structure the app such that you can Locate code quickly, Identify the code at a glance, keep the Flattest structure you can, and Try to be DRY.
    - **Do** make locating code intuitive, simple and fast.
    - **Do** name the file such that you instantly know what it contains and represents.
    - **Do** keep a flat folder structure as long as possible.
    - *Consider* creating sub-folders when a folder reaches seven or more files.
    - **Do** be DRY (Don't Repeat Yourself).
    - ~~Avoid~~ being so DRY that you sacrifice readability.
- **[Overall structural guidelines](https://angular.io/guide/styleguide#overall-structural-guidelines)**
    - **Do** put all of the app's code in a folder named `src`.
    - *Consider* creating a folder for a component when it has multiple accompanying files (`.ts`, `.html`, `.css` and `.spec`).
- **[App root module](https://angular.io/guide/styleguide#app-root-module)**
    - **Do** create an NgModule in the app's root folder, for example, in `/src/app`.
    - *Consider* naming the root module `app.module.ts`.
- **[Feature modules](https://angular.io/guide/styleguide#feature-modules)**
    - **Do** create an `NgModule` for all distinct features in an application; for example, a `Heroes` feature.
    - **Do** place the feature module in the same named folder as the feature area; for example, in `/src/app/heroes`.
    - **Do** name the feature module file reflecting the name of the feature area and folder; for example, `/src/app/heroes/heroes.module.ts`.
- **[Shared feature module](https://angular.io/guide/styleguide#shared-feature-module)**
    - **Do** create a feature module named SharedModule in a shared folder; for example, `/src/app/shared/shared.module.ts` defines `SharedModule`.
    - **Do** declare components, directives, and pipes in a shared module when those items will be re-used and referenced by the components declared in other feature modules.
    - *Consider* using the name `SharedModule` when the contents of a shared module are referenced across the entire application.
    - ~~Avoid~~ providing services in shared modules. Services are usually singletons that are provided once for the entire application or in a particular feature module.
    - **Do** import all modules required by the assets in the `SharedModule`; for example, `CommonModule` and `FormsModule`.
    - **Do** declare all components, directives, and pipes in the `SharedModule`.
    - **Do** export all symbols from the `SharedModule` that other feature modules need to use.
    - ~~Avoid~~ specifying app-wide singleton providers in a `SharedModule`. Intentional singletons are OK. Take care.
- **[Core feature module](https://angular.io/guide/styleguide#shared-feature-module)**
    - *Consider* collecting numerous, auxiliary, single-use classes inside a core module to simplify the apparent structure of a feature module.
    - *Consider* calling the application-wide core module, `CoreModule`. Importing `CoreModule` into the root `AppModule` reduces its complexity and emphasizes its role as orchestrator of the application as a whole.
    - **Do** create a feature module named `CoreModule` in a core folder (e.g. `/src/app/core/core.module.ts` defines `CoreModule`).
    - **Do** put a singleton service whose instance will be shared throughout the application in the `CoreModule` (e.g. `ExceptionService` and `LoggerService`).
    - **Do** import all modules required by the assets in the `CoreModule` (e.g. `CommonModule` and `FormsModule`).
    - **Do** gather application-wide, single use components in the `CoreModule`. Import it once (in the `AppModule`) when the app starts and never import it anywhere else. (e.g. `NavComponent` and `SpinnerComponent`).
    - ~~Avoid~~ importing the `CoreModule` anywhere except in the `AppModule`.
    - **Do** export all symbols from the `CoreModule` that the `AppModule` will import and make available for other feature modules to use.
- **[Prevent re-import of the core module](https://angular.io/guide/styleguide#prevent-re-import-of-the-core-module)**
    - **Do** guard against reimporting of **CoreModule** and fail fast by adding guard logic.
    
## [Components](https://angular.io/guide/styleguide#components)
- **[Component selector names](https://angular.io/guide/styleguide#component-selector-names)**
    - **Do** use dashed-case or kebab-case for naming the element selectors of components.
- **[Components as elements](https://angular.io/guide/styleguide#components-as-elements)**
    - *Consider* giving components an element selector, as opposed to attribute or class selectors.
- **[Extract templates and styles to their own files](https://angular.io/guide/styleguide#components-as-elements)**
    - **Do** extract templates and styles into a separate file, when more than 3 lines.
    - **Do** name the template file `[component-name].component.html`, where `[component-name]` is the component name.
    - **Do** name the style file `[component-name].component.css`, where `[component-name]` is the component name.
    - **Do** specify component-relative URLs, prefixed with `./`.
- **[Decorate input and output properties](Decorate input and output properties)**
    - **Do** use the `@Input()` and `@Output()` class decorators instead of the `inputs` and `outputs` properties of the `@Directive` and `@Component` metadata.
    - *Consider* placing `@Input()` or `@Output()` on the same line as the property it decorates.
- **[Avoid aliasing inputs and outputs](https://angular.io/guide/styleguide#avoid-aliasing-inputs-and-outputs)**
    - ~~Avoid~~ input and output aliases except when it serves an important purpose.
- **[Member sequence](https://angular.io/guide/styleguide#member-sequence)**
    - **Do** place properties up top followed by methods.
    - **Do** place private members after public members, alphabetized.
- **[Delegate complex component logic to services](https://angular.io/guide/styleguide#member-sequence)**
    - **Do** limit logic in a component to only that required for the view. All other logic should be delegated to services.
    - **Do** move reusable logic to services and keep components simple and focused on their intended purpose.
- **[Don't prefix output properties](https://angular.io/guide/styleguide#dont-prefix-output-properties)**
    - ~~Avoid~~ naming events without the prefix `on`.
    - **Do** name event handler methods with the prefix `on` followed by the event name.
- **[Put presentation logic in the component class](https://angular.io/guide/styleguide#dont-prefix-output-properties)**
    - **Do** put presentation logic in the component class, and not in the template.
    
## [Directives](https://angular.io/guide/styleguide#directives)
- **[Use directives to enhance an element](https://angular.io/guide/styleguide#use-directives-to-enhance-an-element)**
    - **Do** use attribute directives when you have presentation logic without a template.
- **[HostListener/HostBinding decorators versus host metadata](https://angular.io/guide/styleguide#use-directives-to-enhance-an-element)**
    - *Consider* preferring the `@HostListener` and `@HostBinding` to the `host` property of the `@Directive` and `@Component` decorators.

## [Services](https://angular.io/guide/styleguide#services)
- **[Services are singletons](https://angular.io/guide/styleguide#services-are-singletons)**
    - **Do** use services as singletons within the same injector. Use them for sharing data and functionality.
- **[Single responsibility](https://angular.io/guide/styleguide#single-responsibility-1)**
    - **Do** create services with a single responsibility that is encapsulated by its context.
    - **Do** create a new service once the service begins to exceed that singular purpose.
- **[Providing a service](https://angular.io/guide/styleguide#providing-a-service)**
    - Do provide services to the Angular injector at the top-most component where they will be shared.
- **[Use the @Injectable() class decorator](https://angular.io/guide/styleguide#providing-a-service)**
    - **Do** use the `@Injectable()` class decorator instead of the `@Inject` parameter decorator when using types as tokens for the dependencies of a service.
    
## [Data services](https://angular.io/guide/styleguide#data-services)
- **[Talk to the server through a service](https://angular.io/guide/styleguide#talk-to-the-server-through-a-service)**
    - **Do** refactor logic for making data operations and interacting with data to a service.
    - **Do** make data services responsible for XHR calls, local storage, stashing in memory, or any other data operations.
    
## [Lifecycle hooks](https://angular.io/guide/styleguide#lifecycle-hooks)
- **[Implement lifecycle hook interfaces](https://angular.io/guide/styleguide#implement-lifecycle-hook-interfaces)**
    - **Do** implement the lifecycle hook interfaces.