```html
<div class="containerX" >
        <div class="container">
            <div>flex: 1 1 5em;</div>
            <div></div>
            <div></div>
            <div></div>
        </div>
        <div class="container" >
            <div></div>
            <div [fx-flex]="calc2Cols"> flex: 2 2 calc(10em + 10px); </div>
            <div></div>
        </div>
        <div class="container" >
            <div [fx-flex]="calc2Cols"> flex: 2 2 calc(10em + 10px); </div>
            <div></div>
            <div></div>
        </div>
        <div class="container">
            <div></div>
            <div></div>
            <div [fx-flex]="calc2Cols"> flex: 2 2 calc(10em + 10px); </div>
        </div>
        <div class="container">
            <div [fx-flex]="calc3Cols" class="col3">  flex: 3 3 calc(15em + 20px); </div>
            <div></div>
        </div>
        <div class="container">
            <div></div>
            <div [fx-flex]="calc3Cols" class="col3">  flex: 3 3 calc(15em + 20px); </div>
        </div>        
      </div>
```