**NOTE: This project is under active development. APIs subject to change.**

# `doc-ast`

[![Chat][gitter-img]][gitter-url] [![Tip][amazon-img]][amazon-url]

## Documentation AST Specification

- Root
  - `type` _`String`_ - Always `"Documentation"`.
  - `body` _`Array.<CommentBlock>`_
- CommentBlock
  - `type` _`String`_ - Always `"CommentBlock"`.
  - `description` _`String`_
  - `tags` _`Array.<CommentBlockTag>`_
  - `trailingCode` _`String`_
- CommentBlockTag
  - `type` _`String`_ - Always `"CommentBlockTag"`.
  - `tag` _`String`_
  - `kind` _`String`_
  - `name` _`String`_
  - `description` _`String`_

### Example

```js
/**
 * # Utilities
 *
 * A library of utility methods.
 *
 * @class Utilites
 * @static
 */
export default new class Utilities {
    /**
     * Escapes the given `html`.
     *
     * @method escape
     * @param {String} html String to escape.
     * @return {String} Escaped html.
     */
    escape(html) {
        return String(html)
            .replace(...);
    }
}
```

```json
{
    "type": "Documentation",
    "body": [
        {
            "type": "CommentBlock",
            "description": "# Utilities\n\nA library of utility methods.",
            "tags": [
                {
                    "type": "CommentBlockTag",
                    "tag": "class",
                    "name": "Utilities"
                },
                {
                    "type": "CommentBlockTag",
                    "tag": "static"
                }
            ],
            "trailingCode": "export default new class Utilities {"
        },
        {
            "type": "CommentBlock",
            "description": "Escapes the given `html`.",
            "tags": [
                {
                    "type": "CommentBlockTag",
                    "tag": "method",
                    "name": "escape"
                },
                {
                    "type": "CommentBlockTag",
                    "tag": "param",
                    "kind": "String",
                    "name": "html",
                    "description": "String to escape."
                },
                {
                    "type": "CommentBlockTag",
                    "tag": "return",
                    "kind": "String",
                    "description": "Escaped html."
                }
            ],
            "trailingCode": "    escape(html) {\n        return String(html)\n            .replace(...);\n    }\n}"
        }
    ]
}
```

## In the Wild

- [Tunic](https://github.com/togajs/tunic) - A customizable documentation comment parser.
- [toga-css](https://github.com/togajs/toga-css) - A CSS-specific documentation comment parser.
- [toga-js](https://github.com/togajs/toga-js) - A JS-specific documentation comment parser.

----

© 2015 Shannon Moeller <me@shannonmoeller.com>

Licensed under [MIT](http://shannonmoeller.com/mit.txt)

[amazon-img]:    https://img.shields.io/badge/amazon-tip_jar-yellow.svg?style=flat-square
[amazon-url]:    https://www.amazon.com/gp/registry/wishlist/1VQM9ID04YPC5?sort=universal-price
[gitter-img]:    http://img.shields.io/badge/gitter-join_chat-1dce73.svg?style=flat-square
[gitter-url]:    https://gitter.im/togajs/toga
