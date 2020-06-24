## BLOCK-readText

### FLEXBOX

There is currently a new specification like `flex` to best layout our pages, other than floats. Flexbox gives us complete control over the alignment, direction, order, and size of our boxes.

In the last chapter, we learned how effectively position elements on a page using `floats` and `inline-block`. For the last decade or so `floats` were the only option to layout the complex layouts. But float was never actually intended for positioning purposes, thus it comes with few pitfalls. And we have discussed all these pitfalls and how to come over it.

To overcome all these limitations `flexbox` invented. Flexbox is one of the most interesting topics of CSS. I am sure while working `flexbox` you will enjoy it.

#### What is flexbox?

Flexbox provides a more efficient way to layout elements. It gives us the ability to align the items and distribute space among the items in a container - even though the size of the elements is unknown or dynamic. With the flexbox, we get the power of flexibility(as the word flex says) to fill the available space. So that elements can easily accommodate according to the size of screens. In a flexbox container, the item expands to fill the free space as well as shrinks to prevent overflow.

#### How does the flexbox model work?

The Flexbox model comes with some sets of properties. Few properties can be applied to parent containers and a few on children items. To make use of those properties and values we need to go into the flexbox zone.

To do so, apply `display: flex` style to an element. Once you do so the element automatically becomes "Flex Container" and children inside are "Flex Item" and we are in the zone of the flexbox model. Now we can use the flexbox properties. Without setting the element's style as `display: flex`, we cannot make use of any flexbox model property.

```
  <div class="container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
  </div>

  * {
    margin: 0;
    padding: 0;
  }
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    font-size: 34px;
    margin: 10px;
  }
```

![Flexbox Concept](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/intro.png)

> #### Terminology:(Flex Container and Flex Items)
>
> While working with flexbox model, there are few basic terminologies that you need to keep in mind.
> For example `flex container` and `flex-item`.
>
> ##### 1. Flex Container
>
> The Parent element where you need to apply `display: flex`.
>
> ##### 2. Flex Items
>
> The children elements inside the flex container.
>
> ![Flexbox Container and Item](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/container-item.png)

In the flexbox model, few properties can be applied to `Flex Container` and few to `Flex Items`. Let's check out what are the properties belong to "Flex Container" and "Flex Items" and discuss them in detail.

#### Understanding the Flex Container properties.

The properties that can be applied to flex containers are:

`display`, `flex-direction`, `flex-wrap`, `flex-flow`, `justify-content`, a`lign-items`, `align-content`.

##### A. Display:

The display property is to activate the flexbox zone. Remember, without setting the `display: flex`, you cannot make use of flexbox properties and values. This is the property from where the real magics get started.

The display property can take two values:

```
  .container {
    display: flex || inline-flex;
  }

```

The display: flex works normally as we have seen earlier.

![Flexbox Concept](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/intro.png)

The `display: inline-flex` is similar to inline-block elements. Applying this value, the element covers the space according to the content it wraps.

![Inline Flex](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/inline-flex.png)

##### B. Flex Direction

Flex direction property determines the direction of the item in which they will lay down. By default when we set the property as `display: flex`, all items line up one after another horizontally. Technically, saying "horizontally" will be wrong here in the flexbox model. Instead, I must say items line up on the main axis. Now here is the time to discuss the two other terminologies i.e. main-axis and cross-axis.

> #### Terminology(main-axis and cross-axis)
>
> Actually, in the flexbox model, there are two axes: `main-axis` and `cross-axis`.
>
> ##### 1. Main Axis
>
> The `main-axis` in the flexbox model is the primary axis along which the items are laid out in the flex container.
> By default, the `main-axis` feels like "horizontal direction", from left to right.
>
> ##### 2. Cross Axis
>
> The cross-axis goes perpendicular to the `main-axis`. It feels like "vertical direction", top to bottom.
>
> ![Flexbox: Main Axis and Cross Axis](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/axis.png)

The important point is that the `main-axis` is not necessary to remain always in the horizontal direction. We can anytime interchange the direction of axes with the `flex-direction` property.

The `flex-direction` property can accept four values:

```
  .container {
    flex-direction: row || column || row-reverse || column-reverse;
  }

```

###### Row(default)

```
  .container {
    flex-direction: row;
  }
```

This is the default value for `flex-direction` property. After applying this property you won't find any changes.

![Flexbox, flex-direction: row](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/row.png)

###### Column

```
  .container {
    flex-direction: column;
  }
```

This value makes all the items in the `flex-container` laid down top to bottom. The `column` value changes the direction of the axes in the flexbox model. The `main-axis` takes the place of `cross-axis` and the cross-axis takes the place of the main-axis.

![Flexbox, flex-direction: column](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/column.png)

