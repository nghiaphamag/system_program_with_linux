<h2> Create Packaging S/W Using GNU Autotools </h2>


<pre>
All Step:
	configure.ac --> aclocal     --> aclocal.m4
	configure.ac --> autoconf    --> configure
	Makefile.am  --> automake    --> Makefile.in
	Makefile.in  --> ./configure --> Makefile
			 make dist   --> *.tar.gz	
			 
Source tree:
.
├── configure.ac
├── Makefile.am
├── myexe-1.0.tar.gz
└── src
    ├── myadd.c
    ├── mydiv.c
    ├── mymath.h
    ├── mymul.c
    ├── mysub.c
    └── prog1.c
</pre>


#### Step 1: Install Package
  Automake (GNU automake) 1.15.1
```shell
gnuautotools/ex1$ sudo apt-get install automake
```
  Autoconf (GNU Autoconf) 2.69
```shell
gnuautotools/ex1$ sudo apt-get install autoconf
```

#### Step 2: Create configure.ac file like that
```text
	AC_INIT([myexe], [1.0], [nghiaphamsg@gmail.com])
	AM_INIT_AUTOMAKE
	AC_PROG_CC([gcc cl cc])
	AC_CONFIG_FILES([Makefile])
	AC_OUTPUT
```
#### Step 3 : Automatic create "aclocal.m4" and "autom4te.cache" by use aclocal command
```shell
gnuautotools/ex1$ aclocal
```
#### Step 4 : Automatic create "configure" by use autoconf command
```shell
gnuautotools/ex1$ autoconf
```
#### Step 5 : Make "Makefile.am"
```text
	AUTOMAKE_OPTIONS=foreign
	bin_PROGRAMS = myexe
	myexe_SOURCES = src/myadd.c src/mysub.c src/mymul.c src/mydiv.c src/prog1.c src/mymath.h
```
#### Step 6: Automatic create "Makefile.in" by use automake command
```shell
gnuautotools/ex1$ automake --add-missing 
```
#### Step 7: Automatic create "Makefile" by execute configure
```shell
gnuautotools/ex1$ ./configure
```
#### Step 8: Generate package with make dist command and check package
```shell
gnuautotools/ex1$ make dist
gnuautotools/ex1$ make distcheck
```
#### Step 9: Make execute file
```shell
gnuautotools/ex1$ make
```

<h2> Create Packaging S/W Using CMAKE </h2>

<pre>
All Step:
	CMakeLists.txt --> cmake --> "Makefiles and other system required files"
	
Source tree:
.
├── build
│   ├── CMakeCache.txt
│   ├── CMakeFiles
│   ├── cmake_install.cmake
│   ├── CPackConfig.cmake
│   ├── CPackSourceConfig.cmake
│   ├── Makefile
│   └── myexe
├── CMakeLists.txt
├── include
│   └── mymath.h
├── lib
│   ├── libarifmath.a
│   └── libarifmath.so
├── man
│   └── myadd.3
└── src
    └── prog1.c
</pre>


#### Step 1: Install Package
  Cmake version 3.10.2
```shell
cmake/ex1$ sudo apt-get install cmake
```	
#### Step 2: Create CMakeLists.txt file like that:
```text
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
```
#### Step 3: Generate Makefiles and other system required files
```shell
cmake/ex1/build$ cmake ../
```
#### Step 4: Make execute file
```shell
cmake/ex1/build$ make
```
#### Step 5: Generate package by use cpack
```shell
cmake/ex1/build$ cpack --config CPackSourceConfig.cmake
```

