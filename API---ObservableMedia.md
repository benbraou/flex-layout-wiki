The **ObservableMedia** is used to obtained programmatic notifications of mediaQuery activations. 

> Deactivations are not announced/published.

### Dependency Injection

Developers use DI to inject a reference to the **ObservableMedia** service:

```js
import {Subscription} from "rxjs/Subscription";
import {MediaChange, ObservableMedia} from "@angular/flex-layout";

@Component({
   selector : 'responsive-component'
})
export class MyDemo implements OnDestroy {
  private _watcher: Subscription;
  public activeMediaQuery = "";

  constructor(public media$: ObservableMedia) {
    this._watcher = media$.subscribe((change: MediaChange) => {
      this.activeMediaQuery = change ? `'${change.mqAlias}' = (${change.mediaQuery})` : "";
    });
  }

  ngOnDestroy() {
    this._watcher.unsubscribe();
  }
}
``


ObservableMedia: 
Injectable Observable used to subscribe to MediaQuery activation changes.
constructor(public watcher$:ObservableMedia ) { watcher$.subscribe(...); }