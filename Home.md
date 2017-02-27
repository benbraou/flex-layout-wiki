# Flex Layout

Angular Flex Layout provides a sophisticated layout API using FlexBox CSS + mediaQuery. This module provides Angular (v2.4.3 and higher) developers with component layout features using a custom Layout API, mediaQuery observables,and injected DOM flexbox-2016 css stylings.  

The Layout engine intelligently automates the process of applying appropriate FlexBox CSS to browser view hierarchies. This automation also addresses many of the complexities and workarounds encountered with the traditional, manual, CSS-only application of Flexbox CSS. 

![css3-flexbox-model](https://cloud.githubusercontent.com/assets/210413/20034148/49a4fb62-a382-11e6-9822-42b90dec69be.jpg)

### Static Layouts 

The Angular Flexbox Layout features enable developers to organize UI page elements in row and column structures with 
alignments, resizing, and padding. These layouts can be nested and easily used with hierarchical DOM structures. 
Since the Layout applies/injects **Flexbox CSS**, DOM elements will fluidly update their positioning and sizes as the  viewport size changes. 

```html
<div class="flex-container" fxLayout="row" fxLayoutAlign="center center">
  <div class="flex-item"></div>
  <div class="flex-item"></div>
  <div class="flex-item"></div>
</div> 
```

> Note: the above Flex-Layout usages do not require any external stylesheets nor any custom CSS programming. The Angular directives do all the work of *magically* setting the flexbox css styles.

### Responsive Layouts

Integrating **mediaQuery** features into the Layout engine enables the API to be **Responsive**: DOM elements can adjust layout-directions, visibility, and sizing constraints based on specific viewport sizes such as desktop or mobile devices. 

```html
<div class="flex-container" 
     fxLayout="row" fxLayout.xs="column" 
     fxLayoutAlign="center center" fxLayoutAlign.xs="start start">
  <div class="flex-item"></div>
  <div class="flex-item"></div>
  <div class="flex-item"></div>
</div> 
```

<br/>

### Using Flex-Layout

Angular Flex Layout is a pure-Typescript Layout engine; unlike the pure CSS-only implementations published in other Flexbox libraries  and the JS+CSS implementation of Angular Material v1.x Layouts. 

*  This implementation of Angular Flex Layouts is independent of Angular Material (v1 or v2).
*  This implementation is currently only available for Angular (v2.4.3 and higher) applications.

<br/>

----

### Quick Links

*  [Wiki Docs](https://github.com/angular/flex-layout/wiki)
*  [Gitter Chat](https://gitter.im/angular/flex-layout)
*  [Discussion Forum](https://groups.google.com/forum/#!forum/angular-flex-layout)

Learning FlexBox

*  [CSS Flexbox Reference](http://cssreference.io/flexbox/)
*  [Learning How Flexbox Works](https://medium.freecodecamp.com/even-more-about-how-flexbox-works-explained-in-big-colorful-animated-gifs-a5a74812b053#.dfi1sit87)
*  [Complete Guide to FlexBox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

Developers

*  [API Documentation](https://github.com/angular/flex-layout/wiki/API-Documentation)
*  [Developer Setup](https://github.com/angular/flex-layout/wiki/Developer-Setup)
*  [Builds + Fast Start](https://github.com/angular/flex-layout/wiki/Fast-Starts)
*  [Integration with Angular CLI](https://github.com/angular/flex-layout/wiki/Integration-with-Angular-CLI)
*  [Webpack Configuration](https://github.com/angular/flex-layout/wiki/Webpack-Configuration)

Demos 

*  [Explore Online](https://tburleson-layouts-demos.firebaseapp.com/)
*  [Source Code](https://github.com/angular/flex-layout/blob/master/src/demo-app/app/demo-app-module.ts)

Templates

*  [Plunkr Template](https://plnkr.co/edit/h8hzyoEyqdCXmTBA7DfK?p=preview)

----


### Why choose Flex-Layout

While other Flexbox CSS libraries are implementations of:

* pure CSS-only implementations, or 
* the JS+CSS Stylesheets implementation of Angular Material v1.x Layouts.

Angular Flex Layout - in contrast - is a pure-Typescript UI Layout engine with an implementation that: 

*  uses HTML attributes (aka Layout API) to specify the layout configurations
*  is currently only available for Angular (v2.x or higher) Applications.
*  is independent of Angular Material (v1 or v2).
*  requires no external stylesheets.
*  requires Angular v2.4.3 or higher.

<br/>

### Browser Support

<a href="http://caniuse.com/#feat=flexbox" target="_blank">
![caniuseflexbox](https://cloud.githubusercontent.com/assets/210413/21288118/917e3faa-c440-11e6-9b08-28aff590c7ae.png)
</a>

<br/>


### Featured Demo

One of the hardest features to implement is a grid layout with specific column spans. Our online demo shows how easy this is!

Live Demo:

<a href="https://tburleson-layouts-demos.firebaseapp.com/#/stackoverflow" target="_blank">
![screen shot 2016-12-16 at 1 00 51 pm](https://cloud.githubusercontent.com/assets/210413/21274826/bc8553f2-c38f-11e6-8188-bc7fd36026c2.png)
</a>

Source Code:

<a href="https://github.com/angular/flex-layout/blob/master/src/demo-app/app/stack-overflow/columnSpan.demo.ts#L23" target="_blank">
![screen shot 2016-12-16 at 1 05 45 pm](https://cloud.githubusercontent.com/assets/210413/21274996/6b640f8a-c390-11e6-87ac-ca85eb6c3983.png)
</a>

 
<br/>

----

### Advantages 

Compared to the Layout API in Angular Material v1.x, this codebase is easier to maintain and debug.
And other more important benefits have also been realized:

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