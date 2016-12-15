
Installing flex-layout with **NPM** is *not yet* available! 

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

![screen shot 2016-12-14 at 5 31 27 pm](https://cloud.githubusercontent.com/assets/210413/21205830/f58ca35c-c223-11e6-95e7-4ed90b044fb5.jpg)

<br/>

### 3) SystemJS + UMD

If your approach follows those shown on the tutorials at **angular.io**, first build the 
release with `gulp build:release`. The `./dist/@angular/flex-layout/flex-layout.umd.js` may be 
then used to easily add **Flex Layout** API features to your application 
(which uses SystemJS to load modules and transcompile).

Here is a Plunkr [Flex-Layout Template](https://plnkr.co/edit/h8hzyoEyqdCXmTBA7DfK?p=preview):

<a href="https://plnkr.co/edit/h8hzyoEyqdCXmTBA7DfK?p=preview" target="_blank">
![screen shot 2016-12-14 at 1 37 51 pm](https://cloud.githubusercontent.com/assets/210413/21197851/9bb2de6c-c202-11e6-9165-53c08663d788.png)
</a>

