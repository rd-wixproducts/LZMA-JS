LZMA in a Browser
===

LZMA.JS is a JavaScript implementation of the Lempel-Ziv-Markov chain (LZMA) compression algorithm.
The JavaScript, CSS, and HTML is licensed under the MIT license.  See LICENSE for more details.

It is based on [gwt-lzma](http://code.google.com/p/gwt-lzma/), which is a port of the LZMA SDK from
Java into JavaScript.  The original Java code is licensed under the Apache License 2.0 license.

Because it is based on a GWT module, the code is unfortunately very difficult to read.  Help cleaning
up the code and making it readable would be appreciated.  It could also be optimized quite a bit.

Live demos can be found [here](http://nmrugg.github.com/LZMA-JS/ "Demos").

How to Use
---

First, load the bootstraping code.
    
    /// In a browser:
    <script src="../src/lzma.js"></script>

    /// In node:
    var LZMA = require("../src/lzma.js").LZMA;

Create the LZMA object.
    
    /// LZMA([optional path])
    /// If lzma_worker.js is in the same director, you don't need to set the path.
    var my_lzma = new LZMA("../src/lzma_worker.js");

(De)Compress stuff.

    /// To compress:
    ///NOTE: mode can be 1-9 (1 is fast but not as good; 9 will probably make your browser crash).
    my_lzma.compress(string, mode, on_finish(result) {}, on_progress (precent) {});
    
    /// To decompress:
    my_lzma.decompress(byte_array, on_finish(result) {}, on_progress (precent) {});

Note
---

The calls to compress() and decompress() are asyncronous, so you need to supply a callback function if you
want to use the (de)compressed data.