###### Row Reverse

```
  .container {
    flex-direction: row-reverse;
  }
```

The `row-reverse` is similar to row but this time all the items will sit from right to left means in the opposite direction.

![Flexbox, flex-direction: row-reverse](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/row-reverse.png)

###### Column Reverse

```
  .container {
    flex-direction: column-reverse;
  }
```

The `column-reverse` is also opposite to the `column` value. The item will lay down from bottom to top.

![Flexbox, flex-direction: column-reverse](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/column-reverse.png)

##### B. Flex Wrap

The `flex-wrap` property determines how the flex-container will accommodate if there are extra flex-items inside it.

Let's take a few more items inside the flex container.

```
  <div class="container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">5</div>
    <div class="item">6</div>
    <div class="item">7</div>
    <div class="item">8</div>
    <div class="item">9</div>
  </div>

  * {
    margin: 0;
    padding: 0;
  }
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    font-size: 34px;
    margin: 10px;
  }
```

![Flexbox, flex-wrap: nowrap](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-nowrap.png)

Yes! exactly this is what happens with the flexbox model if we add extra items in the container. By default, the flex-container will always accommodate all the new items in a single line, even although the browser needs to be scrolled horizontally.

For wrapping the items inside the flex container we have the `flex-wrap` property. The flex-wrap property comes with three different values:

```
  .container {
    flex-wrap: nowrap || wrap || wrap-reverse;
  }
```

###### No wrap(default)

```
  .container {
    flex-wrap: nowrap;
  }
```

The nowrap value is the default value. By default, the container has the nowrap value for the flex-wrap property, whether we apply or not. The container will always accommodate all the items in a single line even although the browser needs to be scrolled horizontally.

###### Wrap

```
  .container {
    flex-wrap: wrap;
  }
```

![Flexbox, flex-wrap: flex-wrap](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-wrap.png)

If the container does not has enough space to accommodate enough items in a single line, then `wrap` value items will automatically break into new lines.

###### Wrap Reverse

```
  .container {
    flex-wrap: wrap-reverse;
  }
```

![Flexbox, flex-wrap: wrap-reverse](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/wrap-reverse.png)

The wrap-reverse is similar to wrap value, but this value wraps the items in the reverse direction.

##### C. Flex flow

The `flex-flow` property is the shorthand property for `flex-direction` and `flex-wrap`. I hope we all know what are shorthand and longhand properties.

```
  .container {
    flex-flow: row wrap;
  }
```

The `flex-flow` property accepts two values at a time, where the first value is for the `flex-direction` and the last value is for `flex-wrap`.

##### D. Justify Content

The `justify-content` property defines how the items will be laid out on the "main-axis". It controls the alignment of the items on the "main-axis". It also helps to make use of extra space leftover in a flex container.

The justify-content property can take 6 different values:

```
  .container {
    justify-content: flex-start || flex-end || center || space-between || space-around || space-evenly;
  }
```

###### Flex Start(default)

```
  .container {
    justify-content: flex-start;
  }
```

![Flexbox, justify-content: flex-start](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/intro.png)

This is the default value of `justify-content` property where all the flex-items will start from the starting point on the "main-axis". As we can see how the flex-items are being laid out from the starting point in a flex-container.

###### Flex End

```
  .container {
    justify-content: flex-end;
  }
```

![Flexbox, justify-content: flex-end](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-end.png)

All the flex-items are laid out towards the endpoint of the "main-axis".

###### Center

```
  .container {
    justify-content: center;
  }
```

The 'center' value for 'justify-content' will center the flex-items along the "main-axis" line.

![Flexbox, justify-content: center](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/center.png)

##### Space Between

```
  .container {
    justify-content: space-between;
  }
```

The extra space in the flex container will be evenly distributed between the flex-items, where the first item in the container will stick to the starting point of the "main-axis" and the last item will stick to the endpoint of the main-axis.

![Flexbox, justify-content: space-between](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/space-between.png)

###### Space Around

```
  .container {
    justify-content: space-around;
  }
```

The extra space in the flex container will be evenly distributed around the flex-items on the "main-axis". Means on the left as well as on the right side of the flex-items there will equal amount of space.

![Flexbox, justify-content: space-around](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/space-around.png)

###### Space Evenly

```
  .container {
    justify-content: space-evenly;
  }
```

The extra space in the flex container will be distributed in such a way that, the space between any two items as well the space of the item from the edge of the container will be equal.

![Flexbox, justify-content: space-evenly](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/space-evenly.png)

##### D. Align Items

The `align-items` property is similar to `justify-content` property. The only difference is that the `align-items` property works on "cross-axis". It defines how the "flex-items" will be laid out on the "cross-axis" inside a "flex container".

