The *@angular/flex-layout* [**ngStyle**](https://github.com/angular/flex-layout/blob/master/src/lib/flexbox/api/style.ts#L53) directive is a subclass of the *@angular/common* [**ngStyle**](https://github.com/angular/angular/blob/master/modules/@angular/common/src/directives/ng_style.ts#L34) directive. 

### Standard Features

Traditionally **ngStyle** updates an HTML element inline styles (highest specificity):

The styles are updated according to the value of the expression evaluation:

 *  - keys are style names with an optional `.<unit>` suffix (ie 'top.px', 'font-style.em'),
 *  - values are the values assigned to those properties (expressed in the given unit).


```html
<some-element 
    style="color:red; font-size:12pt;"
   [ngStyle]="{'font-style': styleExp}">
 ... 
</some-element>

<some-element [ngStyle]="{'max-width.px': widthExp}">
  ...
</some-element>

<some-element [ngStyle]="objExp">
  ...
</some-element>
```

### Responsive Features

The Flex-Layout **ngClass** adds responsive features to also add/remove CSS styles for activated breakpoints.


```html
<some-element 
    style="font-size:12px; color:black; text-align:left;"
    [style.sm]="{'font-size': '16px', color: '#a63db8', 'text-align': 'center'}"
    ngStyle.md="font-size: 24px; color : #0000ff; text-align: right;">
...
</some-elment>

<some-element [ngStyle]="{'max-width.px': widthExp}">
  ...
</some-element>

<some-element [ngStyle]="objExp">
  ...
</some-element>
```

#### Merging Styles

Note that the default styles (specified by `style=""` or `ngStyle="..."`) will be preserved (and merged) into other activation class lists UNLESS the breakpoint has specified that a style should be removed (using a null value)

Below the font size and colors are changed for 'sm' and 'md' breakpoints. Yet for 'md', the `text-align` style remains the same as the default === 'left'. Deactivations of 'sm' or 'md' breakpoints to other breakpoints will result in only the default styles being re-applied.

```html
<some-element 
    style="font-size:12px; color:black; text-align:left;"
    [style.sm]="{'font-size': '16px', color: '#a63db8'}"
    ngStyle.md="font-size: 24px; color : #0000ff; text-align: right;">
  ...
</some-elment>
```

