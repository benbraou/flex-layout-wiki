The token **BREAKPOINTS** is an opaque token in **@angular/flex-layout** that is used to build a **Provider** for a raw list of breakpoints.

```js
import {OpaqueToken} from '@angular/core';

export const BreakPointsProvider = { 
  provide: BREAKPOINTS,
  useValue: RAW_DEFAULTS
};
```

```js
@NgModule({
  providers: [
 // MatchMedia,              // Low-level service to publish observables w/ window.matchMedia()
    BreakPointsProvider,     // Supports developer overrides of list of known breakpoints
 // BreakPointRegistry,      // Registry of known/used BreakPoint(s)
 // MediaMonitor,            // MediaQuery monitor service observes all known breakpoints
 // ObservableMediaProvider  // easy subscription injectable `media$` matchMedia observable
  ]
})
export class MediaQueriesModule {
}
```

This provider is used to return a list to ALL known BreakPoint(s)... and this list is used internal to register mediaQueries and announce mediaQuery activations.


### Custom BreakPoints

Using the **BREAKPOINTS** OpaqueToken, developers can add custom breakpoints or easily override existing breakpoints.

> NOTE: !! custom breakpoints lists MUST contain the following aliases & suffixes: [**xs, gt-xs, sm, gt-sm, md, gt-md, lg, gt-lg, xl**].

