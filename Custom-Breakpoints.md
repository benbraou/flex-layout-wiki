Developers can easily override the default breakpoints used within Flex-Layout.

### Default Breakpoints

The default breakpoints are defined in [break-points-provider.ts](https://github.com/angular/flex-layout/blob/master/src/lib/media-query/providers/break-points-provider.ts#L15) and are registered as a provider using the `BREAKPOINTS` opaque token.

```js
/**
 *  Provider to return a list to ALL known BreakPoint(s)
 */
export const BreakPointsProvider = { 
  provide: BREAKPOINTS,       // opaque token
  useValue: RAW_DEFAULTS      // raw object list
};
```

Please review the wiki [Responsive API](https://github.com/angular/flex-layout/wiki/API-Overview#responsive-features) to review the specific, default breakpoint range values and the alias suffices used.

### Customizing with your own @media query ranges

Developers should build custom providers to override the default **BreakPointRegistry** provider.

```js
import {NgModule } from '@angular/core';
import { RAW_DEFAULTS, BreakPoint } from '@angular/flex'

@NgModule({
  providers: [
    // register a custom provider
    {
      provide : BREAKPOINTS,
      useFactory : function customizeBreakPoints() {
          return RAW_DEFAULTS
            .map((it:BreakPoint) => {
              // For mobile and tablet, reset ranges
              switch(it.alias) {
                case 'xs' : 
                  it.mediaQuery =  '(max-width: 470px)';                        
                  break;
                case 'sm' : 
                  it.mediaQuery =  '(min-width: 471px) and (max-width: 820px)'; 
                  break;
              }
            });
      }
    }
  ]
})
export class MyBreakPointsModule { }
```


### Constraints to customization

Developers have, however, **one** (1) significant constraint to the customization processes. 

Developers should note that each flex-layout directive has hard-coded selectors that use these specific alias. Consider, for example, the **[layout.ts](https://github.com/angular/flex-layout/blob/master/src/lib/flexbox/api/layout.ts#L34-L45)** directive:

```js
@Directive({selector: `
  [fxLayout],
  [fxLayout.xs],
  [fxLayout.gt-xs],
  [fxLayout.sm],
  [fxLayout.gt-sm],
  [fxLayout.md],
  [fxLayout.gt-md],
  [fxLayout.lg],
  [fxLayout.gt-lg],
  [fxLayout.xl]
`})
export class LayoutDirective extends BaseFxDirective { 
 ... 
}
```

---- 

These **hard-coded** responsive selectors force a requirements:

##### Required Aliases

To support the directive selectors, the custom breakpoints list MUST contain the following aliases & suffixes: 
  *  **xs**, 
  *  **gt-xs**, 
  *  **sm**, 
  *  **gt-sm**, 
  *  **md**, 
  *  **gt-md**, 
  *  **lg**, 
  *  **gt-lg**, 
  *  **xl**

##### Extra Aliases

Other custom aliases will not be available as selectors UNLESS the flex-layout directives classes are modified or **extended** with those additional custom selectors.

> This is a known issue and the @angular core team is considering how to appropriate address such dynamic selector features.