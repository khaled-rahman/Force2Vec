
CC = gcc
CFLAGS = -O3 -w 

# precision float=s, double=d 
pre = s

# See simd.h file to get correct vlen for the system and precision 
# example: for AVX512: single precision vlen=16, double vlen = 8 
# FIXME: automate the value from simd.h 
vlen = 16

# dimension 
dim = 128


all: g$(pre)kernel$(dim).h  

xextract: extract.c 
	$(CC) $(CFLAGS) -o $@ extract.c 

g$(pre)kernel$(dim).h : xextract genDimFrc.base
	./xextract -b genDimFrc.base -langC -def DIM $(dim) pre=$(pre) \
	   -def VLEN $(vlen) -o $@  

clean:
	rm -f *.h 

kill:
	rm -f xextract   
