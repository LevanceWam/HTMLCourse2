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
