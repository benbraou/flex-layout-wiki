The injectable **ObservableMedia** service will provide mediaQuery **activations** notifications for all [registered BreakPoints](https://github.com/angular/flex-layout/wiki/Custom-Breakpoints). 

This service is essential an Observable with that exposes a feature to subscribe to mediaQuery
changes and a validator method (`isActive(<alias>)`) to test if a mediaQuery (or alias) is
currently active.

>  !! Only mediaChange activations (not deactivations) are announced by the ObservableMedia

### API

The injectable **ObservableMedia** service has three (3) APIs:

* **`subscribe**(...): Subscription`
* **`asObservable**(): Observable<MediaChange>`
* **`isActive**(query: string): boolean`


####  **`.subscribe()`**

```js
subscribe(next?: (value: MediaChange) => void,
                     error?: (error: any) => void,
                     complete?: () => void): Subscription;
```

Developers use Angular DI to inject a reference to the **ObservableMedia** service as a **constructor** parameter. 

Shown below is the service injection and the subscription to the observable: to get programmatic notifications regarding mediaQuery activations. 

```js
import {Subscription} from "rxjs/Subscription";
import {MediaChange, ObservableMedia} from "@angular/flex-layout";

@Component({
   selector : 'responsive-component'
})
export class MyDemo implements OnDestroy {
  watcher: Subscription;
  activeMediaQuery = "";

  constructor(public media: ObservableMedia) {
    this.watcher = media.subscribe((change: MediaChange) => {
      this.activeMediaQuery = change ? `'${change.mqAlias}' = (${change.mediaQuery})` : "";
      if ( change.mqAlias == 'xs') {
         this.loadMobileContent();
      }
    });
  }

  ngOnDestroy() {
    this.watcher.unsubscribe();
  }

  loadMobileContent() { 
    // Do something special since the viewport is currently
    // using mobile display sizes
  }
}
```

This class uses the BreakPoint Registry to inject alias information into the raw MediaChange
notification. For custom mediaQuery notifications, alias information will not be injected and
those fields will be ''.

> This method is useful when the developer is not interested in using RxJS operators (eg `.map()`, `.filter()`).


### API - `.asObservable()`


```js
asObservable(): Observable<MediaChange>
```

The **ObservableMedia** is not an actual **Observable**. It is a wrapper of an Observable used to publish additional methods like `isActive(<alias>). 

To access the **Observable** and use **RxJS** operators, use `.asObservable()` with syntax like `media.asObservable().filter(....)`.

> Do not forget to **import** the specific RxJS operators you wish to use!


```js
import {Subscription} from "rxjs/Subscription";
import 'rxjs/add/operator/filter';

import {MediaChange, ObservableMedia} from "@angular/flex-layout";

@Component({
   selector : 'responsive-component'
})
export class MyDemo implements OnDestroy {

  constructor(public media: ObservableMedia) {
      media.asObservable()
        .filter((change: MediaChange) => change.mqAlias == 'xs')
        .subscribe(() => this.loadMobileContent() );
  }

  ngOnDestroy() {
    this.watcher.unsubscribe();
  }

  loadMobileContent() {  }
}
```

### API - `.isActive()`

```js
isActive(query: string): boolean
```

This method is useful both for expressions in component templates and in component imperative logic.

```js
import {MediaChange, ObservableMedia} from "@angular/flex-layout";

@Component({
   selector : 'responsive-component',
   template: `
      <div class="ad-content" *ngIf="media$.isActive('xs')">
        Only shown if on mobile viewport sizes
      </div>
   `
})
export class MyDemo implements OnInit {
  constructor(public media: ObservableMedia) { }

  ngOnInit() {
    if (this.media.isActive('xs')) {
       this.loadMobileContent();
    }
  }

  loadMobileContent() { /* .... */ }
}
```