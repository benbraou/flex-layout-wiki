Several Angular Material 1 applications: **[Material-Adaptive](https://github.com/angular/material-adaptive/tree/master/shrine)** have been implemented using custom Flexbox CSS. These efforts illustrated the needs and features within a responsive, adaptive application.

*  [Pesto](https://material-adaptive.firebaseapp.com/pesto/app/dist.html#/home)
*  [Shring](https://material-adaptive.firebaseapp.com/shrine/app/dist.html)

![screen shot 2016-11-05 at 7 26 56 am](https://cloud.githubusercontent.com/assets/210413/20029970/44c16d64-a329-11e6-9a9a-bd00561ea936.png)

Different from responsive layouts where components change sizes and positions, the concepts of Adaptive layouts 
provide for UX where  **different components** may be used for different breakpoints. 

Animations can also be extended to support MediaQuery activations: different animations will run for different viewport sizes.

Developers can use the following directives to achieve some Adaptive UX goals:

*  `fx-hide`
*  `fx-show`
*  `ngIf`

For examples of `fx-hide` usages in Adaptive layouts, please review the demo **Show & Hide Directives**:

* [Demo](https://tburleson-layouts-demos.firebaseapp.com/#/responsive)
* [Source](https://github.com/angular/flex-layout/blob/master/src/demo-app/app/docs-layout-responsive/responsiveShowHide.demo.ts#L15) 

> More examples will be presented and documented before the formal GM release.