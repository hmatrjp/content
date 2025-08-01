---
title: scale()
slug: Web/CSS/transform-function/scale
page-type: css-function
browser-compat: css.types.transform-function.scale
sidebar: cssref
---

The **`scale()`** [CSS](/en-US/docs/Web/CSS) [function](/en-US/docs/Web/CSS/CSS_Values_and_Units/CSS_Value_Functions) defines a transformation that resizes an element on the 2D
plane. Because the amount of scaling is defined by a vector [sx, sy], it can resize the horizontal and vertical dimensions at
different scales. Its result is a {{cssxref("&lt;transform-function&gt;")}} data type.

{{InteractiveExample("CSS Demo: scale()")}}

```css interactive-example-choice
transform: scale(1);
```

```css interactive-example-choice
transform: scale(0.7);
```

```css interactive-example-choice
transform: scale(1.3, 0.4);
```

```css interactive-example-choice
transform: scale(-0.5, 1);
```

```html interactive-example
<section id="default-example">
  <img
    class="transition-all"
    id="example-element"
    src="/shared-assets/images/examples/firefox-logo.svg"
    width="200" />
</section>
```

This scaling transformation is characterized by a two-dimensional vector. Its coordinates define how much scaling is
done in each direction. If both coordinates are equal, the scaling is uniform (_isotropic_) and the aspect
ratio of the element is preserved (this is a [homothetic transformation](https://en.wikipedia.org/wiki/Homothetic_transformation)).

When a coordinate value is outside the \[-1, 1] range, the element grows along that dimension; when inside, it
shrinks. A negative value results in a [point reflection](https://en.wikipedia.org/wiki/Point_reflection)
in that dimension. The value `1` has no effect.

> [!NOTE]
> The `scale()` function only scales in 2D. To scale in 3D, use
> [`scale3d()`](/en-US/docs/Web/CSS/transform-function/scale3d) instead.

## Syntax

```css
scale(sx)

scale(sx, sy)
```

### Values

- `sx`
  - : A {{cssxref("&lt;number&gt;")}} or {{cssxref("&lt;percentage&gt;")}} representing the abscissa (horizontal, x-component) of the scaling vector.
- `sy` {{optional_inline}}
  - : A {{cssxref("&lt;number&gt;")}} or {{cssxref("&lt;percentage&gt;")}} representing the ordinate (vertical, y-component) of the scaling vector.
    If not defined, its default value is `sx`, resulting in a uniform scaling that preserves the element's {{glossary("aspect ratio")}}.

<table class="standard-table">
  <thead>
    <tr>
      <th scope="col"><a href="/en-US/docs/Web/CSS/transform-function#cartesian_coordinates">Cartesian coordinates</a> on <a href="https://en.wikipedia.org/wiki/Real_coordinate_space">ℝ^2</a></th>
      <th scope="col"><a href="https://en.wikipedia.org/wiki/Homogeneous_coordinates">Homogeneous coordinates</a> on <a href="https://en.wikipedia.org/wiki/Real_projective_plane">ℝℙ^2</a></th>
      <th scope="col">Cartesian coordinates on <a href="https://en.wikipedia.org/wiki/Real_coordinate_space">ℝ^3</a></th>
      <th scope="col">Homogeneous coordinates on <a href="https://en.wikipedia.org/wiki/Real_projective_space">ℝℙ^3</a></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="2">
        <math display="block">
          <semantics><mrow><mo>(</mo><mtable><mtr><mtd><mi>sx</mi></mtd><mtd><mn>0</mn></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mi>sy</mi></mtd></mtr></mtable><mo>)</mo></mrow><annotation encoding="TeX">\left( \begin{array}{cc} sx & 0 \\ 0 & sy \end{array} \right)</annotation></semantics>
        </math>
      </td>
      <td>
        <math display="block">
          <semantics><mrow><mo>(</mo><mtable><mtr><mtd><mi>sx</mi></mtd><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mi>sy</mi></mtd><mtd><mn>0</mn></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow><annotation encoding="TeX">\left( \begin{array}{ccc} sx & 0 & 0 \\ 0 & sy & 0 \\ 0 & 0 & 1 \end{array} \right)</annotation></semantics>
        </math>
      </td>
      <td rowspan="2">
        <math display="block">
          <semantics><mrow><mo>(</mo><mtable><mtr><mtd><mi>sx</mi></mtd><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mi>sy</mi></mtd><mtd><mn>0</mn></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow><annotation encoding="TeX">\left( \begin{array}{ccc} sx & 0 & 0 \\ 0 & sy & 0 \\ 0 & 0 & 1 \end{array} \right)</annotation></semantics>
        </math>
      </td>
      <td rowspan="2">
        <math display="block">
          <semantics><mrow><mo>(</mo><mtable><mtr><mtd><mi>sx</mi></mtd><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mi>sy</mi></mtd><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>1</mn></mtd><mtd><mn>0</mn></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow><annotation encoding="TeX">\left( \begin{array}{cccc} sx & 0 & 0 & 0 \\ 0 & sy & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{array} \right)</annotation></semantics>
        </math>
      </td>
    </tr>
    <tr>
      <td><code>[sx 0 0 sy 0 0]</code></td>
    </tr>
  </tbody>
</table>

## Formal syntax

{{CSSSyntax}}

## Accessibility

Scaling/zooming animations are problematic for accessibility, as they are a common trigger for certain types of
migraine. If you need to include such animations on your website, you should provide a control to allow users to turn
off animations, preferably site-wide.

Also, consider making use of the {{cssxref("@media/prefers-reduced-motion", "prefers-reduced-motion")}} media feature
— use it to write a [media query](/en-US/docs/Web/CSS/CSS_media_queries) that will turn off animations if the
user has reduced animation specified in their system preferences.

Find out more:

- [MDN Understanding WCAG, Guideline 2.3 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Operable#guideline_2.3_%e2%80%94_seizures_and_physical_reactions_do_not_design_content_in_a_way_that_is_known_to_cause_seizures_or_physical_reactions)
- [Understanding Success Criterion 2.3.3 | W3C Understanding WCAG 2.1](https://www.w3.org/WAI/WCAG21/Understanding/animation-from-interactions)

## Examples

### Scaling the X and Y dimensions together

#### HTML

```html
<div>Normal</div>
<div class="scaled">Scaled</div>
```

#### CSS

```css
div {
  width: 80px;
  height: 80px;
  background-color: skyblue;
}

.scaled {
  transform: scale(0.7); /* Equal to scaleX(0.7) scaleY(0.7) */
  background-color: pink;
}
```

#### Result

{{EmbedLiveSample("Scaling_the_X_and_Y_dimensions_together", "200", "200")}}

### Scaling X and Y dimensions separately, and translating the origin

#### HTML

```html
<div>Normal</div>
<div class="scaled">Scaled</div>
```

#### CSS

```css
div {
  width: 80px;
  height: 80px;
  background-color: skyblue;
}

.scaled {
  transform: scale(2, 0.5); /* Equal to scaleX(2) scaleY(0.5) */
  transform-origin: left;
  background-color: pink;
}
```

#### Result

{{EmbedLiveSample("Scaling_X_and_Y_dimensions_separately_and_translating_the_origin", "200", "200")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{cssxref("transform")}}
- {{cssxref("scale")}}
- {{cssxref("zoom")}}
- {{cssxref("&lt;transform-function&gt;")}}
- {{cssxref("transform-function/scale3d", "scale3d()")}}
- Other individual transform properties {{cssxref("translate")}} and {{cssxref("rotate")}}
