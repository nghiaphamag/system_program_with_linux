<h1> Create Packaging S/W Using GNU Autotools </h1>


<pre>
All Step:
	configure.ac --> aclocal     --> aclocal.m4
	configure.ac --> autoconf    --> configure
	Makefile.am  --> automake    --> Makefile.in
	Makefile.in  --> ./configure --> Makefile
			 make dist   --> *.tar.gz			

Step1: Install Package
  Automake (GNU automake) 1.15.1
	>> gnuautotools/ex1$ sudo apt-get install automake

  Autoconf (GNU Autoconf) 2.69
	>> gnuautotools/ex1$ sudo apt-get install autoconf

Step2: Create configure.ac file like that
	>> AC_INIT([myexe], [1.0], [nghiaphamsg@gmail.com])
	>> AM_INIT_AUTOMAKE
	>> AC_PROG_CC([gcc cl cc])
	>> AC_CONFIG_FILES([Makefile])
	>> AC_OUTPUT

Step3: Automatic create "aclocal.m4" and "autom4te.cache" by use aclocal command
	>> gnuautotools/ex1$ aclocal

Step4: Automatic create "configure" by use autoconf command
        >> gnuautotools/ex1$ autoconf

Step5: Make "Makefile.am"
	>> AUTOMAKE_OPTIONS=foreign
	>> bin_PROGRAMS = myexe
	>> myexe_SOURCES = src/myadd.c src/mysub.c src/mymul.c src/mydiv.c src/prog1.c src/mymath.h

Step6: Automatic create "Makefile.in" by use automake command
	>> gnuautotools/ex1$ automake --add-missing 

Step7: Automatic create "Makefile" by execute configure 
	>> gnuautotools/ex1$ ./configure

Step8: Generate package with make dist command and check package
	>> gnuautotools/ex1$ make dist
	>> gnuautotools/ex1$ make distcheck
Step9: Make execute file
	>> gnuautotools/ex1$ make
</pre>


