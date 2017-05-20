The [**fxLayoutGap** directive](https://github.com/angular/flex-layout/blob/master/src/lib/flexbox/api/layout-gap.tst#L38) should be used on to specify margin gaps on children within a flexbox container (e.g. nested within a fxLayout container).

*  `margin-right` used when the parent container `flex-direction` == "row" 
*  `margin-bottom` used when the parent container `flex-direction` == "column" 

> Note that the last child item will **NOT** have a margin gap specified; only the inside gaps are specified.

<br/>

## Examples:

#### Flex-Direction: Row

```html
<div fxLayout="row">
  <div>1. One</div> <div>2. Two</div> <div>3. Three</div> <div>4. Four</div>
</div>
```
![lg_1](https://cloud.githubusercontent.com/assets/210413/26279226/7d1633c2-3d73-11e7-8378-4eaca05a78a0.jpg)

```html
<div fxLayout="row" fxLayoutGap="20px">
  <div>1. One</div> <div>2. Two</div> <div>3. Three</div> <div>4. Four</div>
</div>
```

![lg_2](https://cloud.githubusercontent.com/assets/210413/26279227/7d1660c2-3d73-11e7-94a2-b604ba319cbe.jpg)

#### Flex-Direction: Column


```html
<div fxLayout="column" >
  <div>1. One</div> <div>2. Two</div> <div>3. Three</div> <div>4. Four</div>
</div>
```
![fxLayout_column](https://cloud.githubusercontent.com/assets/210413/26279208/f3ea70a4-3d72-11e7-83df-59b2e586d833.jpg)

```html
<div fxLayout="column" fxLayoutGap="20px">
  <div>1. One</div> <div>2. Two</div> <div>3. Three</div> <div>4. Four</div>
</div>
```
![fxLayout_column_gap](https://cloud.githubusercontent.com/assets/210413/26279209/f55fa1d4-3d72-11e7-96b8-27d5604c2c72.jpg)

<br/>



### Using fxLayoutGap with **Wrap**

When using `fxLayoutWrap` to wrap rows or columns, developers should account for the gap sizes when specifying the child item sizes (using fxFlex).

> fxLayoutGap does not track whether `column-reverse` or `row-reverse` are used.