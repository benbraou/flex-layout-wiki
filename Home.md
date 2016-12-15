# Flex Layout

Angular Flex Layout provides a sophisticated layout API using FlexBox CSS + mediaQuery. This module provides Angular 
developers with component layout features using a custom Layout API, mediaQuery observables,and injected DOM 
flexbox-2016 css stylings.  

The Layout engine intelligently automates the process of applying appropriate FlexBox CSS to browser view hierarchies. This automation also addresses many of the complexities and workarounds encountered with the traditional, manual, CSS-only application of Flexbox CSS. 

![css3-flexbox-model](https://cloud.githubusercontent.com/assets/210413/20034148/49a4fb62-a382-11e6-9822-42b90dec69be.jpg)


The Angular Flexbox Layout features enable developers to organize UI page elements in row and column structures with 
alignments, resizing, and padding. These layouts can be nested and easily used with hierarchical DOM structures. 
Since the Layout applies/injects **Flexbox CSS**, DOM elements will fluidly update their positioning and sizes as the  viewport size changes. 

```html
<div class="flex-container" fx-layout="row" fx-layout-align="center center">
  <div class="flex-item"></div>
  <div class="flex-item"></div>
  <div class="flex-item"></div>
</div> 
```
> The above Flex Layout usages do not require any external stylesheets nor any custom CSS programming. The Angular directives do all the work of *magically* setting the flexbox css.

Integrating **mediaQuery** features into the Layout engine enables the API to be **Responsive**: DOM elements can adjust 
layout-directions, visibility, and sizing constraints based on specific viewport sizes such as desktop or mobile devices. 

Angular Flex Layout is a pure-Typescript Layout engine; unlike the pure CSS-only implementations published in other Flexbox libraries   and the JS+CSS implementation of Angular Material v1.x Layouts. 

*  This implementation of Flex Layouts is independent of Angular Material (v1 or v2).
*  This implementation is currently only available for Angular applications.


----

### Useful Resources

*  Getting Started 
*  Fast Start with Builds
*  Using Flex-Layout with Angular CLI

----

<br/>


#### Implementation

The Angular 2 architecture for Layouts eliminates `all` external Flexbox stylesheets and SCSS files formerly used 
in the Angular Material 1 Layout implementations.  This is pure typescript- Angular Layout engine that is 
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

is transformed with inline, injected styles:

```html
<div fx-layout="row" fx-layout-align="center center"
      style="display: flex; flex-direction: row; max-width: 100%; box-sizing: border-box; justify-content: center; align-content: center; align-items: center;">
  <div>one</div>
  <div>two</div>
  <div>three</div>
</div>
```


![ng2layouts_classdiagram](https://cloud.githubusercontent.com/assets/210413/19878402/04fc9e40-9fb6-11e6-9bd7-86a65862a334.png)


#### Summary

Compared to the Layout API in Angular Material v1.x, this codebase easier to maintain and debug, other more important benefits have been realized:

*  Independent of Angular Material 
*  No external CSS requirements
*  Use provider to supply custom breakpoints
*  Notifications for breakpoints changes
  *  Includes workaround for MediaQuery issues with **overlapping** breakpoints
*  Support (future) for Handset/Tablet and Orientation breakpoints
*  Support for **ANY** Layout injector value (instead of increments for 5)
*  Change detection for Layout injector values
*  MediaQuery Activation detection 
*  Support for raw values or interpolated values
*  Support for raw, percentage or px-suffix values


