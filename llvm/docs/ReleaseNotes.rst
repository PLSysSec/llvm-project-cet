=========================
LLVM 11.0.0 Release Notes
=========================

.. contents::
    :local:

.. warning::
   These are in-progress notes for the upcoming LLVM 11 release.
   Release notes for previous releases can be found on
   `the Download Page <https://releases.llvm.org/download.html>`_.


Introduction
============

This document contains the release notes for the LLVM Compiler Infrastructure,
release 11.0.0.  Here we describe the status of LLVM, including major improvements
from the previous release, improvements in various subprojects of LLVM, and
some of the current users of the code.  All LLVM releases may be downloaded
from the `LLVM releases web site <https://llvm.org/releases/>`_.

For more information about LLVM, including information about the latest
release, please check out the `main LLVM web site <https://llvm.org/>`_.  If you
have questions or comments, the `LLVM Developer's Mailing List
<https://lists.llvm.org/mailman/listinfo/llvm-dev>`_ is a good place to send
them.

Note that if you are reading this file from a Git checkout or the main
LLVM web page, this document applies to the *next* release, not the current
one.  To see the release notes for a specific release, please see the `releases
page <https://llvm.org/releases/>`_.

Non-comprehensive list of changes in this release
=================================================
.. NOTE
   For small 1-3 sentence descriptions, just add an entry at the end of
   this list. If your description won't fit comfortably in one bullet
   point (e.g. maybe you would like to give an example of the
   functionality, or simply have a lot to talk about), see the `NOTE` below
   for adding a new subsection.

* ...


.. NOTE
   If you would like to document a larger change, then you can add a
   subsection about it right here. You can copy the following boilerplate
   and un-indent it (the indentation causes it to be inside this comment).

   Special New Feature
   -------------------

   Makes programs 10x faster by doing Special New Thing.


* The inter-procedural analysis and optimization capabilities in the Attributor
  framework and pass have been substantially advanced (initial commit
  `D59918 <https://reviews.llvm.org/D59918>`_, `LLVM-Dev talk <https://youtu.be/CzWkc_JcfS0>`_).
  In this release, 19 different attributes are inferred, including 12 LLVM IR
  attributes and 7 "abstract" attributes, such as liveness. The Attributor is
  still under heavy development and disabled by default, to enable an early run
  pass ``-mllvm -attributor-disable=false`` to an invocation of clang.

* New matrix math intrinsics have been added to LLVM
  (see :ref:`LLVM Language Reference Manual <i_matrixintrinsics>`), together
  with the LowerMatrixIntrinsics pass. The pass lowers matrix intrinsics
  to a set of efficient vector instructions. The lowering pass is off
  by default and can be enabled by passing ``-mllvm -enable-matrix`` to an
  invocation of clang.


Changes to the LLVM IR
----------------------

* The callsite attribute `vector-function-abi-variant
  <https://llvm.org/docs/LangRef.html#call-site-attributes>`_ has been
  added to describe the mapping between scalar functions and vector
  functions, to enable vectorization of call sites. The information
  provided by the attribute is interfaced via the API provided by the
  ``VFDatabase`` class.

Changes to building LLVM
------------------------

...

Changes to the ARM Backend
--------------------------

During this release ...


Changes to the MIPS Target
--------------------------

During this release ...


Changes to the PowerPC Target
-----------------------------

During this release ...

Changes to the SystemZ Target
-----------------------------

* Added support for the ``-march=z15`` and ``-mtune=z15`` command line options
  (as aliases to the existing ``-march=arch13`` and ``-mtune=arch13`` options).
* Added support for the ``-march=native`` command line option.
* Added support for the ``-mfentry``, ``-mnop-mcount``, and ``-mrecord-mcount``
  command line options.
* Added support for the GHC calling convention.
* Miscellaneous codegen enhancements, in particular to enable better
  reuse of condition code values and improved use of conditional
  move instructions.

Changes to the X86 Target
-------------------------

During this release ...


* Functions with the probe-stack attribute set to "inline-asm" are now protected
  against stack clash without the need of a third-party probing function and
  with limited impact on performance.

Changes to the AMDGPU Target
-----------------------------

Changes to the AVR Target
-----------------------------

* Moved from an experimental backend to an official backend. AVR support is now
  included by default in all LLVM builds and releases and is available under
  the "avr-unknown-unknown" target triple.

Changes to the WebAssembly Target
---------------------------------

During this release ...


Changes to the OCaml bindings
-----------------------------



Changes to the C API
--------------------


Changes to the Go bindings
--------------------------


Changes to the DAG infrastructure
---------------------------------

Changes to LLDB
===============

External Open Source Projects Using LLVM 11
===========================================

Zig Programming Language
------------------------

`Zig <https://ziglang.org>`_  is a system programming language intended to be
an alternative to C. It provides high level features such as generics, compile
time function execution, and partial evaluation, while exposing low level LLVM
IR features such as aliases and intrinsics. Zig uses Clang to provide automatic
import of .h symbols, including inline functions and simple macros. Zig uses
LLD combined with lazily building compiler-rt to provide out-of-the-box
cross-compiling for all supported targets.



Additional Information
======================

A wide variety of additional information is available on the `LLVM web page
<https://llvm.org/>`_, in particular in the `documentation
<https://llvm.org/docs/>`_ section.  The web page also contains versions of the
API documentation which is up-to-date with the Git version of the source
code.  You can access versions of these documents specific to this release by
going into the ``llvm/docs/`` directory in the LLVM tree.

If you have any questions or comments about LLVM, please feel free to contact
us via the `mailing lists <https://llvm.org/docs/#mailing-lists>`_.
