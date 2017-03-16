The **fxShow** directive allows developers to dynamically and/or responsively show/hide the hosting element. The fxShow logic defaults to **showing** an element.


1) Flex-Layout supports **STATIC** API for responsive layouts  using the API **without** `.<xxx>` alias suffices: fxShow, fxHide, etc. These are applied regardless of the viewport size; unless overrriden by a registered adaptive API.

*  fxShow (without a value) means use the origin display style value
*  fxHide (without a value) means "display:none"
*  fxShow="false" means "display:none" and hide it.
*  fxHide="false" means use the original display value (should no longer be hidden)
  > fxHide is the inverse of fxShow 

2) Flex-Layout provides a **RESPONSIVE** API for dynamic adaptive layouts. This is simply using the the static API with mediaQuery aliase suffices.
e.g.  
*  **fxShow.gt-sm**, 
*  **fxHide.lg**, etc.  

When a mediaQuery range activates, the directive instances will be notified. If the current activate mediaQuery range (and its associated alias) are not used, then the static API value is restored as the fallback value.

The *fallback* solution uses a **`largest_range-to-smallest_range`** search algorithm. Consider the following:

```html
<div fxShow.sm="false"  fxShow.gt-md="false" fxShow="true" ></div>
```

*  When the `lg` range is activated (by viewport resizing,etc) the div is **hidden** since the `gt-md` is used as the closest descending fallback value.
*  When the `md` range is activated, the div is **shown** since the static API is the closest descending matching condition.
*  When the `sm` range is activated the div is **hidden**.

> Please note that there is no left-to-right precedence. This is an incorrect interpretation..