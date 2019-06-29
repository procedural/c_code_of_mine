My C code on Github:

* Licensed under ["MIT No Attribution" (MIT-0) license](https://github.com/aws/mit-0). Always.
* Compiles with Clang only. It __does not__ support GCC, MSVC or any other compiler.
* Targets Ubuntu OS only. If it works on any other OS, or if I add code for any other OS, it doesn't mean I support that OS.

My current development environment you can rely on when compiling my code:

Ubuntu 18.04.1 (x64), Clang 7.0, .deb dependencies from [c_ubuntu_dev_env](https://github.com/procedural/c_ubuntu_dev_env).

My C code style example:

```c
#pragma once

typedef struct Struct {
  void * structMember;
} Struct;

typedef enum Enum {
  ENUM_MEMBER = 0,
} Enum;

static inline void inlineProcedure(Struct * parameter, float * outParameter) {
  float localVariable = 0.f;
  for (unsigned i = 0; i < 10; i += 1) {
    localVariable += 1.f;
  }
  outParameter[0] = localVariable;
}
```

See also:

* ['static inline' is better than a macro](https://web.archive.org/web/20140906203157/https://www.kernel.org/doc/Documentation/SubmittingPatches)
