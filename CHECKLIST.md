# Coding checklist


## Responsive + fluid design

### Mobile first approach

Use mobile first approach when writing CSS. This ensures that there won't be any unnecessary styles, images or fonts loaded on smaller devices. Most of your Media Queries should be `min-width` (instead of `max-width`).

### Cover all window widths

People use devices in different ways, e. g. use phone in landscape mode, use split view, etc. so one or two breakpoints is not enough.

### Breakpoints on component level

Don't create multiple components for different screen sizes, but create one and differentiate the structure inside.


## Optimization

### No plugin duplicities

To keep the bundle slim, there shouldn't be two plugins imported that provide the same or very similar functionality. Typical example is importing two carousel plugins.

### Image optimization

A correct format should be chosen - learn when to use jpg, png or svg. Also jpegs should be compressed to about 80%, never use 100% quality.

### Lazy loading should be used if necessary

This applies to a huge list of items with images or to carousels.

### Retina images

Since we can generate images from BE in multiple sizes, it's quite easy to set this up - use `<picture>` or `<img srcset>`.


## Accessibility

### Use REM / EM units instead of PX

Let's care about the accesibility at least a little and ditch the old pixels for font sizes and media queries.


## Code quality

### Variable naming

Use primary, secondary, light, dark, sansSerif, serif instead of blue, red, white, black, Arial, TimesNewRoman

### No inline styles

Seriously, no.

### Avoid !important

Note: There are some exceptions, for example when styling plugin-generated CSS you don't have complete control of.

### Use html tags correctly

Use `<img>` instead of `<div>` with background-image, `<button>` and `<a>` instead of `<div>` with onClick and so on…

### Create reusable components

Component modificators should only modify the component look / behaviour. Setting component’s position and other styles (width in some cases) should do the parent component.

E. g. Input width should be controlled by form grid.

### Name transition properties

Don't use `transition: all`, but name only the properties you need.

### No clearfix elements

There's no need to have a `<div className='clearfix' />`, use clearfix mixin instead in the styles that will add pseudo elements to achieve the same in much cleaner way.

### No spacing elements

Avoid using spacing elements, but use margins/padding accordingly.

### Don't use * selectors

It usually means there's some overriding of a bad code and is hard to work with.

### Line height in multiplier, not pixels

With exceptions, like line-height based from height of an element.
