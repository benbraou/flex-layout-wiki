Developers can easily override the default breakpoints used within Flex-Layout.

### Default Breakpoints

The default breakpoints are defined in [break-points-provider.ts](https://github.com/angular/flex-layout/blob/master/src/lib/media-query/providers/break-points-provider.ts#L15) and are registered as a provider using the [`BREAKPOINTS`](https://github.com/angular/flex-layout/blob/master/src/lib/media-query/providers/break-points-provider.ts#L76) opaque token.

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

---- 

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



These **hard-coded** responsive selectors present two (2) requirements:

#### (1) Required Aliases

To support the directive selectors, the custom breakpoints list MUST contain the following aliases & suffixes: 


| alias (suffix)      | fxLayout (selector)      | fxFlex (selector)       |
| ---------- | -------------- | ------------- |
|  **xs**    | fxLayout.xs    | fxFlex.xs     |
|  **gt-xs** | fxLayout.gt-xs | fxFlex.gt-xs  |
|  **sm**    | fxLayout.sm    | fxFlex.sm     |
|  **gt-sm** | fxLayout.gt-sm | fxFlex.gt-sm  |
|  **md**    | fxLayout.md    | fxFlex.md     |
|  **gt-md** | fxLayout.gt-md | fxFlex.gt-md  |
|  **lg**    | fxLayout.lg    | fxFlex.lg     |
|  **gt-lg** | fxLayout.gt-lg | fxFlex.gt-lg  |
|  **xl**    | fxLayout.xl    | fxFlex.xl     |


#### (2) Extra Aliases

If your requirements need to support additional aliases/mediaQueries that support orientation (e.g. landascape, portraint), specific devices (kindle tablets, ipads, iphones, apple watch, etc.)... developers may either:

*  modify the `mediaQuery` ranges (as shown above), or
*  add additional aliases and selectors 

<br/>

Note that any extra **custom aliases** will not be available as selectors UNLESS the flex-layout Directives classes are modified or **extended** with those additional custom selectors. 

> This is a known issue and the @angular core team is considering how to appropriately address such dynamic selector features.

Consider the **`LayoutExtDirective`** class below which provides support for the *print* and *tablet* selectors:

```js
import {Directive, Input, ElementRef, Renderer} from '@angular/core';
import {LayoutDirective} from 'flexbox/api/layout';
import {MediaMonitor} from '../../media-query/media-monitor';

@Directive({selector: `
  [fxLayout.print],
  [fxLayout.tablet.landscape],
  [fxLayout.tablet.portrait]
`})
export class LayoutExtDirective extends LayoutDirective {

  constructor(monitor: MediaMonitor, elRef: ElementRef, renderer: Renderer) {
    super(monitor, elRef, renderer);
  }

  @Input('fxLayout.print')            
  set layoutPrint(val){ this._cacheInput('layoutPrint', val); };
  
  @Input('fxLayout.tablet.landscape') 
  set layoutHTab(val) { this._cacheInput('layoutHTab', val); };
  
  @Input('fxLayout.tablet.portrait')  
  set layoutVTab(val) { this._cacheInput('layoutVTab', val); };

}

```

---- 

### Resources

*  [CSS Media Queries](http://cssmediaqueries.com/)
*  [Media Queries for Standard Devices](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/)
*  [Why you don't need device-specific Breakpoints](https://responsivedesign.is/articles/why-you-dont-need-device-specific-breakpoints)
