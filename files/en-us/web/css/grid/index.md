---
title: grid
slug: Web/CSS/grid
page-type: css-shorthand-property
browser-compat: css.properties.grid
sidebar: cssref
---

The **`grid`** [CSS](/en-US/docs/Web/CSS) property is a [shorthand property](/en-US/docs/Web/CSS/CSS_cascade/Shorthand_properties) that sets all of the explicit and implicit grid properties in a single declaration.

Using `grid` you specify one axis using {{cssxref("grid-template-rows")}} or {{cssxref("grid-template-columns")}}, you then specify how content should auto-repeat in the other axis using the implicit grid properties: {{cssxref("grid-auto-rows")}}, {{cssxref("grid-auto-columns")}}, and {{cssxref("grid-auto-flow")}}.

{{InteractiveExample("CSS Demo: grid")}}

```css interactive-example-choice
grid: auto-flow / 1fr 1fr 1fr;
```

```css interactive-example-choice
grid: auto-flow dense / 40px 40px 1fr;
```

```css interactive-example-choice
grid: repeat(3, 80px) / auto-flow;
```

```html interactive-example
<section class="default-example" id="default-example">
  <div class="example-container">
    <div class="transition-all" id="example-element">
      <div>One</div>
      <div>Two</div>
      <div>Three</div>
    </div>
  </div>
</section>
```

```css interactive-example
#example-element {
  border: 1px solid #c5c5c5;
  display: grid;
  grid-gap: 10px;
  width: 200px;
}

#example-element :nth-child(1) {
  background-color: rgb(0 0 255 / 0.2);
  border: 3px solid blue;
}

#example-element :nth-child(2) {
  background-color: rgb(255 0 200 / 0.2);
  border: 3px solid rebeccapurple;
  grid-column: auto / span 3;
  grid-row: auto / span 2;
}

#example-element :nth-child(3) {
  background-color: rgb(94 255 0 / 0.2);
  border: 3px solid green;
  grid-column: auto / span 2;
}
```

> [!NOTE]
> The sub-properties you don't specify are set to their initial value, as normal for shorthands. Also, the gutter properties are NOT reset by this shorthand.

## Constituent properties

This property is a shorthand for the following CSS properties:

- [`grid-auto-columns`](/en-US/docs/Web/CSS/grid-auto-columns)
- [`grid-auto-flow`](/en-US/docs/Web/CSS/grid-auto-flow)
- [`grid-auto-rows`](/en-US/docs/Web/CSS/grid-auto-rows)
- [`grid-template-areas`](/en-US/docs/Web/CSS/grid-template-areas)
- [`grid-template-columns`](/en-US/docs/Web/CSS/grid-template-columns)
- [`grid-template-rows`](/en-US/docs/Web/CSS/grid-template-rows)

## Syntax

```css
/* <'grid-template'> values */
grid: none;
grid: "a" 100px "b" 1fr;
grid: [line-name1] "a" 100px [line-name2];
grid: "a" 200px "b" min-content;
grid: "a" minmax(100px, max-content) "b" 20%;
grid: 100px / 200px;
grid: minmax(400px, min-content) / repeat(auto-fill, 50px);

/* <'grid-template-rows'> /
   [ auto-flow && dense? ] <'grid-auto-columns'>? values */
grid: 200px / auto-flow;
grid: 30% / auto-flow dense;
grid: repeat(3, [line1 line2 line3] 200px) / auto-flow 300px;
grid: [line1] minmax(20em, max-content) / auto-flow dense 40%;

/* [ auto-flow && dense? ] <'grid-auto-rows'>? /
   <'grid-template-columns'> values */
grid: auto-flow / 200px;
grid: auto-flow dense / 30%;
grid: auto-flow 300px / repeat(3, [line1 line2 line3] 200px);
grid: auto-flow dense 40% / [line1] minmax(20em, max-content);

/* Global values */
grid: inherit;
grid: initial;
grid: revert;
grid: revert-layer;
grid: unset;
```

### Values

- `<'grid-template'>`
  - : Defines the {{cssxref("grid-template")}} including {{cssxref("grid-template-columns")}}, {{cssxref("grid-template-rows")}} and {{cssxref("grid-template-areas")}}.
- `<'grid-template-rows'> / [ auto-flow && dense? ] <'grid-auto-columns'>?`
  - : Sets up an auto-flow by setting the row tracks explicitly via the {{cssxref("grid-template-rows")}} property (and the {{cssxref("grid-template-columns")}} property to `none`) and specifying how to auto-repeat the column tracks via {{cssxref("grid-auto-columns")}} (and setting {{cssxref("grid-auto-rows")}} to `auto`). {{cssxref("grid-auto-flow")}} is also set to `column` accordingly, with `dense` if it's specified.

    All other `grid` sub-properties are reset to their initial values.

- `[ auto-flow && dense? ] <'grid-auto-rows'>? / <'grid-template-columns'>`
  - : Sets up an auto-flow by setting the column tracks explicitly via the {{cssxref("grid-template-columns")}} property (and the {{cssxref("grid-template-rows")}} property to `none`) and specifying how to auto-repeat the row tracks via {{cssxref("grid-auto-rows")}} (and setting {{cssxref("grid-auto-columns")}} to `auto`). {{cssxref("grid-auto-flow")}} is also set to `row` accordingly, with `dense` if it's specified.

    All other `grid` sub-properties are reset to their initial values.

## Formal definition

{{cssinfo}}

## Formal syntax

{{csssyntax}}

## Examples

### Creating a grid layout

#### HTML

```html
<div id="container">
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
</div>
```

#### CSS

```css
#container {
  display: grid;
  grid: repeat(2, 60px) / auto-flow 80px;
}

#container > div {
  background-color: #8ca0ff;
  width: 50px;
  height: 50px;
}
```

#### Result

{{EmbedLiveSample("Creating_a_grid_layout", "100%", 150)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{cssxref("grid-template")}}
- {{cssxref("grid-template-rows")}}
- {{cssxref("grid-template-columns")}}
- {{cssxref("grid-template-areas")}}
- {{cssxref("grid-auto-columns")}}
- {{cssxref("grid-auto-rows")}}
- {{cssxref("grid-auto-flow")}}
- [Line-based placement with CSS grid](/en-US/docs/Web/CSS/CSS_grid_layout/Grid_layout_using_line-based_placement)
- [Grid template areas: grid definition shorthands](/en-US/docs/Web/CSS/CSS_grid_layout/Grid_template_areas#grid_definition_shorthands)
