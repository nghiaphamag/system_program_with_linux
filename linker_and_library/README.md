<h2> Dynamic Library </h2>


#### Step 1: Compile each .c file with -fPIC flag to create object file:
```shell
  ~/dynamiclib$ gcc -c -Wall -fPIC *.c
```
#### Step 2: Produce a shared object which can then be linked with other objects
```shell
  ~/dynamiclib$ gcc -shared *.o -o libmath.so
```
<pre>
Option: 
  -Wall: include warnings. See man page for warnings specified.
  -fPIC: Compiler directive to output position independent code, a characteristic required by shared libraries. Also see "-fpic".
  -shared: Produce a shared object which can then be linked with other objects to form an executable.
</pre>  
  
#### Step 3: Compile .c file to object file and linker dynamic library:
```shell
  ~/dynamiclib/driver$ gcc -c prog1.c -I ../
  ~/dynamiclib/driver$ gcc prog1.o -o myexe -lmath.so -L ../
```
#### Step 4: Check info execute file:
```shell
  ~/dynamiclib/driver$ file myexe
```
or the shared library dependencies of the executable can be listed with the command:
```shell
  ~/dynamiclib/driver$ ldd myexe
```
#### Step 5: Run Program
Set path:
```shell
  ~/dynamiclib/driver$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/neko/Project/system_program_with_linux/linker/dynamiclib
```
and run:
```shell
  ~/dynamiclib/driver$ myexe
```


<h2> Static Library </h2>


#### Step 1: Compile each .c file to create object file:
```shell
  ~/staticlib$ gcc -c *.c
```
#### Step 2: Create library which can then be linked with other objects
```shell
  ~/staticlib$ ar -rs *.o -o libmath.a
```
#### Step 3: Compile .c file to object file and linker static library:
```shell
  ~/staticlib/driver$ gcc -c prog1.c -I ../
  ~/staticlib/driver$ gcc prog1.o -o myexe -lmath.so -L ../
```
#### Step 4: Check info execute file:
```shell
  ~/staticlib/driver$ file myexe
```
#### Step 5: Run Program
```shell
  ~/staticlib/driver$ myexe
```
