## Responsive Features

To extend the [static API]() with responsive features, we first associate specific breakpoint aliases with mediaQuery values. And if we use Breakpoints as specified by Material Design:

<a href="https://material.io/guidelines/layout/responsive-ui.html" target="_blank">
![](http://material-design.storage.googleapis.com/publish/material_v_4/material_ext_publish/0B8olV15J7abPSGFxemFiQVRtb1k/layout_adaptive_breakpoints_01.png)
</a>

<br/>

We can associate breakpoints with mediaQuery definitions using breakpoint **alias(es)**:

| breakpoint | mediaQuery |
|--------|--------|
| ""    | 'screen'                                                |
| xs    | 'screen and (max-width: 599px)'                         |
| gt-xs | 'screen and (min-width: 600px)'                         |
| sm    | 'screen and (min-width: 600px) and (max-width: 959px)'  |
| gt-sm | 'screen and (min-width: 960px)'                         |
| md    | 'screen and (min-width: 960px) and (max-width: 1279px)' |
| gt-md | 'screen and (min-width: 1280px)'                        |
| lg    | 'screen and (min-width: 1280px) and (max-width: 1919px)'|
| gt-lg | 'screen and (min-width: 1920px)'                        |
| xl    | 'screen and (min-width: 1920px) and (max-width: 5000px)'|
<br/>

If we combine the breakpoint `alias` with the Layout API we can easily support Responsive breakpoints with a 
simple markup convention: the `alias` is used as **suffix** extensions to the Layout API:

```html
<api>.<breakpoint alias>="<value>"
[<api>.<breakpoint alias>]="<expression>"
```


Below is an example usage of the Responsive Layout API:

```html
<div fxLayout='column' class="zero">

  <div fxFlex="33" [fxFlex.md]="box1Width" class="one" ></div>
  <div fxFlex="33" [fxLayout]="direction" fxLayout.md="row" class="two">

    <div fxFlex="22"    fxFlex.md="10px" fxHide.lg                       class="two_one"></div>
    <div fxFlex="205"   fxFlex.md="65"                                    class="two_two"></div>
    <div fxFlex="30px"  fxFlex.md="25"   fxShow [fxHide.md]="hideBox"   class="two_three"></div>

  </div>
  <div fxFlex class="three"></div>

</div>
```

In the markup above the layout directives use both static values and expression bindings; where the values are expressed as raw, percentage, or pixel values.

<br/>


