```html
<div class="containerX" (click)="toggleDirection()" [fx-layout]="direction" fx-layout-wrap>
        <div class="one   flexitem "                    > 1 <div class="markup">&lt;div fx-flex-order="1"&gt;</div> </div>
        <div class="two   flexitem "  fx-flex-order="3" > 2 <div class="markup">&lt;div fx-flex-order="3"&gt;</div> </div>
        <div class="three flexitem "  fx-flex-order="5" > 3 <div class="markup">&lt;div fx-flex-order="5"&gt;</div> </div>
        <div class="four  flexitem "                    > 4 <div class="markup">&lt;div fx-flex-order="2"&gt;</div> </div>
        <div class="five  flexitem "  fx-flex-order="4" > 5 <div class="markup">&lt;div fx-flex-order="4"&gt;</div> </div>
      </div>
```