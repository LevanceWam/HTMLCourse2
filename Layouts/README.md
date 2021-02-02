# Layouts

> In this section we are going to be looking into sizing and positioning elements on a screen.

This section will include:

- CSS Box Model
- Sizing Elements
- Overflowing
- Measurement units
- Positioning
- Floating Elements
- FlexBox & Grid Layouts
- Media queries

## CSS Box Model

> **This is a important concept in CSS**

When the browser renders a element it places that element in a invisible box. At the core of the box we have the content area. This is where the content is displayed. Following that we have padding, this is used for adding space out side of the content area. Next is the border area, if we have a border it is shown after the padding and content. Finally we have margin area, this is used to add space between different elements.

This is what we call the BoxModel.

### Margin and Padding:

A lot of people do not know how to use padding and margin properly and this is why a lot of issues occur in their layouts.

Remember that padding is the space between the content and the border. Margin is the spacing between elements.

If we inspect 2 elements that are next to eachother and have padding applied we can see that they stack or add to eachother. So if one element has 10px and the other 5px the shared px equal out to 15px.

With margin it is a little bit different. We have a concept called margin collapse, if we have 2 elements that are close to each other their margins get collapse into a single margin.

## Overflow

> Another CSS concept

So lets say we have a container with a fixed size and we have too much content in the container. The container is not fitting the entire content, this is when overflow happens. We can use the overflow property to control how overflow
should behave.

Important values:

- visible (default)
- hidden
- scroll
- auto

```css
.box {
  width: 150px;
  height: 150px;
  border: 3px solid green;

  /* will show overflow */
  overflow: visible;

  /* the extra content will be hidden */
  overflow: hidden;

  /* scroll bars will only appear if overflow happens */
  overflow: auto;

  /* 2 scroll bars a horiziontal and a vertical bar will appear */
  overflow: scroll;

  /* this will provide a scroll if needed  */
  /* this is going to hide the horizontal scroll */
  overflow: hidden auto;
}
```

## Measurement Units

> CSS measurement units

In CSS we have a few measurement units. That can be broken up into 2 catergories.

- absolute
- relative

### Absolute:

Absolute values are always fixed they never change.
examples for this include:

- px
- pt
- in
- cm
- mm

The last 4 units have to do with printing and they have nothing to do with the web.

### Relative:

Relative units are relative to something else.

For this catergory we have:

- %, (relative to the size of the container)
  - these are relative to the parent element
- vw & vh
  - both vw and vh are relative to the viewport
- em & rem
  - both are relative to the font size

\*\* Cool Tip:

if we set a rule for the html and make the font-size 62.5%
this means 62.5% of 16px = 10px;

this will make it a little easier when calculating the pxs when using rem.

```css
.box {
  /* using px values this box will stay the same size on all devices */
  /* this is known as absolute values */
  width: 100px;
  height: 100px;
}

.box2 {
  /* 50% of the width if of the parent */
  /* it will be 150px because the body is currently 300px this is going to be removed */
  width: 50%;
  height: 100px;
}

.box3 {
  width: 50%;
  /* this is not going to show a box because we did not set the height of the parent */
  height: 100%;
}

.box4 {
  /* these units will take up the width and height of the viewport */
  width: 50vw;
  height: 100vh;
}

.box5 {
  /* this will multiply the font size by 10 to give us a width */

  /* but because this element does not have a font size to go off of 
    it will inherit from the body element which will inherit from the html because body doesn't have a font-size either */

  /* so the width will be 10x16px because it is the default fontsize */
  width: 10em;
  height: 100vh;
}

.box6 {
  /* the width will now be 200px */
  font-size: 20px;
  width: 10em;
  height: 50vh;
}

.box7 {
  /* 15 x font size of the root element (html)*/
  width: 15rem;
  height: 50vh;
}
```

## Positioning

> positioning elements with css

    - relative: relative to the elements normal position other elements are not affected

    - absolute: position a element relative to the parent element

    - fixed: position a element relative to the viewport

