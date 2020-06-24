## BLOCK-readText

#### Understanding the Flex Item properties.

In the last section, we have seen all the properties and values for the flex-container. We saw how we can align the items on the "main-axis" or "cross-axis" and how to utilize the extra space inside a flex-container. Like flex-container, there are few properties that we can apply on flex-items.

The properties that can be applied to flex-items are:

`order`, `flex-grow`, `flex-shrink`, `flex-basis`, `flex`, `align-self`.

##### A. Order

The `order` property is used to reorder the flex-item within a flex-container without changing the source code in an HTML document. By default, we know that the elements are laid out according to the order in which it is written in the HTML document.

However, we can reorder the place of items on a page with `order` property in the flexbox. For example, let's say we want our first item at the end.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
    <div class="item item3">3</div>
    <div class="item item4">4</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
  }
  .item1 {
    order: 1;
  }
```

![Flexbox Order Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/order1.png)

The item-1 will at the end because of its order `1`. By default, every item has `0` value for the `order` property. The property accepts unitless value in number, it can be negative or positive. The items are reordered according to the values applied to the order property, from lowest to highest. If the order value for the items is the same then the items are laid out according to the order appeared in HTML source code.

Let's see another example where we will reorder the 4th item at the first position and 1st item at the last.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
    <div class="item item3">3</div>
    <div class="item item4">4</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
  }
  .item1 {
    order: 1;
  }
  .item4 {
    order: -1;
  }
```

![Flexbox Order Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/order2.png)

##### B. Flex Grow

The flex-grow property allows the items to grow if there is extra space inside the flex container. The property accepts unitless value in number which provides the ability to grow to the items.

By default, the value for the flex-grow property is `0`, which means the size of the item will be auto. It may accept any value but not negative. If we want the item to grow and fill the extra space inside the container, we will have to apply `flex-grow` property and set the value greater than `0`. Let's check out the property visually.

Suppose we have two items inside a flex-container and we want the items to grow in the same proportionality. Then we can set the value 1 for `flex-grow` property for the items.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;padding: 40px 50px;
    margin: 10px;
    flex-grow: 1;
  }
```

![Flex Grow Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-grow1.png)

If all the items have `flex-grow` set to `1` the extra space will be distributed equally to all the items.

If one of the items has a value of 2, the remaining space would take up twice as much space as the others.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
  }
  .item1 {
    flex-grow: 2;
  }
  .item2 {
    flex-grow: 1;
  }
```

![Flex Grow Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-grow2.png)

##### C. Flex Shrink

The `flex-shrink` property is opposite to the `flex-grow` property. It allows the items to shrink if there is no extra space in the container. For the practical view, just reduce the size of your screens. You will find the width of the items is also reducing as the size of screens is reducing.

By default, the value for `flex-shrink` property is 1. Similar to `flex-grow` property the `flex-shrink` property also accepts a unitless value but greater than `0`. Negative values are invalid.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
    flex-basis: 300px;
    flex-shrink: 1;
  }
```

Here, 1 is the default value for the `flex-shrink` property that we have applied, so the item's size will reduce as per the size of the screens. For a better understanding of `flex-shrink` property, I have also applied `flex-basis` property. The `flex-basis` property is to set the initial size of the item before the item will grow or shrink in a flex-container according to the extra space, that we will see in the next section.

![Flex Shrink Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-shrink1.png)

This is what we will see after applying `flex-shrink: 1` and `flex-basis: 300px`. Now if you will reduce the size of your screen, the item size will also reduce.

![Flex Shrink Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-shrink2.png)

However, if we set `0` value for the `flex-shrink` property the item size won't reduce as per the size of the screens. The item will overflow in the flex container.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
    flex-basis: 300px;
    flex-shrink: 0;
  }
```

![Flex Shrink Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-shrink3.png)

##### D. Flex Basis

We got a bit introduction of `flex-basis` property in the last section. The `flex-basis` property is somewhat similar to the width property, as it accepts the values(in px, %, em, rem, etc.) similar to the width property. The `flex-basis` property is applied to set a base width or size of the flex-item from where the item will grow or shrink if necessary.

By default, the value for flex-basis property is auto, which means the base size of the item will be computed based on the content inside it plus whatever the padding we will apply to the item.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
    flex-basis: 200px;
  }
```

![Flex Basis Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-basis.png)

##### Flex

The `flex` property is the shorthand property for the `flex-grow`, `flex-shrink`, and `flex-basis`.

```
  .item {
    flex: 0 1 auto;
  }
```

This is the default value for the `flex` property where the first value is for `flex-grow`, second is for `flex-shrink` and the last value is for `flex-basis`. The last two value for flex property is optional.

```
  .item {
    flex:  1;
  }
```

Here, 1 is the value for the flex-grow property, and the values for `flex-shrink` and `flex-basis` will be automatically set to the default.

It's better to go with the `flex` shorthand property, instead of applying `flex-grow`, `flex-shrink`, and `flex-basis` individually.

##### F. Align Self

The `align-self` property is exactly similar to align-items property. It accepts all the same values as the `align-items` accepts. The only difference is that the `align-self` property is applied to the flex-items but the `align-items` property is applied to the flex container.

```
  .container {
    align-self: auto || stretch || flex-start || flex-end || center || baseline;
  }
```

Also, we all know from the above discussion that "align" always works on the "cross-axis", therefore we must have some extra space on the "cross-axis".

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
    <div class="item item3">2</div>
  </div>

  .container {
    display: flex;
    height: 350px;
    align-items: flex-start;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
  }
```

###### Auto

The `auto` value for `align-self` property inherits, whatever the value is set for `align-items` in the flex-container. If it is `flex-star`, the `align-self` value will be also `flex-start`.

```
  .item3 {
    align-self: auto;
  }
```

![Flexbox, align-self: auto](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/item-start.png)

###### Stretch

The `stretch` property is to stretch out the size of individual items on the "cross-axis" to fill the extra space.

```
  .item3 {
    align-self: stretch;
  }
```

![Flexbox, align-self: stretch](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/item-stretch.png)

###### Flex Start

The item will be aligned from the starting point on the "cross-axis".

```
  .item3 {
    align-self: flex-start;
  }
```

![Flexbox, align-self: flex-start](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/item-start.png)

###### Flex End

The item will be aligned towards the endpoint on the "cross-axis".

```
  .item3 {
    align-self: flex-end;
  }
```

![Flexbox, align-self: flex-start](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/item-end.png)

###### Center

The item will be aligned at the center on the "cross-axis".

```
  .item3 {
    align-self: center;
  }
```

![Flexbox, align-self: center](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/item-center.png)

###### Baseline

We have already seen baseline value for align-items property for the "flex-container". The baseline value for `align-self` property also works in the same way.

```
  .item3 {
    align-self: baseline;
  }
```

![Flexbox, align-self: baseline](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/item-baseline.png)

> Note: float, clear, and vertical-align do not affect a flex item.

