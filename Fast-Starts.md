### NPM Install

```terminal
npm install @angular/flex-layout -D
```

Next, modify your `app.module.ts` to use the `FlexLayoutModule`:

```js
import { NgModule }         from '@angular/core';
import { BrowserModule }    from '@angular/platform-browser';
import { FlexLayoutModule } from "@angular/flex-layout";

import { DemoApp }          from './demo-app/demo-app';

@NgModule({
  declarations    : [ DemoApp ],
  bootstrap       : [ DemoApp ],
  imports         : [
    BrowserModule,
    FlexLayoutModule
  ]
})
export class DemoAppModule { }
```

<br/>

### SystemJS + UMD

If your approach follows those shown on the tutorials at **angular.io**, then use the npm-installed file `@angular/flex-layout/bundles/flex-layout.umd.js` to easily add **Flex Layout** API features to your application 
(which uses SystemJS to load modules and transcompile).

Here is a Plunkr [Flex-Layout Template](https://plnkr.co/edit/h8hzyoEyqdCXmTBA7DfK?p=preview):

<a href="https://plnkr.co/edit/h8hzyoEyqdCXmTBA7DfK?p=preview" target="_blank">
![screen shot 2016-12-14 at 1 37 51 pm](https://cloud.githubusercontent.com/assets/210413/21197851/9bb2de6c-c202-11e6-9165-53c08663d788.png)
</a>

<br/>

```js
System.config({
  //use typescript for compilation
  transpiler: 'typescript',
  //typescript compiler options
  typescriptOptions: {
      // Copy of compiler options in standard tsconfig.json
      "target": "es5",
      "module": "es2015",
      "moduleResolution": "node",
      "sourceMap": true,
      "emitDecoratorMetadata": true,
      "experimentalDecorators": true,
      "noImplicitAny": true,
      "suppressImplicitAnyIndexErrors": true
  },
  meta: {
      'typescript': {
        "exports": "ts"
      }
    },  
  paths: {
    'npm:': 'https://unpkg.com/'
  },
  //map tells the System loader where to look for things
  map: {
    
    'app': './src',

    '@angular/core': 'npm:@angular/core/bundles/core.umd.js',
    '@angular/common': 'npm:@angular/common/bundles/common.umd.js',
    '@angular/compiler': 'npm:@angular/compiler/bundles/compiler.umd.js',
    '@angular/platform-browser': 'npm:@angular/platform-browser/bundles/platform-browser.umd.js',
    '@angular/platform-browser-dynamic': 'npm:@angular/platform-browser-dynamic/bundles/platform-browser-dynamic.umd.js',
    '@angular/flex-layout' : 'npm:@angular/flex-layout/bundles/flex-layout.umd.js',
    
    // other libraries
    'rxjs':                      'npm:rxjs',
    'angular-in-memory-web-api': 'npm:angular-in-memory-web-api/bundles/in-memory-web-api.umd.js',
    'typescript':                'npm:typescript@2.0.10/lib/typescript.js',    
  },
  //packages defines our app package
  packages: {
    app: {
      main: './boot.ts',
      defaultExtension: 'ts'
    },
    rxjs: {
      defaultExtension: 'js'
    }
  }
});
```

----

### Local Builds

Developers can, however, easily install this `@angular/flex-layout` library using a **local repository build** 
and a directory copy:

```console
gulp build:release
ditto ./dist/@angular/flex-layout <projectPath>/node_modules/@angular/flex-layout
```

> The expected deployment process to **npm** (and the standardized use 
of `npm i @angular/flex-layout`) is **NOT** yet available. NPM installs will be available 
after the the flex-layout v1.0.0-beta.1 release (week of December 20, 2016).

<br/>

### 1) UMD + `<script>`

Use Gulp and Rollup to build `flex-layout.umd.js` UMD:

```console
gulp build:lib
cp ./dist/@angular/flex-layout/flex-layout.umd.js  <yourProjectPath>/scripts/flex-layout.umd.js
```

Use the bundle with an external script tag in the index.html of your Angular 2 application shell:

```html
<script src="/scripts/flex-layout.umd.js"></script>

```

<br/>

### 2) Angular CLI + `@angular/flex-layout`

If you are using the Angular CLI to bundle and serve your application (using `ng serve`), 
you can use the `ngc` to build the *flex-layout* files; each with  generated metadata files. 

Copy that directory to your project's `node_modules/@angular/flex-layout` directory:

```terminal
gulp build:release
cp -rF ./dist/@angular/flex-layout <ngCLiProjectPath>/node_modules/@angular/
```

Next, modify your `app.module.ts` to use the `FlexLayoutModule`:

```js
import { NgModule }         from '@angular/core';
import { BrowserModule }    from '@angular/platform-browser';
import { MaterialModule }   from "@angular/material";
import { FlexLayoutModule } from "@angular/flex-layout";

import { DemoApp }          from './demo-app/demo-app';

@NgModule({
  declarations    : [ DemoApp ],
  bootstrap       : [ DemoApp ],
  imports         : [
    BrowserModule,
    MaterialModule,
    FlexLayoutModule
  ]
})
export class DemoAppModule { }
```