The align-items property comes with four values:

```
  .container {
    align-items: stretch || flex-start|| flex-end|| center || baseline;
  }
```

###### Stretch(default)

The stretch value for the align-items property is the default value. All the "flex-items" are stretched on the "cross-axis" to fill the extra space inside a container. By default, you won't see any effect on the items, because right now there is no extra space on the "cross-axis" inside the container. Let's apply some height(let's say 350px) to the container and thereafter see the changes.

```
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
    height: 350px;
  }
```

![Flexbox, align-items: stretch](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/stretch.png)

That's how all the flex-items behave in flexbox on "cross-axis". So without applying `align-items: stretch`, to the container the items are stretched out to fill the space on the "cross-axis".

###### Flex start

```
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
    height: 350px;
    align-items: flex-start;
  }
```

As expected the flex-items will be laid out from the starting point on the "cross-axis".

![Flexbox, align-items: flex-start](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/align-start.png)

###### Flex End

```
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
    height: 350px;
    align-items: flex-end;
  }
```

As expected the flex-items will be laid out towards the endpoint on the "cross-axis".

![Flexbox, align-items: flex-end](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/align-end.png)

###### Center

```
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
    height: 350px;
    align-items: center;
  }
```

The `center` value for `align-items` property will center the flex-items along the "cross-axis" line.

![Flexbox, align-items: center](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/align-center.png)

###### Baseline

```
  <!-- HTML -->
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
    <div class="item item3">3</div>
    <div class="item item4">4</div>
  </div>

  <!-- CSS -->
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
    height: 350px;
    aign-items: baseline;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
  }
  .item1 {
    font-size: 34px;
  }
  .item2 {
    font-size: 20px;
  }
  .item3 {
    font-size: 48px;
  }
  .item4 {
    font-size: 72px;
  }
```

![Flexbox, align-items: baseline](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/baseline.png)

The `baseline` value aligns the items based on the baseline of the text. Check out the image above for understanding.

> ###### To be not confused, always remember, "justify" works along the `main-axis` and "align" works along the `cross-axis`.

##### D. Align Content

The align-content property is similar to both `justify-content` and align-items` property.

The difference is that the `justify-content` and `align-items` property works on the individual items but the `align-content` property works on the multi-line flex container. The `align-content` property aligns flex container's lines when there is extra space on the cross-axis.

If all the "flex-items" are on a single line in a container then this property does not affect.

The align-content property accepts 6 different values:

```
  .container {
    align-content: stretch || flex-start || flex-end || center || space-between || space-around;
  }
```

Let's add a few more flex items so that we have a multi-line flex-container. Remember this property does not affect single line flex-container.

```
  <div class="container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">5</div>
    <div class="item">6</div>
    <div class="item">7</div>
    <div class="item">8</div>
    <div class="item">9</div>
  </div>

  .container {
    display: flex;
    flex-wrap: wrap;
    background: #FAFFFC;
    border: 5px solid #182945;
    height: 350px;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
  }
```

###### Stretch(default)

```
  .container {
    display: flex;
    flex-wrap: wrap;
    align-content: stretch;
  }
```

The `stretch is the default value for the`align-content` property. All the items are stretched to take up the remaining space on the "cross-axis".

![Flexbox, align-content: stretch](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/content-stretch.png)

###### Flex Start

```
  .container {
    display: flex;
    flex-wrap: wrap;
    align-content: flex-start;
  }
```

All the items in a multi-line flex container will be aligned from the starting point on the "cross-axis".

![Flexbox, align-content: flex-start](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/content-start.png)

###### Flex End

```
  .container {
    display: flex;
    flex-wrap: wrap;
    align-content: flex-end;
  }
```

All the items in a multi-line flex-container will be aligned towards the endpoint on the "cross-axis".

![Flexbox, align-content: flex-end](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/content-end.png)

###### Center

```
  .container {
    display: flex;
    flex-wrap: wrap;
    align-content: center;
  }
```

Items are laid out to the `center` of the multi-line flex-container on the "cross-axis".

![Flexbox, align-content: center](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/content-center.png)

###### Space Between

```
  .container {
    display: flex;
    flex-wrap: wrap;
    align-content: space-between;
  }
```

The spaces are evenly distributed between the flex-items on the "cross-axis" as `justify-content: space-between` property works on the "main-axis".

![Flexbox, align-content: space-between](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/content-between.png)

###### Space Around

```
  .container {
    display: flex;
    flex-wrap: wrap;
    align-content: space-around;
  }
```

The spaces are evenly distributed around the flex-items on the "cross-axis" as `justify-content: space-around` property works on the "main-axis".

![Flexbox, align-content: space-around](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/content-around.png)

