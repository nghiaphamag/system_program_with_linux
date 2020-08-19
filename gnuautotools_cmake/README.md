<h2> Create Packaging S/W Using GNU Autotools </h2>


<pre>
All Step:
	configure.ac --> aclocal     --> aclocal.m4
	configure.ac --> autoconf    --> configure
	Makefile.am  --> automake    --> Makefile.in
	Makefile.in  --> ./configure --> Makefile
			 make dist   --> *.tar.gz			
</pre>

<pre>
Step1: Install Package
  Automake (GNU automake) 1.15.1
	>> gnuautotools/ex1$ sudo apt-get install automake

  Autoconf (GNU Autoconf) 2.69
	>> gnuautotools/ex1$ sudo apt-get install autoconf

Step2: Create configure.ac file like that
	AC_INIT([myexe], [1.0], [nghiaphamsg@gmail.com])
	AM_INIT_AUTOMAKE
	AC_PROG_CC([gcc cl cc])
	AC_CONFIG_FILES([Makefile])
	AC_OUTPUT

Step3: Automatic create "aclocal.m4" and "autom4te.cache" by use aclocal command
	>> gnuautotools/ex1$ aclocal

Step4: Automatic create "configure" by use autoconf command
        >> gnuautotools/ex1$ autoconf

Step5: Make "Makefile.am"
	AUTOMAKE_OPTIONS=foreign
	bin_PROGRAMS = myexe
	myexe_SOURCES = src/myadd.c src/mysub.c src/mymul.c src/mydiv.c src/prog1.c src/mymath.h

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

<h2> Create Packaging S/W Using CMAKE </h2>

<pre>
All Step:
	CMakeLists.txt --> cmake --> "Makefiles and other system required files"
</pre>

<pre>
Step1: Install Package
  Cmake version 3.10.2
	>> cmake/ex1$ sudo apt-get install cmake
	
Step2: Create CMakeLists.txt file like that:

	cmake_minimum_required (VERSION 3.7)
	project(ex1_cmakeproject)

	include_directories(${CMAKE_SOURCE_DIR}/include)
	link_directories(${CMAKE_SOURCE_DIR}/lib)

	set(SOURCES src/prog1.c)
	add_executable(myexe ${PROJECT_SOURCE_DIR}/${SOURCES})

	target_link_libraries(myexe libc.so libarifmath.a)

	install(TARGETS myexe DESTINATION /usr/bin)
	install(FILES man/myadd.3 DESTINATION /usr/share/man/man3)


	include(InstallRequiredSystemLibraries)
	set(CPACK_GENERATOR "DEB")
	set(CPACK_DEBIAN_PACKAGE_MAINTAINER "NekoBot")
	set(CMAKE_C_STANDARD 11)
	set(CMAKE_C_STANDARD_REQUIRED True)
	include(CPack)

Step3: Generate Makefiles and other system required files
	>> cmake/ex1/build$ cmake ../

Step4: Make execute file
	>> cmake/ex1/build$ make
	
Step5: Generate package by use cpack
	>> cmake/ex1/build$ cpack --config CPackSourceConfig.cmake

</pre>
