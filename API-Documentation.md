## HTML API (Declarative)

Below are the links to the documentation pages for each directive within the **@angular/flex-layout** API.

*  **[API Overview](https://github.com/angular/flex-layout/wiki/API-Overview)**: <br/>Introduction to static and responsive API and BreakPoints details.<br/>

### Containers

API for DOM container elements [with 1 or more nested child elements]:

* **fxLayout**: <br/>Defines the flow order of child items within a flexbox container.<br/>`<div fxLayout="column">  </div>`<br/>&nbsp;
* **fxLayoutWrap**  : <br/>Defines if child items appear on a single line or on multiple lines within a flexbox container.<br/>`<div fxLayoutWrap> </div>`<br/>&nbsp;
* **fxLayoutGap**:<br/>Defines if child items within a flexbox container should have a gap. <br/>`<div fxLayoutGap="10px">  </div>`<br/>&nbsp;
* **fxLayoutAlign**:<br/>Defines how flexbox items are aligned according to both the main-axis and the cross-axis, within a flexbox container. <br/>`<div fxLayoutAlign="start stretch">  </div>`


<br/>
### Child Elements within Containers

API for DOM elements nested within FlexBox container elements:

* **[fxFlex](https://github.com/angular/flex-layout/wiki/fxFlex-API)**: <br/>This markup specifies the resizing of its host element within a flexbox container flow.<br/>`<div fxFlex="1 2 calc(15em + 20px)"></div>`

* **fxFlexOrder**: <br/>Defines the order of a flexbox item. <br/>`<div fxFlexOrder="2"></div>`

* **fxFlexOffset**: <br/>Offset a flexbox item in its parent container flow layout. <br/>`<div fxFlexOffset="20px"></div>`

* **fxFlexAlign**: <br/>Works like fxLayoutAlign, but applies only to a single flexbox item, instead of all of them. <br/>`<div fxFlexAlign="center"></div>`

* **fxFlexFill**: <br/> Maximizes width and height of element in a layout container <br/>`<div fxFlexFill></div>`


<br/>
### Special Features

API for any DOM element:

* **fxShow**: <br/>This markup specifies if its host element should be displayed (or not).<br/>`<div fxShow></div>`

* **fxHide**: <br/>This markup specifies if its host element should NOT be displayed.<br/>`<div fxHide></div>`

* **class**: <br/>Enhances the **ngClass** directive with support for mediaQuery activations. <br/>`<div [class.sm]="{'fxClass-sm': hasStyle}"></div>`

* **style**: <br/>Enhances the **ngStyle** directive with suport for mediaQuery activations. <br/>`<div [style.xs]="{'font-size.px': 10, color: 'blue'}"></div>`


<br/>

## JavaScript API (Imperative)

Most of the **@angular/flex-layout** functionality is provided via Directives. The Flex-Layou API, however, does publish three (3) important features important for programmatic purposes:

* **ObservableMedia**: <br/> Injectable Observable used to subscribe to MediaQuery activation changes.<br/>
`constructor(public watcher$:ObservableMedia ) { watcher$.subscribe(...); }`

* **BREAKPOINTS**: <br/> Opaque token used to override or extend the default breakpoints with custom MediaQuery breakpoints.<br/> `providers: [{provide: BREAKPOINTS, useValue: MY_CUSTOM_BREAKPOINTS }]`

* **BaseFxDirectiveAdapter**: <br/> Adapter class useful to extend existing Directives with MediaQuery activation features. <br/> `export class ClassDirective extends NgClass { ... }` 