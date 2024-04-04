# macro keywords
## block
> block: a sequence of statements (a block expression inside {})
- { silly; things }
It matches any sequence of statements, delimited by braces.

## expr
> expr: an expression
- 1
- x + 1
- if x == 4 { 1 } else { 2 }
It does not match statements like `let x = 1`, since it's not a single expression

## ident
> ident: an identifier (such as a variable name)
- x
- long_Identifer
Unicode strings that are not keywords (such as if or let)
As a exception, the underscore character `_` is not an identifier in Rust.

## item
> item: an item (a struct, module, etc.)
Top>level definitions are called items.
These include functions, use declarations, type definitins, and so on
- use std::io;
- fn main() { println!("hello") }
- const X: usize = 8;

## meta
> meta: a meta item (the information that goes inside attributes)
The parameters inside attributes are called meta items, which are captured by
`meta`.
- #![foo]
- #[foo]
- #[foo(bar)]
- #[foo(bar="baz")]

## pat
> pat: a pattern
Match expressions have patterns on the left-hand side of each match, which `pat`
captures.
- 1
- "x"
- t
- *t
- Some(t)
- 1 | 2 | 3
- 1 ... 3
- _

## path
> path: a qualified name
Paths are qualified names, that is, names with a namespace attached to them.
- foo
- foo::bar

## statements 
> stmt: a statement
Much like expressions, except that more patterns are accepted by stmt.
- foo
- 1
- 1 + 2
- let x = 1

## tt
> tt: a token tree
Capture a single token tree.
A token tree is either a single token (such as 1, +, or "foo bar") or several
tokens surrounded by any of the braces (), [], or {}.
- foo
- { bar; if x == 2 { 3 } else { 4 }; baz }

## ty
> ty: a type
- u32
- String

## vis
> vis: represents a visibility modifier
表示可见性修饰符，它会捕捉可见性修饰符 pub, pub(crate) 等

## lifetime
> lifetime: identifies a lifetime
表示声明周期

## literal
可以是任何标记的文字
> literal: a literal that can be token
