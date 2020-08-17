Step 1: Compile each .c file with -fPIC flag to create object file:\
  `>> ~/dynamiclib$ gcc -c -Wall -fPIC *.c`\
Step 2: Produce a shared object which can then be linked with other objects\
  `>> ~/dynamiclib$ gcc -shared *.o -o libmath.so`

Option: \
  -Wall: include warnings. See man page for warnings specified.\
  -fPIC: Compiler directive to output position independent code, a characteristic required by shared libraries. Also see "-fpic".\
  -shared: Produce a shared object which can then be linked with other objects to form an executable.\
  
  
Step 3: Compile .c file to object file and linker dynamic library:\
  `>> ~/dynamiclib/driver$ gcc -c prog1.c -I ../`\
  `>> ~/dynamiclib/driver$ gcc prog1.o -o myexe -lmath.so -L ../`\

Step 4: Check info execute file:\
  `>> ~/dynamiclib/driver$ file myexe`\
or the shared library dependencies of the executable can be listed with the command:\
  `>> ~/dynamiclib/driver$ ldd myexe`\
  
Step 5: Run Program\
Set path:\
  `>> ~/dynamiclib/driver$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/neko/Project/system_program_with_linux/linker/dynamiclib`\
and run:\
  `>> ~/dynamiclib/driver$ myexe`\
