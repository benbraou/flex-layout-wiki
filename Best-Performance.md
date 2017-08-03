#### Performance considerations with Tables

**@angular/flex-layout** performs extremely well for most usage scenarios EXCEPT large tables.


Developers generating dynamic tables (using `*ngFor`) should be aware of performance impacts using flex-layout directives. 

For small number of rows (eg. < 100), @angular/flex-layout is a excellent choice for layouts. Consider the table definition below were each row has column elements; each using a `fxFlex`. Since the directives apply styles inline for each element in each row, large tables may manifest performance impacts with dynamic inline stylings.

```
<div *ngFor="let obj of data" fxLayout fxLayout.xs="column" class.xs="column">
  <div fxFlex="40" >{{obj.origin}}</div>
  <div fxFlex="40" >{{obj.destination}}</div>
  <div fxFlex="20" >{{obj.price}}</div>
</div>  
```

![screen shot 2017-08-03 at 12 46 39 pm](https://user-images.githubusercontent.com/210413/28935328-d1667e58-7849-11e7-8e2d-5983b4071a1d.png)

> Dynamic-inline-styling performance impacts are especially noticeable for **column** layouts. Developers should note that FlexBox CSS with `flex-direction = "column"` requires significantly more webkit engine processing to properly adjust column heights and layout the composition.

#### Use Responsive Class API for large Tables

For **responsive table layouts** with large number of rows, developers should use the responsive `class` API to specify a flexbox CSS style class instead of inline flexbox styles. 

Below we are using the responsive `class` and `class.xs` API to specify class names.

```html
    <div *ngFor="let obj of data" class="flow row" class.xs="flow column">
      <div class="item_40" style="background-color: #ccdeee">{{obj.origin}}</div>
      <div class="item_40" style="background-color: #aaddaa">{{obj.destination}}</div>
      <div class="item_20" style="background-color: #ddaadd">{{obj.price}}</div>
    </div>  
```


```css  
.flow { 
  display: flex;  
  box-sizing: border-box;   
  -webkit-box-direction: normal;   

  .row { 
    flex-direction: row;      
    -webkit-box-orient: horizontal;   
  }

  .column { 
     flex-direction: column;   
     -webkit-box-orient: vertical;  
     height:100px;       /*  important for sizing of row heights */
     margin-bottom: 20px;   
  }
}

.item_40, .item_20 {  
  flex: 1 1 100%;   
  box-sizing: border-box;   
  -webkit-box-flex: 1; 
}

.row     .item_40 {  max-width: 40%; }
.row     .item_20 {  max-width: 20%; }

.column  .item_40 {   max-height: 40%; }
.column  .item_20 {  max-height: 20%; }
```
  
> Here is an online [Plunkr - Flex-Layout Performance](https://plnkr.co/edit/s0Hkx4S9Xc830Kzoj48V?p=preview) that demonstrates the issue (see `Use fxLayout` button) and solution (see `Use CSS` button).