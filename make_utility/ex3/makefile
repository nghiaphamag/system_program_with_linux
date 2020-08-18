#this is a comment
myexe : myadd.o mysub.o mydiv.o  mymul.o prog1.o
	gcc -o myexe myadd.o mysub.o mydiv.o mymul.o prog1.o
myadd.o : myadd.c
	gcc -c myadd.c 
mysub.o : mysub.c
	gcc -c mysub.c 
mydiv.o : mydiv.c
	gcc -c mydiv.c
mymul.o : mymul.c
	gcc -c mymul.c
prog1.o : prog1.c mymath.h
	gcc -c prog1.c -I . 
clean:
	@rm -f *.o
install: myexe
	@cp myexe /usr/bin
	@chmod a+x /usr/bin/myexe
	@chmod og-w /usr/bin/myexe
	@echo "myexe successfully installed in /usr/bin"
uninstall:
	@rm -f /usr/bin/myexe
	@echo "myexe successfully un-installed from /usr/bin"
