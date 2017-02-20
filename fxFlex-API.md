The **fxFlex** directive should be used on elements within a **fxLayout** container and identifies the resizing of that element within the flexbox container flow. **fxFlex** is essentially the FlexBox API for resizing elements in horizontal or vertical stacks. 

![css3-flexbox-model](https://cloud.githubusercontent.com/assets/210413/20034148/49a4fb62-a382-11e6-9822-42b90dec69be.jpg)

This directive is the most powerful, smartest directive within the **flex-layout** API. Flexbox element resizing leverages [three (3) features](http://cssreference.io/flexbox/):

* flex-grow:  defines how much a flexbox item should **grow** if there's space available
* flex-shrink: defines how much a flexbox item should **shrink** if there is **not enough** space available.
* flex-basis: defines the initial size of a flexbox item.

Note that the resizing occurs along the main-axis of the layout and maybe affected by the **fxLayoutAlign** options. 

> Developer's seeking details on FlexBox should review [CSS-Tricks - A Guide to FlexBox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/).

### fxFlex Attribute Usages

The **fxFlex** directive supports two (2) usages: short-form & long-form.

*  The **long-form** enables the developer to specify the grow, shrink, and basis values inline.
  *  fxFlex="1 1 52%"
  *  fxFlex="3 3 calc(15em + 20px)"
  *  fxFlex="1 1 auto"


*  The **short-form** enables developers to specify only the **flex-basis** and uses defaults for the shrink and grow options: (default values == 1).
  *  fxFlex
  *  fxFlex=""
  *  fxFlex="2 2 calc(10em + 10px);"
  *  fxFlex="102px"

Note the above examples are using static values. To use runtime expressions, developers should use the box-notation to specify 1-way DataBind (to an expression). E.g. [fxFlex]="twoColumnSpan".

### fxFlex Options

The **flex-basis** values can be pixels, percentages, calcs, em, vw, vh, or known *aliases*.

  *  fxFlex
  *  fxFlex=""
  *  fxFlex="2 2 calc(10em + 10px);"
  *  fxFlex="102px"
  *  fxFlex="auto"


Flex-basis aliases are accepted shorthand terms used to easily specify Flexbox stylings. Here are the industry mappings:


| alias | Equivalent CSS | 
| ----- | -------------- |
|  `grow`     | `{flex: 1 1 100%}` |
|  `initial`  | `{flex: 0 1 auto}` |
|  `auto`     | `{flex: <grow> <shrink> 100%}` |
|  `none`     | `{flex: 0 0 auto}` |
|  `nogrow`   | `{flex: 0 1 auto}` |
|  `noshrink` | `{flex: 1 0 auto}` |


Here is an example of a non-trivial layout using fxFlex options:

<a href="https://tburleson-layouts-demos.firebaseapp.com/#/stackoverflow" target="_blank">
![screen shot 2017-02-20 at 3 38 07 pm](https://cloud.githubusercontent.com/assets/210413/23142663/c106c196-f782-11e6-8079-9d49ba83ea3a.png)
</a>


### Additional fxFlex Stylings

**fxFlex** also auto-assign additional stylings, dependent upon the fxFlex value used and the layout, main-axis direction:

* **box-sizing** : `border-box`
* **max-width**: when direction == `row` and use fixed sizes+shrink or `0%`
* **max-height**: when direction == `column` and use fixed sizes or `0%` 
* **min-width**: when direction == `row` and use fixed sizes+grow or `0%`
* **min-height**: when direction == `column` and use fixed sizes+grow or `0%`

When a parent **fxLayout** container changes flow-direction, the **fxFlex** directive will automatically update the element's inline-styling with corrected stylings.

### Default fxFlex Values

When the Angular compiler builds an instance of the **FlexDirective**, it initializes the 

```js
@Input('fxFlex') set(val) {....} 
```

with the static value of "". **fxFlex** is the same/equivalent as **fxFlex=""**. And this empty string value is internally interpreted (by the FlexDirective) and instruction to assign an inline element-styling of

```css
flex: 1 1 0.000000001px
```

... assuming the values of *shrink* and *grow* have not been overridden from the default `1`.

> Another usage (with distinct grow and shrink values) such as `<div fxFlex fxShrink="0" fxGrow="2"></div>`
would result in an inline styling of `flex : 2 0 0.000000001px`.

This means that developers should consider the notation 

```html
<div fxFlex><div>
```

to mean 

```console
Resize the div element to fill the available space along the 
main-axis flow of its parent container!
```


----

### Known Issues with fxFlex

While Flex-Layout makes every attempt to assign smart, valid flexbox stylings... some usages and some browsers will manifest layout issues.

[CanIuse.com](http://CanIuse.com] reports and tracks many browsers issues using FlexBox; especially with **IE browsers** and **Column** stacking layouts. 

Developers should consult the **[Known Issues](http://caniuse.com/#feat=flexbox)** and the [Resources](http://caniuse.com/#feat=flexbox) sections.

<a href="http://caniuse.com/#feat=flexbox" target="_blank">
![caniuseflexbox](https://cloud.githubusercontent.com/assets/210413/21288118/917e3faa-c440-11e6-9b08-28aff590c7ae.png)
</a>