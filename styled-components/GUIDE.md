# Styled components

[![N|Solid](https://avatars2.githubusercontent.com/u/20658825?s=200&v=4)](https://www.styled-components.com/)

## Documentation

  - [Styled components](https://www.styled-components.com/)
  - [Github](https://github.com/styled-components/styled-components)

## Standards

### Theming
- if it is not necessary, use one theme for the entire application.

### Default values
Variables (colors, dimensions, breakpoints, ...) set in theme file without logic.

__Example__:
```js
const MODE = 'base';

const FONT_SIZE = {
	BASE: '1.2rem',
	H1: '2.4rem',
	H2: '1.6rem',
	H3: '1.4rem',
	H4: '1.4rem',
	H5: '1.4rem',
};

const LINE_HEIGHT = {
	BASE: '1.4'
};

const COLORS = {
	BASE: '#5a5a5a',
	LIGHT: '#959595',
	EXTRA_LIGHT: '#bfbfbf',
	PRIMARY: '#455fff',
	SECONDARY: '#ff4545',
	TERTIARY: '#42b972',
	INVERTED: '#ffffff'
};

const BG_COLOR = {
	BASE: '#ffffff',
	DARK: '#f5f5f5',
	PRIMARY: '#f5f7ff',
	SECONDARY: '#fff5f5',
	TERTIARY: '#f5fff9',
};

const BORDER_COLOR = {
	BASE: '#eaeaea',
	INPUT: '#dfdfdf',
};

const ALERT = {
	SUCCESS: '#5fd98b',
	ERROR: '#ff3e3e',
	WARNING: '#ffbd3e',
};

const BOX_SHADOW = {
	BOX: '0 4px 11px 4px rgba(29, 47, 150, 0.06)',
	SIDE_NAVBAR: '0 2px 6px 1px rgba(117, 117, 117, 0.05)',
};

const BREAKPOINT = {
	XS: '(min-width: 0)',
	SM: '(min-width: 576px)',
	MD: '(min-width: 768px)',
	LG: '(min-width: 992px)',
	XL: '(min-width: 1200px)',
};

export default {
	FONT_SIZE,
	LINE_HEIGHT,
	COLORS,
	BG_COLOR,
	BORDER_COLOR,
	ALERT,
	BOX_SHADOW,
	BREAKPOINT,
	MODE,
};
```
__Example usage__:
```js
import { withProps } from 'recompose';
import styled from 'styled-components';
import styledMap from 'styled-map';
import is from 'styled-is';

const fontSize = styledMap`
	default: ${({ theme }) => theme.FONT_SIZE.BASE};
	styleH1: ${({ theme }) => theme.FONT_SIZE.H1};
	styleH2: ${({ theme }) => theme.FONT_SIZE.H2};
	styleH3: ${({ theme }) => theme.FONT_SIZE.H3};
	styleH4: ${({ theme }) => theme.FONT_SIZE.H4};
	styleH5: ${({ theme }) => theme.FONT_SIZE.H5};
`;

const lineHeight = styledMap`
	default: ${({ theme }) => theme.LINE_HEIGHT.BASE};
`;

const fontWeight = styledMap`
	default: 400;
	strong: 600;
	styleH1: 600;
`;

const color = styledMap`
	default: ${({ theme }) => theme.COLORS.BASE};
`;

const Text = styled.span`
	font-size: ${fontSize};
	line-height: ${lineHeight};
	font-weight: ${fontWeight};
	color: ${color};
	text-align: ${is('centered')`center`};
	text-transform: ${is('uppercased')`uppercase`};
	text-align: ${is('justified')`justify`};
	margin: 0;
`;

export default Text;

const Paragraph = withProps({ as: 'p' })(Text);
Paragraph.displayName = 'Paragraph';
const H1 = withProps({ as: 'h1', styleH1: true })(Text);
H1.displayName = 'H1';
const H2 = withProps({ as: 'h2', styleH2: true })(Text);
H2.displayName = 'H2';
const H3 = withProps({ as: 'h3', styleH3: true })(Text);
H3.displayName = 'H3';
const H4 = withProps({ as: 'h4', styleH4: true })(Text);
H4.displayName = 'H4';
const H5 = withProps({ as: 'h5', styleH5: true })(Text);
H5.displayName = 'H5';

export { Paragraph, H1, H2, H3, H4, H5 };
```
### Units
Use __relative units__ instead of absolute units.

- Use __Rem__
- If you setup global font-size to 62.5%, your conversion from px to rem will be by dividing 10
```sass
html {
    font-size: 62.5%;
}

.... 

p {
    font-size: 1.6rem // 16px
}
```

### Media Queries
```js
@media screen and ${({ theme }) => theme.BREAKPOINT.XS} {
    ...
}
```
### Components
- Write smaller components with less modifiers than one complex universal component. It is clearer and more readable.
- No inline styles
- __Modifiers__ - use props and style map

### Spacings (paddings, margins)
- Solve within the component (or by wrapper). Don`t use component like Step.
- Extend the existing component `styled(Component)`

### Helpers / Mixins / Plugins
- [Polished](https://polished.js.org/docs/) 
- [Other plugins](https://www.styled-components.com/ecosystem)

### HTML5 Semantic Elements
- Use html tags correctly - header, nav, footer, article, section, ...
- More informations: [w3schools](https://www.w3schools.com/html/html5_semantic_elements.asp) 

### Fonts
- import from css file
