OPT=-O3 -DNDEBUG

all: libfsst.a

clean:
	-@rm -f libfsst.[oa] fsst_avx512.o

libfsst.a: libfsst.cpp libfsst.hpp fsst.h fsst_avx512.o
	c++ -std=c++17 -W -Wall -c $(OPT) $(CXXFLAGS) -g libfsst.cpp 
	ar ru $@ libfsst.o fsst_avx512.o 
	ranlib $@

fsst_avx512.o: fsst_avx512.cpp fsst_avx512_unroll1.inc fsst_avx512_unroll2.inc fsst_avx512_unroll3.inc fsst_avx512_unroll4.inc
	g++ -std=c++17 -W -Wall -g -O1 $(CXXFLAGS) -c fsst_avx512.cpp # -O1: no constant propagation reduces register pressure and improves unrolling
