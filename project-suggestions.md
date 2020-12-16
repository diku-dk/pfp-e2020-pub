# Project suggestions

These projects are intentionally open-ended.  They are intended as an
opportunity for you to showcase your mastery of the learning goals:

* Parallel algorithmic reasoning.

* Parallel cost models.

* Judging the suitability of the language/tool for the problem at
  hand.

* Applied data-parallel programming.

This means that you are free to diverge from the project descriptions
below, or come up with your own ideas, as long as they provide a
context in which you can demonstrate the course contents.

You are *not* judged on whether e.g. Futhark happens to be a good fit
or run particularly fast for whatever problem you end up picking, but
you *are* judged on how you evaluate its suitability.  For that
matter, you also don't have to use Futhark.

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

## A sparse matrix library in Futhark

Construct a library of sparse matrix operations in Futhark, including,
for instance, operations for rotations, matrix-matrix-muliply,
matrix-vector multiply, matrix transpose, and matrix inverse. Evaluate
the library using a number of tests and discuss the parallel
performance of the operations. Use the library for an example
application.

A number of different sparse matrix representations are possible,
including compressed sparse row (CSR) and compressed sparse column
(CSC) representations. [See the Wikipedia article for
more](https://en.wikipedia.org/wiki/Sparse_matrix).

## Parallel implementation of Simplex

The [Simplex
algorithm](https://en.wikipedia.org/wiki/Simplex_algorithm) is a
popular technique for linear programming.  It maximises cost functions
of a certain form and is widely used in practice.  There is a bunch of
published work on parallelising it
([here](https://dl.acm.org/doi/10.1016/S0167-6377%2800%2900017-1),
[here](https://dl.acm.org/doi/10.1109/IPDPS.2011.362),
[here](https://www.sciencedirect.com/science/article/abs/pii/S0096300314014714)).
This project is about reading the prior work and implementing one or
more of these approaches in a parallel programming language and seeing
if you can beat established implementations of linear programming.

## Futhark implementations of function optimisation techniques

We've covered automatic differentiation in one of our lectures.
Automatic differentiation is mostly a building block in optimisation
procedures.  This project is about finding one such procedure,
figuring out how it can be made parallel (*strongly* recommended by
building on prior work), and then implementing it.

One such optimisation technique is
[Nelder-Mead](https://en.wikipedia.org/wiki/Nelder%E2%80%93Mead_method),
which is particularly useful when the function being optimised is not
differentiable.

[Gradient descent](https://en.wikipedia.org/wiki/Gradient_descent) is
an extremely popular technique for finding local minima of
differentiable functions, and is widely used for deep learning.  It's
pretty straightforward to implement basic gradient descent, so this
would ideally also involve looking at variants (stocastic, conjugate,
or evolutionary gradient descent).

Implementing [simulated
annealing](https://en.wikipedia.org/wiki/Simulated_annealing) also
sounds fun.

## EmbedSOM

[EmbedSOM](https://github.com/exaexa/EmbedSOM) does "embedding and
visualization of multidimensional datasets"
([paper](https://f1000research.com/articles/8-2120)).  [The core loop
looks like
this](https://github.com/exaexa/EmbedSOM/blob/b118a0eba4ad486ef32288d5c88c55ffe6d33e96/src/embed.cpp#L391-L401).
At a high level, for each point we need to compute the
*k*-nearest-neighbours, and then do some operations for these
neighbours.  It would be cool to see if we could make this run faster
than the current CPU implementation!  This is a very *interesting*
project, but it is definitely only suitable if you are very
comfortable with applied parallel programming and reading existing C++
code (which doesn't look that bad for C++, admittedly).  It's also
good to have some friends - I think this project is too big for a
single student.

## Approximate Nearest Neighbor Fields (ANNFs)

ANNFs is a central in computer vision, being used in many tasks such
as inpainting in videos, super-resolution, denoising. Essentially,
computing ANNFs consists of decomposing the image pair into overlapping
patches, and then finding for every patch of the first image a patch
in the second image that approximates it well. Since computing the
best match is too (computationally) expensive---i.e., the nearest-neighbor
patch---fast approximate methods have been proposed such as 
[Patch Match](material/ANNFs/patch-match.pdf) or 
[Coherency Sensitive Hashing](material/ANNFs/coherency-sens-hash.pdf) or
[Propagation-Assisted KD Trees](material/ANNFs/annf-kdtrees.pdf).

Your task would be to develop a GPU implementation (in Futhark, or CUDA,
or in your favorite data-parallel language) for either "Patch Match" or
"Coherency Sensitive Hashing" methods for computing ANNFs.
If you find it helpful, you may use the framework available at
[this github project](https://github.com/diku-dk/annfmp).

## Automatic Differentiation

A set of programs that use automatic differentiation and which are written in
Jax can be found [here](https://github.com/google/jax/tree/master/examples).

The task for this project is simple:

* chose one or more such programs and analyse its parallelism

* rewrite it in Futhark in a data-parallel fashion

* apply the reverse differentiation rules presented in the last two lectures
  (or/and invent your own) to infer a semantically-equivalent program
  that also computes the jacobian (gradient).

* validate against the Jax implementation and compare the performance
  of the Jax and Futhark solutions.

## Bioinformatics Projects (proposed by your colleagues Xuening and Maya)

There are four such bio-informatics projects that are briefly described
in this [document](material/bioinformatics/PFP_project_proposals_Bioinf.pdf)
