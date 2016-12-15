The Angular 2 architecture for Layouts eliminates `all` external Flexbox stylesheets and SCSS files formerly used in the Angular Material 1 Layout implementations.  

This is pure typescript- Angular Layout engine that is 
independent of Angular Material yet can be used easily within any Material 2 application.

The Layout API directives are used to create DOM element style injectors which inject specific, custom Flexbox 
CSS directly as inline styles onto the DOM element. 

For example, consider the use of the `fx-layout="row"` and `fx-layout-align="center center"` directives.

Static Markup:

```html
<div [fx-layout]="direction" fx-layout-align="center center">
  <div>one</div>
  <div>two</div>
  <div>three</div>
</div>
```

is transformed (at runtime) with inline, injected styles:

```html
<div fx-layout="row" fx-layout-align="center center"
      style="display: flex; flex-direction: row; max-width: 100%; box-sizing: border-box; justify-content: center; align-content: center; align-items: center;">
  <div>one</div>
  <div>two</div>
  <div>three</div>
</div>
```