# bf

a tiny [brainfuck] interpreter

_This project is not meant to be practical. It is an exercise in
[code golf]._

My goal was to make a brainfuck interpreter with JavaScript in 140
bytes. That did not happen, but it is only `249` bytes. In order
to accomplish this some rules were broken. All the variables are leaked
into the global scope and they all have single byte names. There is no
indentation. The entire logic is performed in a single `for` loop. It
relies on the scope chain to find required identifiers outside of its
own logic (mainly because input and output are environment dependent).

Now for the good parts. It is small, but still maintainable. Each line
only performs one task (just in a slightly convoluted manner). It
follows the brainfuck implementation standards as closely as possible,
which is easy because there really isn't a [standard]. And finally, the
code doesn't take long to read (but probably a little longer to
understand).

## usage

Since `input` and `output` are dependent on the environment, they need
to be implemented before running the interpreter. The scope chain is
checked for the existence of three identifiers (`B`, `I` and `O`).

- `B` string of brainfuck code to run
- `I` string of input for the brainfuck code
- `O` callback function to handle output. It is passed a single
  parameter containing the character to write.

**Warning**: The following global variables are created:
`$`,`F`,`U`,`C`,`K`,`_`,`f`,`u`,`c`,`k`

Check the `index.js` file and `examples` directory for implementation
details.

## examples

There are HTML (browser) and Nodejs (CLI) demos in the examples
directory. The [HTML demo is live here][html] and the
[Nodejs CLI example][cli] is called `bf`. CLI usage:

```sh
bf <file> [input]

bf hello.b
bf rot13.b 'hello world'
```

## license

```txt
Copyright (C) 2022 Randy Schneck
This program is free software. It comes without any warranty, to
the extent permitted by applicable law. You can redistribute it
and/or modify it under the terms of the Do What The Fuck You Want
To Public License, Version 2, as published by Sam Hocevar. See
the LICENSE file for more details.
```

[brainfuck]: https://en.wikipedia.org/wiki/Brainfuck
[standard]: http://www.muppetlabs.com/~breadbox/bf/standards.html
[code golf]: https://en.wikipedia.org/wiki/Code_golf
[html]: https://rasch.srht.site/bf/demo/
[cli]: https://git.sr.ht/~rasch/bf/blob/main/examples/bf
