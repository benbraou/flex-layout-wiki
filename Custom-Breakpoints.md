Developers can easily override the default breakpoints used within Flex-Layout.

### Default Breakpoints

The default breakpoints are defined in [break-points-provider.ts](https://github.com/angular/flex-layout/blob/master/src/lib/media-query/providers/break-points-provider.ts#L15) and are registered as a provider using the `BREAKPOINTS` opaque token.

```js
/**
 *  Provider to return a list to ALL known BreakPoint(s)
 */
export const BreakPointsProvider = { // tslint:disable-line:variable-name
  provide: BREAKPOINTS,
  useValue: RAW_DEFAULTS
};
```

### Customizing with your own MediaQuery ranges

Developers should build custom providers to override this default **BreakPointRegistry** dataset provider.


### Constraints to customization

Developers have, however, **one** (1) significant constraint to the customization processes. Developers should note that each flex-layout directive has hard-coded selectors that use these specific alias. 

Consider - for example - the **[layout.ts](https://github.com/angular/flex-layout/blob/master/src/lib/flexbox/api/layout.ts#L34-L45)**
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
export class LayoutDirective extends BaseFxDirective implements OnInit, OnChanges, OnDestroy { ... }
```

These **hard-coded** responsive selectors force a requirements:

* the custom breakpoints list MUST contain the following aliases & suffixes: **xs, gt-xs, sm, gt-sm, md, gt-md, lg, gt-lg, xl**.  
* other custom aliases will not be available as selectors UNLESS the flex-layout directives classes are modified or **extended** with those additional custom selectors.

> This is a known issue and the @angular core team is considering how to appropriate address such dynamic selector features.