The token **BREAKPOINTS** is an opaque token in **@angular/flex-layout** used to build a **Provider** for a raw list of breakpoints.

```js
export const BreakPointsProvider = { 
  provide: BREAKPOINTS,
  useValue: RAW_DEFAULTS
};
```

This Provider is used to return a list to ALL known BreakPoint(s)... and this list is used internal to register mediaQueries and announce mediaQuery activations.


### Custom BreakPoints

Using the **BREAKPOINTS** OpaqueToken, developers can add custom breakpoints or easily override existing breakpoints.

> NOTE: !! custom breakpoints lists MUST contain the following aliases & suffixes: [**xs, gt-xs, sm, gt-sm, md, gt-md, lg, gt-lg, xl**].

