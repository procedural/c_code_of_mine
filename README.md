My public C code on Github:

* Compiles with Clang only. It __does not__ support GCC, MSVC or any other compiler.
* Targets Ubuntu OS only. If it works on any other OS, or if I add code for any other OS, it doesn't mean I support that OS.

My current development environment you can rely on when compiling my code:

Ubuntu 18.04.1 (x64 only), Clang 7.0, .deb dependencies from [c_ubuntu_dev_env](https://github.com/procedural/c_ubuntu_dev_env).

My C code style example:

```c
#pragma once

typedef struct Struct {
  void * structMember;
} Struct;

typedef enum Enum {
  ENUM_MEMBER = 0,
} Enum;

static inline void inlineProcedure(const Struct * parameter, float * outParameter) {
  float localVariable = 0.f;
  for (unsigned i = 0; i < 10; i += 1) {
    localVariable += 1.f;
  }
  outParameter[0] = localVariable;
}
```

Rules I follow:

* Strict aliasing is always disabled, `restrict` is never used.
* Indices are of type `unsigned`, byte counts are of type `uint64_t` (`size_t` is avoided due to Swift translating C's `size_t` to Swift's `Int` which has a different maximum value).
* Always `goto exit`, never `return` in the middle of a procedure.
* `enum` is a 32-bit `unsigned` or `int` value, misintepretation of this is a compiler's problem.
* Always separate `#if` blocks, never `#else`, never `#elif`.
* Enums are always numbered explicitly.

`CMakeLists.txt` I start with:

```cmake
set(CMAKE_C_COMPILER_FORCED TRUE)
project(main C)
add_executable(main main.c)
```

See also:

* ['static inline' is better than a macro](https://web.archive.org/web/20140906203157/https://www.kernel.org/doc/Documentation/SubmittingPatches)
* [An inline function is as fast as a macro](https://gcc.gnu.org/onlinedocs/gcc/Inline.html)
> GCC does not inline any functions when not optimizing unless you specify the ‘always_inline’ attribute for the function
