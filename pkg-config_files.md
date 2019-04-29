## pkg-config

##### Preliminaries
You can find the software at pkg-config's [page](https://www.freedesktop.org/wiki/Software/pkg-config/), and the available information regarding this topic is in [this](https://people.freedesktop.org/~dbn/pkg-config-guide.html) guide.

#### What is pkg-config's purpose?
In simple words, it is a way to provide necessary details for compiling and linking a program to a library. `pkg-config` tool is able to read specially formatted files and use that information for the compilation and linking. 

#### `pkg-config` files
These files have file extension `.pc` and have two types of statements: metadata keywords and freeform variables. 

There are little number of keywords. Let's take a particular example to illustrate the possible "values" these keywords may have:

 1. **Name:** `PETSc`
 2. **Description:** `Library to solve ODEs and algebraic equations`
 3. **URL:** `https://www.mcs.anl.gov/petsc/`
 4. **Version:** `3.11.0`
 5. **Requires**
 6. **Requires.private**
 7. **Conflicts**
 8. **Cflags:** `-I${includedir}`
 9. **Libs:** `-L${libdir} -lpetsc`
 10. **Libs.private:** `-L/opt/lib/intel/compilers_and_libraries_2018.3.222/linux/mkl/lib/intel64 
-L/usr/lib/x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/7 -L/lib/x86_64-linux-gnu -lm -lX11 -lpthread -lmkl_intel_ilp64 -lmkl_sequential -lmkl_core -lpthread -ldl -lstdc++ -lmpichfort -lmpich -lgfortran -lm -lgfortran -lm -lgcc_s -lquadmath -lstdc++ -ldl`

The most important keywords are **Requires**, **Requires.private**, **Cflags**, **Libs** and **Libs.private**. What does *private* mean in here? If the application you are compiling depends on some library that internally depends on some other library, you don't need to link directly against the later one.

Regarding the freeform variables, they are strings and values separated by an equal sign, and they can be used later in the definition of the keywords. They just make keywords' information more readable.

#### Some commands
There are only a few commands to use with `pkg-config` and they can be seen with `pkg-config --help` or, for a more detailed explanation, `man pkg-config`. Some of the more useful commands are:
1. `--modversion` Version of the package
2. `--cflags` Preprocessor and compile flags (duplicate flags are omitted)
3. `--libs` Linking flags (duplicate flags are omitted)
4. `--exists` Prints 0 if the file is found in the `PKG_CONFIG_PATH`
5. `--static`Libraries for static linking (includes private libraries)

#### How to use it in your code?
```
c++ `pkg-config --cflags --libs PETSc` main.cpp -o main.x
```