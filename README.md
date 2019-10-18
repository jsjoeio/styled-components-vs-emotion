# styled-components-vs-emotion
A short doc comparing the popular CSS-in-JS libraries `styled-components` and `emotion` as of October 2019. For a more detailed comparison, see:
* [this Spectrum thread](https://spectrum.chat/styled-components/general/styled-components-vs-emotion~47206c1b-a688-424e-9e96-6f265993587e) (Aug 2018 - Mar 2019)
* [this shorter Frontity discussion](https://community.frontity.org/t/which-one-should-we-use-emotion-vs-styled-components/27)

## Brief Description

### [`styled-components`](https://www.styled-components.com/)
>Utilising tagged template literals (a recent addition to JavaScript) and the power of CSS, styled-components allows you to write actual CSS code to style your components. It also removes the mapping between components and styles – using components as a low-level styling construct could not be easier!

### [`emotion`](https://emotion.sh/)
>Emotion is a performant and flexible CSS-in-JS library. Building on many other CSS-in-JS libraries, it allows you to style apps quickly with string or object styles. It has predictable composition to avoid specificity issues with CSS. With source maps and labels, Emotion has a great developer experience and great performance with heavy caching in production.

### Functionality
The APIs of the two libraries have [converged over time](https://css-tricks.com/the-fragmented-but-evolving-state-of-css-in-js/). Both let you create a component with styling specified via CSS, or via object notation. (Styled Components added the latter capability [in May 2018](https://twitter.com/mxstbr/status/999918627997470724).)

#### `styled-components`

```javascript
// CSS syntax in tagged template literal
const Title = styled.h1`
  font-size: 1.5em;
  text-align: center;
  color: palevioletred;
`
render(<Title>Hiya!</Title>)

// Object syntax
const button = styled.button({
  color: 'blue'
});
```

#### `emotion`

```javascript
// Object syntax
const titleStyles = css({
  fontSize: '1.5em',
  textAlign: 'center',
  color: 'palevioletred'
})

render(<h1 className={titleStyles}>Hiya!</h1>)

// Tagged template literal syntax
render(
  <h1
    className={css`
      font-size: 1.5em;
      text-align: center;
      color: palevioletred;
    `}
  >
    Hiya!
  </h1>
)
```

In addition, `classNames` used in `emotion` are powerful because the `css` API has a special property called `composes` that allows you to create new styles composed with previously created styles. Here's an example pulled from [this Medium article](https://medium.com/@tkh44/emotion-ad1c45c6d28b) written by the creator of `emotion`:

```javascript
const imageBase = css`
  width: 32px;
  height: 32px;
  border-radius: 50%;
`
const avatarStyle = css`
  composes: ${imageBase};
  border: 1px solid #7519E5
`

// This would generate a classname for the previous style AND also the new avatarStyle:
// ex. css-imageBase-12345 css-avatarStyle-12345
```

## Comparison
Here's how the two libraries compare based on features and stats:

### Features - at parity
This information was taken from the documentation websites.

Library | Attaching Props? | Media Queries? | Global Styles? | Nested Selectors? | Server Side Rendering? | Theming Support?
--- | :---: | :---: | :---: | :---: | :---: | :---: |
`styled-components` | Yes | Yes| Yes | Yes | Yes | Yes   
`emotion` | Yes | Yes | Yes | Yes | Yes | Yes

### Stats
These numbers were pulled on October 18th, 2019.

Library | Creation Date | Last Updated (GitHub) | Size | Repo Stars | # of Contributors | Community Size (Spectrum)
--- | --- | --- | --- | --- | --- | --- |
[`styled-components`](https://github.com/styled-components/styled-components) | August 16th, 2016 | 8 days ago | ? 14.6kb ? | 26,197 | 252 | [10,113](https://spectrum.chat/styled-components)
[`emotion`](https://github.com/emotion-js/emotion) | May 27th, 2017 | 6 days ago | ? 8.9kb ? | 9,118 | 184 | [479](https://spectrum.chat/emotion)

### Worthy Notes

* `emotion` is [ready](https://community.frontity.org/t/which-one-should-we-use-emotion-vs-styled-components/27/8) for [React Concurrent mode](https://dev.to/pomber/about-react-suspense-and-concurrent-mode-21aj) and it has a smaller bundle size
- `emotion` [performed faster](https://github.com/A-gambit/CSS-IN-JS-Benchmarks/blob/master/RESULT.md) than `styled-components` back in March 12th when a comparison was done over all CSS-in-JS libraries. **However, maintainers of `styled-components` are actively improving performance and say [they are within 0.5-2x emotion's times](https://twitter.com/_philpl/status/1017312352641933317).**
- Kent C. Dodds recommended `emotion` over `styled-components` in [this tweet](https://twitter.com/kentcdodds/status/994230853189320705) saying that it's smaller and faster. 

### Contributions
If you see a typo or something that is out-of-date or incorrect, please submit a PR and I will happily update this doc.

