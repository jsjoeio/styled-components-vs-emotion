# styled-components-vs-emotion
a short doc comparing the popular CSS-in-JS libraries `styled-components` and `emotion`

## Brief Description

### [`styled-components`](https://www.styled-components.com/)
>Utilising tagged template literals (a recent addition to JavaScript) and the power of CSS, styled-components allows you to write actual CSS code to style your components. It also removes the mapping between components and styles – using components as a low-level styling construct could not be easier!

### [`emotion`](https://emotion.sh/)
>Emotion is a performant and flexible CSS-in-JS library. Building on many other CSS-in-JS libraries, it allows you to style apps quickly with string or object styles. It has predictable composition to avoid specificity issues with CSS. With source maps and labels, Emotion has a great developer experience and great performance with heavy caching in production.

### Functionality
It appears as thought the main difference between the two is with `styled-components` you have one option: create a component with specific styling.

With `emotion` you have that same option, or you can pass the css to it. Here are some examples:

```javascript
//Using styled-components (borrowed from styled-components website)
const Title = styled.h1`
  font-size: 1.5em;
  text-align: center;
  color: palevioletred;
`
render(<Title>Hiya!</Title>)

//Using emotion object syntax
const titleStyles = css({
  fontSize: '1.5em',
  textAlign: 'center',
  color: 'palevioletred'
})

render(<h1 className={titleStyles}>Hiya!</h1>)

//Using emotion tagged template literal syntax
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

In addition, `classNames` used in `emotion` are powerful because the `css` api has a special property called `composes` that allows you to create new styles composed with previously created styles. Here's an example pulled from [this Medium article](https://medium.com/@tkh44/emotion-ad1c45c6d28b) written by the creator of `emotion`:

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

//This would generate a classname for the previous style AND also the new avatarStyle:
//ex. css-imageBase-12345 css-avatarStyle-12345
```

## Comparison
Here's how the two libraries compare based on features and stats:

### Features
This information was taken from the documentation websites.

Library | Attaching Props? | Media Queries? | Global Styles? | Nested Selectors? | Server Side Rendering? | Theming Support?
--- | :---: | :---: | :---: | :---: | :---: | :---: |
`styled-components` | Yes | Yes| Yes | Yes | Yes | Yes   
`emotion` | Yes | Yes | Yes | Yes | Yes | Yes

### Stats
These numbers were pulled on July 13th, 2018.

Library | Creation Date | Last Updated (GitHub) | Size | Repo Stars | # of Contributors | Community Size (Spectrum)
--- | --- | --- | --- | --- | --- | --- |
`styled-components` | August 16th, 2016 | 2 days ago | 14.6kb | 17,636 | 210 | 3,700
`emotion` | May 27th, 2017 | 9 hours ago | 8.9kb| 4,307 | 97 | 56

### Worthy Notes
- `emotion` [performed faster](https://github.com/A-gambit/CSS-IN-JS-Benchmarks/blob/master/RESULT.md) than `styled-components` back in March 12th when a comparison was done over all CSS-in-JS libraries. **However, maintainers of `styled-components` are actively improving performance and say [they are within 0.5-2x emotion's times](https://twitter.com/_philpl/status/1017312352641933317).**
- Kent C. Dodds recommended `emotion` over `styled-components` in [this tweet](https://twitter.com/kentcdodds/status/994230853189320705) saying that it's smaller and faster. 

### Contributions
If you see a typo or something that is out-of-date or incorrect, please submit a PR and I will happily update this doc.

