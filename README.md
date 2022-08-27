# remark-critic-markup
This is a remark plugin to make markdown support [the CriticMarkup syntax](https://github.com/CriticMarkup/CriticMarkup-toolkit#the-basic-syntax).

this plugin provides a transformer to match the basic syntax of CriticMarkup:

**Addition**

* markdown content: `++addition++`
* generate HTML: `<ins class="critic addition">addition</ins>`

**Deletion**

* markdown content: `--deletion--`
* generate HTML: `<del class="critic deletion">deletion</del>`

**Substitution**:

* markdown content: `~~remove~>substitution~~`

    :warning: this syntax may conflict with the remark-gfm [strikethrough syntax](https://github.com/remarkjs/remark-gfm), maybe this syntax can be replaced by Addition and Deletion syntax

    ***so this redundant syntax won't transform in this package***

**Comment**

* syntax(origin): `>>comment<<`

    :warning: this syntax may conflict with the markdown [blockquote syntax](https://commonmark.org/help/)

* markdown content(adjust): `//comment//`

* generate HTML: `<span class="critic comment">comment</span>`

**Highlight**

* markdown content: `==highlight==`

* generate HTML: `<mark class="critic highlight">highlight</mark>`


## Install

```bash
npm install remark-critic-markup
```

## Usage

```js
import {remark} from 'remark';
import remarkCriticMarkup from 'remark-critic-markup';

const doc = 'These are some contents satisfy criticMarkup syntax ++addition++ --deletion-- //comment// ==highlight==';
remark().use(remarkCriticMarkup).process(doc).then(file => {
    console.log(String(file));
});
```

## License
[MIT](./LICENSE)