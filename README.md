# mdlog

Markdown on `console.log`

[![npm](https://nodei.co/npm/mdlog.png)](https://nodei.co/npm/mdlog/)


## What Is?

```javascript
require('mdlog/override');

console.log([
  '# Hello, *mdlog* World!',
  '',
  'You can use Markdown syntax on `console.log`.',
  '',
  '- Markdown is **powerfull**.',
  '- Markdown is **useful**.',
  '- Markdown is **readable**.',
  '',
  '> Markdown is a text-to-HTML conversion tool for web writers.',
  'Markdown allows you to write using an easy-to-read, easy-to-write plain text format,',
  'then convert it to structurally valid XHTML (or HTML).',
  '',
  'see <http://en.wikipedia.org/wiki/Markdown>.',
].join('\n'));
```

then output is:

![output to terminal](https://raw.githubusercontent.com/MakeNowJust/mdlog/master/sample/readme.png)


## Install

```console
$ npm install --save mdlog
```

`--save` option is optional.

## API

#### `mdlog = require('mdlog')`

`mdlog` is the implementation of `mdlog/override`'s `console.log`. You can use it without `console.log` pollution.

First it pass its arguments to `util.format`, then call `convert` with this result and `config`.


#### `convert = require('mdlog/convert')`

`convert` is converter from Markdown to terminal output.

It follows two arguments.  First argument is `markdown`. It is Markdown text.  Second argument is `config`.  This config is JavaScript object having such key/values:

  - `config.mdast_<mdast_option_name>` is passed to `mdast`'s API.
  - `config.stringify` is a default parameter of `config.<node_type>_stringify`.
  - `config.<node_type>_stringify` is whether using `mdast.stringify`.
  - `config.<node_type>_bold`, `config.<node_type>_italic`, `config.<node_type>_underline`, `config.<node_type>_delete` and `config.<node_type>_color` is decoration config.
  - `config.<node_type>_block` is whether `<node_type>` is block.


#### `config = require('mdlog/config')`

It is default `config`.  It is custamizable by environemt variable `MDLOG_CONFIG`.

```console
$ env MDLOG_CONFIG='heading_color:32' node sample/readme.js
```


#### `require('mdlog/override')`

`console.log` overrides `mdlog`. __This module pollutes global `console` object.__


### License

MIT License. See <https://makenowjust.github.io/license/mit?2015>.