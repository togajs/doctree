# The DocTree Spec

[![Chat][gitter-img]][gitter-url]

Many programming languages have related projects for parsing documentation out of specially-formatted comments used to generate human-readable help files and IDE tooltips. This [specification][spec] aims to standardize a representation of parsed documentation as a language-agnostic [abstract syntax tree][ast].

[ast]: https://en.wikipedia.org/wiki/Abstract_syntax_tree
[spec]: https://github.com/togajs/doctree/blob/master/spec.idl

## History

Most documentation generators target a single language and produce their own unique output. For projects that incorporate multiple languages this dispairty can make it difficult to find, maintain, and share documentation across all project members.

This specification is the result of the desire to create a single tool capable of producing unified documentation for an entire project regardless of the languages used.

## Example

Example JavaScript input:

```js
/**
 * # Utilities
 *
 * A library of utility methods.
 *
 * @class Utilites
 * @static
 */
export const Utilities = {
    /**
     * Escapes the given `html`.
     *
     * @method escape
     * @param {String} html String to escape.
     * @return {String} Escaped html.
     */
    escape(html) {
        return String(html)
            .replace(/&/g, '&amp;')
            .replace(/</g, '&lt;')
            .replace(/>/g, '&gt;');
    }
}
```

Resulting DocTree AST as JSON:

```json
{
    "type": "Documentation",
    "blocks": [
        {
            "type": "Block",
            "comment": {
                "type": "Comment",
                "description": "# Utilities\n\nA library of utility methods.",
                "tags": [
                    {
                        "type": "Tag",
                        "tag": "class",
                        "name": "Utilities"
                    },
                    {
                        "type": "Tag",
                        "tag": "static"
                    }
                ]
            },
            "code": {
                "type": "Code",
                "code": "export const Utilities = {"
            }
        },
        {
            "type": "Block",
            "comment": {
                "type": "Comment",
                "description": "Escapes the given `html`.",
                "tags": [
                    {
                        "type": "Tag",
                        "tag": "method",
                        "name": "escape"
                    },
                    {
                        "type": "Tag",
                        "tag": "param",
                        "kind": "String",
                        "name": "html",
                        "description": "String to escape."
                    },
                    {
                        "type": "Tag",
                        "tag": "return",
                        "kind": "String",
                        "description": "Escaped html."
                    }
                ]
            },
            "code": {
                "type": "Code",
                "code": "    escape(html) {\n        return String(html)\n            .replace(/&/g, '&amp;')\n            .replace(/</g, '&lt;')\n            .replace(/>/g, '&gt;');\n    }\n}"
            }
        }
    ]
}
```

## In the Wild

- [Tunic](https://github.com/togajs/tunic) - A customizable documentation comment parser.

## Influences

### AST

- [ESTree](https://github.com/estree/estree)
- [Shift AST](https://github.com/shapesecurity/shift-spec)

### Generators

- [Docco](https://github.com/jashkenas/docco)
- [Doxygen](https://en.wikipedia.org/wiki/Doxygen)
- [Javadoc](https://en.wikipedia.org/wiki/Javadoc)
- [JSDoc](https://en.wikipedia.org/wiki/JSDoc)
- [Pandoc](https://en.wikipedia.org/wiki/Pandoc)
- [Perldoc (pod)](https://en.wikipedia.org/wiki/Perldoc)
- [PHPDoc](https://en.wikipedia.org/wiki/PHPDoc)
- [RDoc](https://en.wikipedia.org/wiki/RDoc)
- [Sphinx](https://en.wikipedia.org/wiki/Sphinx_%28documentation_generator%29)

----

© 2015 Shannon Moeller <me@shannonmoeller.com>

Licensed under [MIT](http://shannonmoeller.com/mit.txt)

[gitter-img]: http://img.shields.io/badge/gitter-join_chat-1dce73.svg?style=flat-square
[gitter-url]: https://gitter.im/togajs/doctree
