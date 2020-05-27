# Design System

## General

- Feature before layout

### Hierarchy

- Create visual hierarchy, focus on important element
- Focus on content, not the title
- Icon naturally looks "heavy", good to de-emphasize it by giving it a softer color

### Layout and Spacing

- Start with too much white space

## Text

### General

- Don't center long form text
- Right-align numbers
- Enable hyphenation when justify texts

### Font Size

#### Scale

- 12px
- 14px
- 16px
- 18px
- 20px
- 24px
- 30px
- 36px
- 48px
- 60px
- 72px

### Font Weight

#### General

- A normal font weight (400 / 500) for most text
- A heavier font weight (600 / 700) for text you want to emphasize
- Avoid font weights under 400 for UI work, use lighter color or smaller font size instead

### Line length

Paragraphs should fit between 45 and 75 characters per line. Easiest way is using em units, which are relative to the current font size. A width of 20-35 em will get you in the right ballpark.

### Line Height

- Align by baseline
- Line height should be proportional to line length, and inversely proportional to font size

## Color

- Avoid grey text on colored backgrounds, user color with the same hue, adjust the saturationand lightness until it looks right
- Use HSL instead of hex, note that HSL and HSB are different
  - Hue: position on the color wheel. 0° - red,  120° - green,  240° - blue
  - Saturation: how colorful or vivid a color looks. 0% - grey, 100% - vibrant and intense.
  - Lightness: how close a color is to black or white. 0%: pure black, 100%: pure white, 50%: pure color of the given hue

### General

- A dark color for primary content (ex. headline)
- A Grey for secondary content (ex. date)
- A lighter grey for tertiary content (ex. copyright notice)
- Liven up the page - add color with accent borders

### Color Palette

- Greys - 8 to 10 shades, don't use pure black or pure white
- Primary Color(s) - 5 to 10 shades
- Accent Colors - 5 to 10 shades each, use sparingly throughout the UI
- Increase saturation for darker and lighter shades
- Rotate hue towards the brighter hue when changing lightness is not possible - 60°, 180°, 300°. Darker hues - 0°, 120°, 240°. Don't rotate the hue more than 20°-30°
- True grey has a saturation of 0, add a little cool feeling with a bit of blue, or yellow / orange for warmth

### Define the shades

1. Choose the base color. Good rule of thumb is to pick a shade that would work well as a button background.
2. Find the edges (darkest and lightest shade). The darkest shade is usually reserved for text, lightest shade might be used to tint the background of an element.
3. Filling in the gaps. 100 to 900 is a good scale.

## Spacing

### General

- 16px is the default font size in major browsers

### Scale

- 4px
- 8px
- 12px
- 16px
- 24px
- 32px
- 48px
- 64px
- 96px
- 128px
- 192px
- 256px
- 384px
- 512px
- 640px
- 768px

### Margin

### Padding

### Width

### Height

## Box Shadows

### Create Depth

#### Raise Content

Top edge should be lighter, bottom edge should be darker. Choose the lighter color instead of using a semi-transparent white. Use top border or inset box shadow with a slight vertical offset:

Example top:
`box-shadow: inset 0 1px 0 hsl(224, 84%, 74%);`

Example bot:
`box-shadow: 0 1px 3px hsla(0, 0%, 0%, .2);`

Only add a couple of pixles for blur radius, as the shadow should have pretty sharp edges

#### Inset Content

Opposite of above.

### Elevation

- Small shadows with a tight blur radius - lower elevation
- Larger shadows with a higher blur radius - higher elevation and closer to the user
- Use solid shadows for flat design
- Overlap elements to create depth

Examples:
- Smaller shadows - button, the element should be noticed by the user, but not dominant the page
  - `box-shadow: 0 1px 3px hsla(0, 0%, .2);`
- Medium shadows - dropdowns, elements that need to sit a bit further above the rest of the UI
  - `box-shadow: 0 4px 6px hsla(0, 0%, .1);`
- Large shadows - modal dialogs, the element should capture the user's attention
  - `box-shadow: 0 15px 35px hsla(0, 0%, .2);`

### Combine 2 Shadows

Combine a larger and softer shadow, and a tighter and darker shadow

#### System

5 options is usually plenty

Example:

Single Shadow
```
0 1px 3px hsla(0, 0%, .2);
0 4px 6px hsla(0, 0%, .2);
0 5px 15px hsla(0, 0%, .2);
0 10px 24px hsla(0, 0%, .2);
0 15px 35px hsla(0, 0%, .2);
```

Two Shadows
```
0 1px 3px hsla(0, 0%, .12);
0 1px 2px hsla(0, 0%, .24);

0 3px 6px hsla(0, 0%, .15);
0 2px 4px hsla(0, 0%, .12);

0 10px 20px hsla(0, 0%, .15);
0 3px 6px hsla(0, 0%, .10);

0 15px 25px hsla(0, 0%, .15);
0 5px 10px hsla(0, 0%, .5);

0 20px 40px hsla(0, 0%, .2);
```

## Border Radius

## Opacity

## Image

### Text on Images

To increase overall text contrast:

- Add a semi-transparent overlay to the background image
- Lower the image contrast
- Colorize the image, steps:
  1. Lower the image contrast, to balance out a bit
  2. Desaturate the image, to remove any existing color
  3. Add a solid fill, using the "multiply" blend mode
- Add a text shadow, use a large blur without any offset

[Back](../../../README.md)
