#this is a comment
myexe : myadd.o mysub.o mydiv.o  mymul.o prog1.o
	gcc -o myexe prog1.o myadd.o mysub.o mydiv.o mymul.o 
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
clean :
	rm myexe myadd.o mysub.o mydiv.o mymul.o prog1.o 
