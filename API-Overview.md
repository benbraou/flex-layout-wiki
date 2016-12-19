### API Overview

The Flex Layout features provide smart, syntactic directives to allow developers to easily and intuitively create responsive and adaptive layouts using Flexbox CSS. 

The public **Layout API** is a simply list of HTML attributes that can be used on HTML containers and elements.
An important [fundamental] concept is understanding which APIs are used on DOM containers versus APIs used on DOM elements in those containers.  

#### API for DOM containers:  

| HTML API    | Allowed values                                                          |
|--------------------|-------------------------------------------------------------------------|
|  fx-layout         | `row | column | row-reverse | column-reverse`                           |                  
|  fx-layout-wrap    | `"" | wrap | none | nowrap | reverse`                                   |                   
|  fx-layout-align   | `start|center|end|space-around|space-between` `start|center|end|stretch`|                   
|  fx-layout-margin  | %, px, vw, vh                                                           |                   
|  fx-layout-padding | %, px, vw, vh                                                           |         
|  fx-layout-gap     | %, px, vw, vh                                                           |     

#### API for DOM elements in a DOM container (with Layout attributes):   

| HTML API    | Allowed values (raw or interpolated)                                    |
|--------------------|-------------------------------------------------------------------------|
|  fx-flex           | "" , px , %, vw, vh, "<grow> <shrink> <basis>",                         |              
|  fx-flex-order     | int                                                                     |                       
|  fx-flex-offset    | %, px, vw, vh                                                           |     
|  fx-align          | `start|baseline|center|end`                                             |                   
|  fx-fill           |                                                                         |

#### API for any element: 

| HTML API    | Allowed values (raw or interpolated)                                    |
|--------------------|-------------------------------------------------------------------------|
|  fx-hide           | TRUE, FALSE, 0, ""                                                      |     
|  fx-show           | TRUE, FALSE, 0, ""                                                      |     


Shown below is sample HTML markup that uses both the container and element API:


### Static Markup Example

```html
<div fx-layout='column' class="zero">

  <div fx-flex="33"                          class="one" ></div>
  <div fx-flex="33%" [fx-layout]="direction" class="two">

    <div fx-flex="22%"    class="two_one"></div>
    <div fx-flex="205px"  class="two_two"></div>
    <div fx-flex="30"     class="two_three"></div>

  </div>
  <div fx-flex class="three"></div>

</div>
```

Flex Layout directives **assign CSS styles** directly in-line to the host element. These in-line styles override inherited styles, **ShadowDOM** styles and even ShadowDOM tree stylings on the element  `:host`

## Responsive Features

To extend the static API with responsive features, we first associate specific breakpoint aliases with mediaQuery values. And if we use Breakpoints as specified by Material Design:

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
| xl    | 'screen and (min-width: 1920px)'                        |
<br/>

If we combine the breakpoint `alias` with the Layout API we can easily support Responsive breakpoints with a 
simple markup convention: the `alias` is used as **suffix** extensions to the Layout API:

```html
<api>.<breakpoint alias>="<value>"
[<api>.<breakpoint alias>]="<expression>"
```


Below is an example usage of the Responsive Layout API:

```html
<div fx-layout='column' class="zero">

  <div fx-flex="33" [fx-flex.md]="box1Width" class="one" ></div>
  <div fx-flex="33" [fx-layout]="direction" layout.md="row" class="two">

    <div fx-flex="22"    fx-flex.md="10px" fx-hide.lg                       class="two_one"></div>
    <div fx-flex="205"   fx-flex.md="65"                                    class="two_two"></div>
    <div fx-flex="30px"  fx-flex.md="25"   fx-show [fx-hide.md]="hideBox"   class="two_three"></div>

  </div>
  <div fx-flex class="three"></div>

</div>
```

In the markup above the layout directives use both static values and expression bindings; where the values are expressed as raw, percentage, or pixel values.
