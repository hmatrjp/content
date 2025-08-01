---
title: -moz-image-rect
slug: Web/CSS/-moz-image-rect
page-type: css-function
status:
  - deprecated
  - non-standard
browser-compat: css.types.-moz-image-rect
sidebar: cssref
---

{{Non-standard_Header}}{{Deprecated_Header}}

The **`-moz-image-rect`** value for [CSS](/en-US/docs/Web/CSS) {{CSSxRef("background-image")}} lets you use a portion of a larger image as a background.

## Syntax

```css
-moz-image-rect(url("my-url"), top, right, bottom, left);
```

### Values

- {{CSSxRef("url_value", "&lt;url&gt;")}}
  - : The URI of the image from which to take the sub-image.
- `top`
  - : The top edge, specified as an {{CSSxRef("&lt;integer&gt;")}} or {{CSSxRef("&lt;percentage&gt;")}}, of the sub-image within the specified image.
- `right`
  - : The right edge, specified as an {{CSSxRef("&lt;integer&gt;")}} or {{CSSxRef("&lt;percentage&gt;")}}, of the sub-image within the specified image.
- `bottom`
  - : The bottom edge, specified as an {{CSSxRef("&lt;integer&gt;")}} or {{CSSxRef("&lt;percentage&gt;")}}, of the sub-image within the specified image.
- `left`
  - : The left edge, specified as an {{CSSxRef("&lt;integer&gt;")}} or {{CSSxRef("&lt;percentage&gt;")}}, of the sub-image within the specified image.

## Description

This property allows you to, for example, use different parts of one larger image as backgrounds in different parts of your content.

The syntax for the rectangle is similar to the [`rect()`](/en-US/docs/Web/CSS/shape#syntax) function generating a {{CSSxRef("&lt;shape&gt;")}} CSS type. All four values are relative to the upper left corner of the image.

## Examples

This example loads an image and uses it in four segments to draw the Firefox logo in four {{HTMLElement("div")}} blocks. Clicking on their container causes the four segments to rotate around by swapping the {{CSSxRef("background-image")}} property values among the four {{HTMLElement("div")}} blocks.

### CSS

The CSS defines one container style, then the styles for the four boxes that comprise the complete image.

The container looks like this:

```css
#container {
  width: 267px;
  height: 272px;
  top: 100px;
  left: 100px;
  position: absolute;
  font-size: 16px;
  text-shadow: white 0px 0px 6px;
  text-align: center;
}
```

Then the four boxes defining the segments of the image are defined. Let's look at them one at a time.

```css
#box1 {
  background-image: -moz-image-rect(url(firefox.png), 0%, 50%, 50%, 0%);
  width: 133px;
  height: 136px;
  left: 0px;
  top: 0px;
  position: absolute;
}
```

This is the top-left corner of the image. It defines a rectangle containing the top-left quarter of the image in the file `firefox.jpg`.

```css
#box2 {
  background-image: -moz-image-rect(url(firefox.png), 0%, 100%, 50%, 50%);
  width: 133px;
  height: 136px;
  left: 133px;
  top: 0px;
  position: absolute;
}
```

This defines the top-right corner of the image.

The other corners follow a similar pattern:

```css
#box3 {
  background-image: -moz-image-rect(url(firefox.png), 50%, 50%, 100%, 0%);
  width: 133px;
  height: 136px;
  left: 0px;
  top: 136px;
  position: absolute;
}
#box4 {
  background-image: -moz-image-rect(url(firefox.png), 50%, 100%, 100%, 50%);
  width: 133px;
  height: 136px;
  left: 133px;
  top: 136px;
  position: absolute;
}
```

### HTML

We include a container with four boxes:

```html
<div id="container">
  <div id="box1">Top left</div>
  <div id="box2">Top right</div>
  <div id="box3">Bottom left</div>
  <div id="box4">Bottom right</div>
</div>
```

This places the four segments of our image in a two-by-two box grid. These four segments are all contained within a larger {{HTMLElement("div")}} block whose primary purpose is to receive click events and dispatch them to our JavaScript code.

### JavaScript

This code handles the click event when the container receives a mouse click.

```js
function rotate() {
  let prevStyle = window
    .getComputedStyle(document.getElementById("box4"), null)
    .getPropertyValue("background-image");

  // Now that we've saved the last one, start rotating
  for (let i = 1; i <= 4; i++) {
    const curId = `box${i}`;

    // Shift the background images
    const curStyle = window
      .getComputedStyle(document.getElementById(curId), null)
      .getPropertyValue("background-image");
    document.getElementById(curId).style.backgroundImage = prevStyle;
    prevStyle = curStyle;
  }
}

document.getElementById("container").addEventListener("click", rotate);
```

This uses {{DOMxRef("window.getComputedStyle()")}} to fetch the style of each element, shifting it to the following element. Notice that before it begins doing so it saves a copy of the last box's style since it will be overwritten by the third element's style. By copying the values of the {{CSSxRef("background-image")}} property from one element to the next with each mouse click, we achieve the desired effect.

### What it looks like

{{EmbedLiveSample("Examples","400","400")}}

## Specifications

Not part of any standard.

## Browser compatibility

{{Compat}}

## See also

- [Mozilla CSS extensions](/en-US/docs/Web/CSS/Mozilla_Extensions)
- [CSS Backgrounds and Borders module](/en-US/docs/Web/CSS/CSS_backgrounds_and_borders)
