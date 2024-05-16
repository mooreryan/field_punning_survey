<!-- TOC --><a name="punning-in-various-programming-languages"></a>
# "Punning" In Various Programming Languages

A short survey of record field and function argument punning in different programming languages.

### Contents

* [Agda](#agda)
* [Haskell](#haskell)
* [JavaScript](#javascript)
* [OCaml](#ocaml)
  + [Records](#records)
  + [Function arguments](#function-arguments)
* [PureScript](#purescript)
* [Reason](#reason)
* [ReScript](#rescript)
* [Ruby](#ruby)
* [Rust](#rust)
* [License](#license)

<!-- TOC --><a name="agda"></a>
## Agda

- [Hidden Argument Puns](https://agda.readthedocs.io/en/latest/language/syntactic-sugar.html#id5) (link to Agda docs)

<!-- TOC --><a name="haskell"></a>
## Haskell

- [Record puns](https://ghc.gitlab.haskell.org/ghc/doc/users_guide/exts/record_puns.html)

<!-- TOC --><a name="javascript"></a>
## JavaScript

```javascript
var x = 1
var y = 2

var point_a = { x, y }

x *= 10
var point_b = { ...point_a, x }
```

- [Object initializer (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer)
- [Spread syntax (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

<!-- TOC --><a name="ocaml"></a>
## OCaml

Try both examples in the OCaml [playground](https://ocaml.org/play#code=dHlwZSBwb2ludCA9IHsgeCA6IGludDsgeSA6IGludH0KCigqIENvbnN0cnVjdGluZyAqKQpsZXQgcG9pbnRfYSA9IAogIGxldCB4ID0gMSBpbiBsZXQgeSA9IDIgaW4gCiAgeyB4OyB5IH0KCigqIFVwZGF0aW5nICopCmxldCBwb2ludF9iID0KICBsZXQgeCA9IDMgaW4gCiAgeyBwb2ludF9hIHdpdGggeCB9CgpsZXQgc3VidHJhY3QgfnggfnkgPSB4IC0geQoKbGV0IHggPSAzCmxldCB5ID0gMgoKbGV0IGEgPSBzdWJ0cmFjdCB%2BeCB%2BeSAoKiAxICopCmxldCBiID0gc3VidHJhY3QgfnkgfnggKCogYWxzbyAxICop).

<!-- TOC --><a name="records"></a>
### Records

```ocaml
type point = { x : int; y : int}

(* Constructing *)
let point_a = 
  let x = 1 in let y = 2 in 
  { x; y }

(* Updating *)
let point_b =
  let x = 3 in 
  { point_a with x }
```

- [Field Punning](https://dev.realworldocaml.org/records.html) (Real World OCaml book)

<!-- TOC --><a name="function-arguments"></a>
### Function arguments

```ocaml
let subtract ~x ~y = x - y

let x = 3
let y = 2

let a = subtract ~x ~y (* 1 *)1
let b = subtract ~y ~x (* also 1 *)
```


<!-- TOC --><a name="purescript"></a>
## PureScript

- [Record Puns](https://book.purescript.org/chapter4.html#record-puns) (link to PureScript docs)

<!-- TOC --><a name="reason"></a>
## Reason

- [Record Shorthand Notation](https://reasonml.github.io/docs/en/record#shorthand-notation) (link to Reason docs)

<!-- TOC --><a name="rescript"></a>
## ReScript

Try this example in the ReScript [playground](https://rescript-lang.org/try?version=v11.1.0&code=C4TwDgpgBGD2CWA7YUC8UDeAPAXFJwANFCHgQL4BQlANhCnAQPoCGamlUUdKW7AjJ270S7AExDsxEFSq0RjZEwBG7DEJ5Q+6AMySAdIcXBWxLLMpA).

```rescript
type point = {x: int, y: int}

let point_a = {
  let x = 1
  let y = 2
  {x, y}
}

let point_b = {
  let x = 3
  {...point_a, x}
}
```

<!-- TOC --><a name="ruby"></a>
## Ruby

From Ruby 3.1 [release notes](https://www.ruby-lang.org/en/news/2021/12/25/ruby-3-1-0-released/):

> - Values in Hash literals and keyword arguments can be omitted. [[Feature #14579]](https://bugs.ruby-lang.org/issues/14579)
>     - `{x:, y:}` is syntax sugar for `{x: x, y: y}`.
>     - `foo(x:, y:)` is syntax sugar for `foo(x: x, y: y)`.


<!-- TOC --><a name="rust"></a>
## Rust

[Field Init Shorthand](https://doc.rust-lang.org/book/ch05-01-defining-structs.html#using-the-field-init-shorthand) (The Rust Programming Language)

```rust
struct User {
    active: bool,
    username: String,
    email: String,
    sign_in_count: u64,
}

fn build_user(email: String, username: String) -> User {
    User {
        active: true,
        username,
        email,
        sign_in_count: 1,
    }
}
```

<!-- TOC --><a name="license"></a>
## License

<p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/mooreryan/field_punning_survey">A Field Punning Survey</a> by <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://github.com/mooreryan">Ryan M. Moore</a> is licensed under <a href="https://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">CC BY 4.0<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1" alt=""><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1" alt=""></a></p> 
