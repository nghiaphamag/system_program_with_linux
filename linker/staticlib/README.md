Step 1: Compile each .c file to create object file:\
  `>> ~/staticlib$ gcc -c *.c`\
Step 2: Create library which can then be linked with other objects\
  `>> ~/staticlib$ ar -rs *.o -o libmath.a`
  
Step 3: Compile .c file to object file and linker dynamic library:\
  `>> ~/staticlib/driver$ gcc -c prog1.c -I ../`\
  `>> ~/staticlib/driver$ gcc prog1.o -o myexe -lmath.so -L ../`

Step 4: Check info execute file:\
  `>> ~/staticlib/driver$ file myexe`\

Step 5: Run Program\
  `>> ~/staticlib/driver$ myexe`
