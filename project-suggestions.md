# Project suggestions

## Parallel seam-carving

Seam Carving is a technique for doing content-aware resizing of
images - that is, shrinking the size of an image while minimising loss
of detail.  Sam Westrick, author of
[MaPLe](https://github.com/MPLLang/mpl), has written an [excellent
article on his own implementation in parallel
SML](https://shwestrick.github.io/2020/07/29/seam-carve.html).  This
project involves implementing seam carving in a parallel language,
such as Futhark or ISPC.

You almost certainly cannot base your work on Sam Westrick's
implementation, but his article also explains the algorithm in
high-level detail, which you can use as inspiration for your own
implementation.

## Porting a Parboil benchmark to a parallel language

[Parboil](http://impact.crhc.illinois.edu/parboil/parboil.aspx) is a
suite of benchmarks that is used when presenting new research into
compilers or parallel programming.  This project is about picking one
of the benchmarks and porting it to a parallel language covered in
class (I prefer Futhark, but if you want to use `ispc` or Parallel
Haskell, that's fine too).  For Futhark, [we already have
implementations of `histo`, `mri-q`, `sgemm`, `stencil`, and
`tpacf`](https://github.com/diku-dk/futhark-benchmarks/tree/master/parboil),
so we are mostly interested in the remaining ones.