### Position property:

now by default the position of all elements is static
this means they are not positioned they appear in their normal position

### z-index:

By setting the z-index (zed-index) property to a positive or negative value to move the box along the zed axis.

on webpages we have 3 axis:

- horizontal axis (x-axis)
- vertical axis (y axis)
- zed axis(z-axis) \* this axis represents the depth

Think of it like a line that comes from the screen towards your eyes
by default the zed index of all properties is 0. If we set it to a positive value like one it comes closer to us. If we set it to a negative value it will move away from us. The higher or lower the number on the Z axis. The higher or lower The element will move up or down to axis.

### Absolute positioning:

This is contrast to relative positioning with absolute positioning. We can position a element relative to its container.

**_so first we need to set the position of the container to
relative this is very important_**

### Fixed positioning

now sometimes we are going to want to set a element relative to the viewport
for example. A navbar that always stays on the top

```css
.boxes {
  margin-top: 20px;
  border: 3px solid lightgrey;
  /* when we want to use the absolute value the container needs to be set to relative */
  position: relative;
}

.box {
  /* this is going to set the width by multiplying by the default width */
  width: 5rem;
  height: 5rem;
}

.box-one {
  background: gold;
  /* this sets the position of this box relative to the container  */
  position: absolute;
  /* when we use 0 we do not need to specify a unit */
  right: 0;
  bottom: 0;
}

.box-two {
  background: tomato;
  /* moving the box relative to its original position */
  position: relative;
  /* adding 5rem of space to the left of the box */
  left: 3rem;
  top: 2rem;
  z-index: -1;
}
.box-three {
  background: dodgerblue;
  position: fixed;
  top: 0;
}
```

## FlexBox

> This is a layout method

- Used for laying out elements in one direction like in a row or column.

- This is a lot easier and simpler than floats.

The most common use for flexbox is navigation bars because in navigation bars. We have a bunch of menu items (hyperlinks) laid out horizontally.

First we go to the container (parent element) and set the display to flex. This will layout the boxes horizontally
we didn't have to use floats and worry about parent collapsing.

We can layout a bunch of elements in one direction either in a row or in a column.

### flex-direction:

By using the flex direction property
we can control the direction of the layout

By default it is row but we can set this to:

- column
- column-reverse
- row
- row-reverse

### Alignment:

Now we are going to look into alignment to align items. We need to understand the concept of axes in flex.

In flex we have 2 axes:

1. main(primary) axis
2. cross(secondary) axis

These axes are dependant on the direction.

#### direction: row:

if we set the direction to row:

    * The main axis is going to be the horizontal axis and cross is going to be the vertical axis.

#### direction: column:

if we set the direction to column:

    * The main axis is going to be the vertical axis. The cross axis is going to be the horizontal axis.

Why does this matter?

By using these axes we can easily align items inside of their container.

#### aligning items:

when we are aligining items there are 2 properties we need remember:

1.  justify-content

    - used to align items along the main axis

2.  align-items
    - used to align items along the cross axis

Just understand that we have 2 properties for alignment justify-content and align-items. These are the properties we use most of the time.

it was not always this easy in the past but flex all we have to do is set these 4 properties:

    - display: (flex)
    - flex-direction
    - justify-content
    - align-items

```css
.container {
  margin-top: 1rem;
  border: 3px solid lightgrey;
  /* this lays out the boxes horiziontally in our code */
  display: flex;
  /* by default the value is set to row but we can change this */
  flex-direction: row;
  /* default value is flex start but by setting this to the end */
  /* this will show up at the end of the row */
  justify-content: flex-end;
}

.container2 {
  border: 3px solid lightgrey;
  display: flex;
  flex-direction: row;
  /* this aligns the items in the center */
  justify-content: center;
  /* aligning the items on the secondary axis */
  /* this doesn't work right away if we do not have space */
  align-items: center;
  /* setting the height of container to 90% of viewport */
  height: 45vh;
}
```
