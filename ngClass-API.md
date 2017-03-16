The *@angular/flex-layout* [**ngClass**](https://github.com/angular/flex-layout/blob/master/src/lib/flexbox/api/class.ts) directive is a subclass of the *@angular/common* [**ngClass**](https://github.com/angular/angular/blob/master/modules/@angular/common/src/directives/ng_class.ts#L43) directive. 

### Standard Features

Traditionally **ngClass** adds and removes CSS classes on an HTML element:

The CSS classes are updated as follows, depending on the type of the expression evaluation:
 * - `string` - the CSS classes listed in the string (space delimited) are added,
 * - `Array` - the CSS classes declared as Array elements are added,
 * - `Object` - keys are CSS classes that get added when the expression given in the value evaluates to a truthy value, otherwise they are removed.

```html
<some-element [ngClass]="stringExp|arrayExp|objExp">...</some-element>

<some-element  ngClass="first second"> </some-element>
<some-element [ngClass]="['first', 'second']"> </some-element>
<some-element [ngClass]="{'first': true, 'second': true, 'third': false}"> </some-element>
<some-element [ngClass]="{'class1 class2 class3' : true}"> </some-element>
```

### Responsive Features

The Flex-Layout **ngClass** adds responsive features to also add/remove CSS classes; but only for activated breakpoints.


```html
<some-element  
     ngClass="first" 
    [ngClass.xs]="{'first':false, 'third':true}">  
</some-element>

<some-element 
    [ngClass]="['first', 'second']" 
    ngClass.gt-xs="third" >
</some-element>

<some-element 
    [ngClass]="{'class1 class2 class3' : true}" 
    [ngClass.md]="{'class1' : false, 'class4 class5':true}"> 
</some-element>
```

#### Merging Classes

Note that the default classes (specified by `class=""` and `ngClass="..."` will be preserved (and merged) into other activation class lists UNLESS the breakpoint has specified that a default class should be removed:

Below the class === "first" used all mediaQuery activations **except** for 'xs' (mobile) where it is explicitly removed;

```html
<some-element  
    ngClass="first" 
    [ngClass.xs]="{'first':false, 'third':true}">
</some-element>
```

