# JavaScript API (Imperative)

# HTML API (Declarative)

## fxLayout

## fxLayoutWrap

## fxLayoutGap

## fxFlex

The **fxFlex** directive should be used on elements within a **fxLayout** container and identifies the resizing of that element within the flexbox container flow. This directive is the most powerful, smartest directive within the **flex-layout** API:

Flexbox element resizing leverages [three (3) features](http://cssreference.io/flexbox/):

* flex-grow:  defines how much a flexbox item should **grow** if there's space available
* flex-shrink: defines how much a flexbox item should **shrink** if there is **not enough** space available.
* flex-basis: defines the initial size of a flexbox item.

Flex-Layout supports two (2) usages of the the **fxFlex** directive: short-form & long-form:

*  The **long-form** enables the developer to specify the grow, shrink, and basis values inline.
  *  fxFlex="1 1 52%"
  *  fxFlex="3 3 calc(15em + 20px)"
  *  fxFlex="1 1 auto"
*  The **short-form** enables developers to specify only the flex-basis and uses defaults for the shrink and grow options: (default values == 1).
  *  fxFlex
  *  fxFlex="2 2 calc(10em + 10px);"
  *  fxFlex="102px"




