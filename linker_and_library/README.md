<h2> Dynamic Library </h2>

<pre>
Step 1: Compile each .c file with -fPIC flag to create object file:
  >> ~/dynamiclib$ gcc -c -Wall -fPIC *.c
Step 2: Produce a shared object which can then be linked with other objects
  >> ~/dynamiclib$ gcc -shared *.o -o libmath.so

Option: 
  -Wall: include warnings. See man page for warnings specified.
  -fPIC: Compiler directive to output position independent code, a characteristic required by shared libraries. Also see "-fpic".
  -shared: Produce a shared object which can then be linked with other objects to form an executable.
  
  
Step 3: Compile .c file to object file and linker dynamic library:
  >> ~/dynamiclib/driver$ gcc -c prog1.c -I ../
  >> ~/dynamiclib/driver$ gcc prog1.o -o myexe -lmath.so -L ../

Step 4: Check info execute file:
  >> ~/dynamiclib/driver$ file myexe
or the shared library dependencies of the executable can be listed with the command:
  >> ~/dynamiclib/driver$ ldd myexe
  
Step 5: Run Program
Set path:
  >> ~/dynamiclib/driver$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/neko/Project/system_program_with_linux/linker/dynamiclib
and run:
  >> ~/dynamiclib/driver$ myexe
</pre>


<h2> Static Library </h2>

<pre>
Step 1: Compile each .c file to create object file:
  >> ~/staticlib$ gcc -c *.c
Step 2: Create library which can then be linked with other objects
  >> ~/staticlib$ ar -rs *.o -o libmath.a
  
Step 3: Compile .c file to object file and linker dynamic library:
  >> ~/staticlib/driver$ gcc -c prog1.c -I ../
  >> ~/staticlib/driver$ gcc prog1.o -o myexe -lmath.so -L ../

Step 4: Check info execute file:
  >> ~/staticlib/driver$ file myexe

Step 5: Run Program
  >> ~/staticlib/driver$ myexe
</pre>
