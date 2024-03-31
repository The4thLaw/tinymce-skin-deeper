# Deeper, a TinyMCE skin using CSS variables

>_We need to go deeper_

Deeper is a TinyMCE skin based on Oxide where the LESS variables are bound to native CSS variables. This allows installations to customize the look and feel of the editor at runtime, with the downside that no color variation can be preprocessed (something that would be possible when developing a static Oxide variation).

It is meant to be compatible with Vuetify through a bridge between the Deeper and Vuetify theme variables.

## Installation

TODO

## Compatibility

This skin was tested on:

| Skin  | TinyMCE | Vuetify |
|-------|---------|---------|
| 1.0.0 | 7.0.0   | 3.5.13  |

## Development

This skin uses the [TinyMCE "creating a skin"](https://www.tiny.cloud/docs/tinymce/7/creating-a-skin/) guide from the documentation as basis.

### Running the demo

```shell
npm install
npm run start
```

### Building the skin

```shell
npm install
npm run build
```
