## HTML API (Declarative)

Below are the links to the documentation pages for each directive within the **@angular/flex-layout** API.

#### Containers

API for container elements [with 1 or more nested child elements]:

* **fxLayout**: <br/>Defines the flow order of child items within a flexbox container.<br/>`<div fxLayout="column">  </div>`
* **fxLayoutWrap**  : <br/>Defines if child items appear on a single line or on multiple lines within a flexbox container.<br/>`<div fxLayoutWrap> </div>`
* **fxLayoutGap**:<br/>Defines if child items within a flexbox container should have a gap using `margin-right` or `margin-left`. `<div fxLayoutGap="10px">  </div>`

<br/>
#### Child Elements within Containers

API for elements nested within FlexBox container elements:

* **[fxFlex](https://github.com/angular/flex-layout/wiki/fxFlex-API)**<br/> This markup specifies the resizing of its host element within a flexbox container flow.<br/>e.g. `<div fxFlex="1 2 calc(15em + 20px)"></div>`


<br/>

## JavaScript API (Imperative)

The programmatic API for **flex-layout** is deliberately minimized. 


