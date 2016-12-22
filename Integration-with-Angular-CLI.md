Using Flex-Layout with the the Angular CLI is easy.

## Install the CLI
 
 ```bash
 npm install -g angular-cli
 ```
 
## Create a new project
 
 ```bash
 ng new my-project
 ```

The new command creates a project with a build system for your Angular app.

## NPM Install Angular Flex-Layout components  

```bash
npm install --save @angular/flex-layout
```

## Import the Angular Flex-Layout NgModule
  
**src/app/app.module.ts**
```ts
import { FlexLayoutModule } from '@angular/flex-layout';
// other imports 
@NgModule({
  imports: [FlexLayoutModule.forRoot()],
  ...
})
export class PizzaPartyAppModule { }
```

## Configuring SystemJS
If your project is using SystemJS for module loading, you will need to add `@angular/flex-layout` 
to the SystemJS configuration:

```js
System.config({
  // existing configuration options
  map: {
    ...,
    '@angular/flex-layout': 'npm:@angular/flex-layout/bundles/flex-layout.umd.js'
  }
});
```

## Sample Angular 2 Flex-Layout projects

Developers are encouraged to review the live demos and source for the Flex-Layout Demos:

*  [Live Demos](https://tburleson-layouts-demos.firebaseapp.com/)
*  [Demo Source Code](https://github.com/angular/flex-layout/blob/master/src/demo-app/app/demo-app-module.ts)
