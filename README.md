
tinf - tiny inflate library (ALTERED)
=====================================

This is **altered** version of [jibsen/tinf](https://github.com/jibsen/tinf).

Main differences compared to original tinf library:
  - Memory for the `tinf_data` object is passed, to avoid using more than
    1k of stack space.
  - Source and destination buffer reads and writes are done using configurable
    macros, to allow flexible input/output.
  - Source code of finfzlib and tinfgzip was not adjusted to above changes, so
    they was removed to avoid confusion. Tests, tools, examples, makefiles
    were depending on it, so they were removed too.
  - Documentation fixes to reflect above changes.


About
-----

Version 1.2.1

Copyright (c) 2003-2019 Joergen Ibsen

<http://www.ibsensoftware.com/>

tinf is a small library implementing the decompression algorithm for the
[deflate][wpdeflate] compressed data format (called 'inflate'). Deflate
compression is used in e.g. zlib, gzip, zip, and png.

I wrote it because I needed a small in-memory zlib decompressor for a self-
extracting archive, and the zlib library added 15k to my program. The tinf
code added only 2k.

Naturally the size difference is insignificant in most cases. Also, the
zlib library has many more features, is well-tested, and mostly faster.
But if you have a project that calls for a small and simple deflate
decompressor, give it a try :-)

[wpdeflate]: https://en.wikipedia.org/wiki/DEFLATE


Usage
-----

The include file `src/tinf.h` contains documentation in the form of
[doxygen][] comments.

You can simply compile the source files and link them into your project.

[doxygen]: http://www.doxygen.org/


Notes
-----

tinf requires int to be at least 32-bit.

The inflate algorithm and data format are from 'DEFLATE Compressed Data
Format Specification version 1.3' ([RFC 1951][deflate]).

The original version of tinf assumed it was given valid compressed data, and
that there was sufficient space for the decompressed data. If code size is
of the utmost importance, and you are absolutely sure you can trust the
compressed data, you may want to check out [tinf 1.1.0][tinf110] (last
release without security checks).

Ideas for future versions:

  - Wrappers for unpacking zip archives and png images
  - Optional table-based Huffman decoder

[deflate]: http://www.rfc-editor.org/rfc/rfc1951.txt
[tinf110]: https://github.com/jibsen/tinf/releases/tag/v1.1.0


Related Projects
----------------

  - [puff](https://github.com/madler/zlib) (in the contrib folder of zlib)
  - [tinfl](https://github.com/richgel999/miniz) (part of miniz)
  - [uzlib](https://github.com/pfalcon/uzlib)
  - [gdunzip](https://github.com/jellehermsen/gdunzip) (GDScript)
  - [tiny-inflate](https://github.com/foliojs/tiny-inflate) (JavaScript)
  - [tinflate](http://achurch.org/tinflate.c) (unrelated to this project)
  - The [Wikipedia page for deflate](https://en.wikipedia.org/wiki/DEFLATE)
    has a list of implementations


License
-------

This projected is licensed under the [zlib License](LICENSE) (Zlib).
