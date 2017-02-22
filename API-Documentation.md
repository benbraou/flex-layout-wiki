## HTML API (Declarative)

Below are the links to the documentation pages for each directive within the **@angular/flex-layout** API.

#### Containers

API for container elements [with 1 or more nested child elements]:

* **[fxLayout]()**: <br/>Defines the flow order of child items within a flexbox container.<br/>e.g. `<div fxLayout="column">  </div>`<br/>&nbsp;
* **[fxLayoutWrap]()**  : <br/>Defines if child items appear on a single line or on multiple lines within a flexbox container.<br/>e.g. `<div fxLayoutWrap> </div>`<br/>&nbsp;
* **[fxLayoutGap]()**:<br/>Defines if child items within a flexbox container should have a gap. <br/>e.g. `<div fxLayoutGap="10px">  </div>`<br/>&nbsp;
* **[fxLayoutAlign]()**:<br/>Defines how flexbox items are aligned according to both the main-axis and the cross-axis, within a flexbox container. <br/><span style="font-size:0.7em;">e.g. </span>`<div fxLayoutAlign="start stretch">  </div>`


<br/>
#### Child Elements within Containers

API for elements nested within FlexBox container elements:

* **[fxFlex](https://github.com/angular/flex-layout/wiki/fxFlex-API)**<br/>This markup specifies the resizing of its host element within a flexbox container flow.<br/>e.g. `<div fxFlex="1 2 calc(15em + 20px)"></div>`

* **[fxFlexOrder]()**<br/>Defines the order of a flexbox item. <br/>e.g. `<div fxFlexOrder="2"></div>`

* **[fxFlexOffset]()**<br/>Offset a flexbox item in its parent container flow layout. <br/>e.g. `<div fxFlexOffset="20px"></div>`

* **[fxFlexAlign]()**<br/>Works like fxLayoutAlign, but applies only to a single flexbox item, instead of all of them. <br/>e.g. `<div fxFlexAlign="center"></div>`

* **[fxFlexFill]()**<br/> Maximizes width and height of element in a layout container <br/>e.g. `<div fxFlexFill></div>`




<br/>

## JavaScript API (Imperative)

The programmatic API for **flex-layout** is deliberately minimized. 


