## Angular

### What and why?

- client side framework
- provides right tools 
- defines how it should be designed and how the code should be organized - nemmere at vedligholde
- Feature
  - databinding
  - directives

### Basic

- 1 module in 1 file. Can be many classes in 1 module
- `export class` just means `public class`. That means use class outside the module
- **notations** called **decorators**. Just object with attributes

### Data binding

- **Interpolation** (one way)  
  -  `User Name: {{username}}` 
  - takes value of username and show in the browser
  - **one way** data binding:  **property -> view** 
- **Event binding**
  - `(click)=handleLogin()`
  - bind event with component event method
- **Two way data binding**
  - `[(ngModel)]="username"`
  - Banana in the box approach
  - every time the value is changed is bound back to a component property
  - tighten directly: **property <-> view** 
  - made of two parts. 
    - property binding `[ngModel]`
    - event binding `(ngModelChange)`

### Directives
- `ngModel`
- extended meaning that is represented in HTML. On the top what is available in HTML
- Directives associated with `modules`

### Dependency injections

- `consturtor(private router: Router){}` - find a router and inject to this component
- it is enough. `router` now is available as a member variable

### Modules

- Angular application is build of modules
- Any feature we would like to use from angular, we need import in `app.module.ts`
- Angular modules used to group components
- Group of components
- If use want to reuse the component, you have to import module
- All `.ts` and `.js` files are JavaScript Modules
- `AppModule` is the root module

### Routes

- navigate from one component to another

### `routerLink`

- uses instead of `href` in order to build **single page app**
- `href` reloads all page, so **never**

### Service

- `@Injectable` 

### `canActivate` and RouteGuard
- only authenticated users can reach that route

### Observable

- one of best approaches of implementing **asynchronous call** 
- just declaring, what needs to be done, when the successful/ error comes back. 
- `subscribe` what we should do, when response is back

### Private attributes
https://coryrylan.com/blog/private-methods-and-properties-in-typescript-classes

https://medium.com/@martin_hotell/10-typescript-pro-tips-patterns-with-or-without-react-5799488d6680

