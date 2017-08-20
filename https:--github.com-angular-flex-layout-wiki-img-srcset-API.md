The ImgSrcsetDirective is a smart API purposed to extend the *`<img srcset>`* attribute.


*  Image used as isolated tag: `<img>` 
*  Image used as nested tag within a `<picture>` element
  ```html
    <picture>
      <img srcset>
    </picture>
  ```

#### Isolated Img 

When **not nested** within a `<picture>` DOM element, the Image element may specify both `src` and `srcset` attributes.