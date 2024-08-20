# Deeper, a TinyMCE skin using CSS variables

>_We need to go deeper_

Deeper is a TinyMCE skin based on Oxide where the LESS variables are bound to native CSS variables. This allows installations to customize the look and feel of the editor at runtime, with the downside that no color variation can be preprocessed (something that would be possible when developing a static Oxide variation).

It is meant to be compatible with Vuetify through a bridge between the Deeper and Vuetify theme variables.

## Installation

TODO

## Compatibility

This skin was tested on:

| Skin  | TinyMCE         | Vuetify |
|-------|-----------------|---------|
| 1.0.0 | 7.0.0 - 7.3.0   | 3.5.13  |


## Development

This skin uses the [TinyMCE "creating a skin"](https://www.tiny.cloud/docs/tinymce/7/creating-a-skin/) guide from the documentation as basis.

While building the skin, all expressions that cannot be evaluated by less (such as a `darken` on a now CSS variable) are replaced by random CSS colors. This will allow pinpointing the source of potential issues in binding the variables.

### Running the demo

```shell
npm install
npm run start
```

Note that a VSCode tasks exists to start the demo (`npm: start`).

### Building the skin

```shell
npm install
npm run build
```

Note that a VSCode tasks exists to build the project (`npm: build`).

### Working on the style

Random CSS colors can be retrieved from https://www.color-hex.com/random.php or https://www.random.org/colors/hex .

To evaluate original Oxide expressions, go to https://lesscss.org/less-preview/ and paste the following:
```css
@background-color: #fff;
@menu-background-color: contrast(@background-color, @background-color, lighten(@background-color, 5%));
@toolbar-background-color: @background-color;
@border-color: #eee;
@button-background-color: @color-tint;
@button-enabled-background-color: darken(@button-background-color, 10%);
@color-black: #222f3e;
@color-error: #c00;
@color-success: #78AB46;
@color-tint: #006ce7;
@color-white: #fff;
@text-color: contrast(@background-color, @color-black, @color-white);
@text-color-muted: contrast(@background-color, fade(@color-black, 70%), fade(@color-white, 50%));
@dialog-background-color: contrast(@background-color, @background-color, lighten(@background-color, 5%));
@textfield-background-color: contrast(@background-color, @background-color, lighten(@background-color, 5%));
@toolbar-button-text-color: contrast(@background-color, @color-white, @color-black);
@tinymce-separator-color: #cdef5b;

.bg-luma-checker(@color-light, @color-dark) {
  @result: if((luma(@background-color) > 50%), @color-light, @color-dark);
}

.eval {
	color: /* TODO */;
}
````

Then evaluate any color expression as needed.

To get an idea of the progress:
```shell
grep -RE '(darken|fade|contrast|lighten|mix|multiply)\(' src/less/theme/ | grep -v '//' | wc -l
```
