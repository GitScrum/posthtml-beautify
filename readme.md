# <a href="https://github.com/posthtml/posthtml"><img valign="text-bottom" height="49" title="PostHTML logo" src="http://posthtml.github.io/posthtml/logo.svg"></a> beautify

> A [posthtml](https://github.com/posthtml) plugin to beautify you html files

[![Travis Build Status](https://img.shields.io/travis/GitScrum/posthtml-beautify.svg?style=flat-square&label=unix)](https://travis-ci.org/GitScrum/posthtml-beautify)[![AppVeyor Build Status](https://img.shields.io/appveyor/ci/GitScrum/posthtml-beautify.svg?style=flat-square&label=windows)](https://ci.appveyor.com/project/GitScrum/posthtml-beautify)[![npm version](https://img.shields.io/npm/v/posthtml-beautify.svg?style=flat-square)](https://www.npmjs.com/package/posthtml-beautify)[![Dependency Status](https://david-dm.org/gitscrum/posthtml-beautify.svg?style=flat-square)](https://david-dm.org/gitscrum/posthtml-beautify)[![XO code style](https://img.shields.io/badge/code_style-XO-5ed9c7.svg?style=flat-square)](https://github.com/sindresorhus/xo)[![Coveralls status](https://img.shields.io/coveralls/GitScrum/posthtml-beautify.svg?style=flat-square)](https://coveralls.io/r/GitScrum/posthtml-beautify)

[![npm downloads](https://img.shields.io/npm/dm/posthtml-beautify.svg?style=flat-square)](https://www.npmjs.com/package/posthtml-beautify)[![npm](https://img.shields.io/npm/dt/posthtml-beautify.svg?style=flat-square)](https://www.npmjs.com/package/posthtml-beautify)[![Package Quality](http://npm.packagequality.com/shield/posthtml-beautify.svg?style=flat-square)](http://packagequality.com/#?package=posthtml-beautify)

## Why?
Format your html and inline css markup according to the [HTML5 syntax Style Guide](http://www.w3schools.com/html/html5_syntax.asp), [Code Guide](http://codeguide.co/#html). Full list of supported options:
- [ ] Transform lower case element names
- [x] Transform lower case attribute names
- [x] Only double quotes
- [x] Close all html elements 
- [x] Removing trailing slash in self-closing 
- [x] Removes spaces at the equal sign
- [x] Add blank lines to separate large or logical code blocks
- [x] Add 2 spaces of indentation. *Do not use TAB*.
- [ ] Add language attribute
- [ ] Add character encoding
- [ ] Attribute order
- [x] Boolean attributes
- [ ] Creates file from the inline styles
- [ ] Create scoped class name (*use css-modules*) instead inline styles
- [ ] validate elements and attributes name

## Install

```bash
npm i -S posthtml posthtml-beautify
```

> **Note:** This project is compatible with node v4+

## Usage

```js
import {readFileSync, writeFileSync} from 'fs';
import posthtml from 'posthtml';
import beautify from 'posthtml-beautify';

const html = readFileSync('input.html', 'utf8');

posthtml()
    .use(beautify({rules: {indent: 4}}))
    .process(html)
    .then(result => {
        writeFileSync('output.html', result.html);
    });

```

## Example

#### input.html
```html
<!DOCTYPE html>

 <table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>A</td>
    <td>Description of A</td>
  </tr>
  <tr>
    <td>B</td>
    <td>Description of B</td>
  </tr>
</table>
    <div>
<div class="first">
                first</div>   <div class="middle"></div>
<div class="last">last <b>line  </b> <a href="#">            test</a></div>

</div>
<img src="img.png" alt=""><input type="text">
```

#### output.html
```html
<!DOCTYPE html>
<table>
  <tr>
    <th>Name</th>

    <th>Description</th>
  </tr>

  <tr>
    <td>A</td>

    <td>Description of A</td>
  </tr>

  <tr>
    <td>B</td>

    <td>Description of B</td>
  </tr>
</table>
<div>
  <div class="first">first</div>
</div>
<div class="middle"></div>
<div class="last">
  last

  <b>line</b>

  <a href="#">test</a>
</div>
<img src="img.png" alt="">
<input type="text">
```

## Options

#### `rules`
Type: `Object`  
Default: `{indent: 2, eol: '\n'}`
