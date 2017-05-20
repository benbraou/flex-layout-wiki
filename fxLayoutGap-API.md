The [**fxLayoutGap** directive](https://github.com/angular/flex-layout/blob/master/src/lib/flexbox/api/layout-gap.tst#L38) should be used on to specify margin gaps on children within a flexbox container (e.g. nested within a fxLayout container).

DOM containers whose children should layout or flow as the text direction along the main-axis or the cross-axis. 

```html
<div fxLayout="row" fxLayoutGap="25px">
  <div>1. One</div> <div>2. Two</div> <div>3. Three</div> <div>4. Four</div>
</div>
```

or


```html
<div fxLayout="row">
  <div>1. One</div> <div>2. Two</div> <div>3. Three</div> <div>4. Four</div>
</div>
```

![fxLayout_row](https://cloud.githubusercontent.com/assets/210413/26279205/f0d8901c-3d72-11e7-825a-4f0223c11cb1.jpg)

```html
<div fxLayout="row" fxLayoutGap="20px">
  <div>1. One</div> <div>2. Two</div> <div>3. Three</div> <div>4. Four</div>
</div>
```

![fxLayout_row_gap](https://cloud.githubusercontent.com/assets/210413/26279206/f242a212-3d72-11e7-9929-4803ac30f75e.jpg)

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

### fxLayout Options

Shown below are the supported **fxLayout** directive values and their resulting CSS stylings on the hosting element container:

| Value | Equivalent CSS | 
| ----- | -------------- |
|  '' (default)    | `{flex-direction: row}` |
|  `row`     | `{flex-direction: row}` |
|  `row-reverse`  | `{flex-direction: row-reverse}` |
|  `column`     | `{flex-direction: column}` |
|  `column-reverse`     | `{flex-direction: column-reverse}` |

<br/>

### fxLayout Side-Effects

Changes to the fxLayout value will cause the following directives to update and modify their element stylings:

*  **fxLayoutGap**
*  **fxFlex**
*  **fxLayoutAlign**
