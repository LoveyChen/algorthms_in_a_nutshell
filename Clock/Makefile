CC = gcc

INCLUDE = -I../Timing/

CFLAGS = -O3 -Wall -pedantic $(INCLUDE)

# default rule to build C files
.c.o: 
	$(CC) -c $(CFLAGS) $*.c

REPORT = ../Timing/report.o
TIMING = ../Timing/timing.o  

all: test tableA-5 resolution

tableA-5: tableA-5.o
	$(CC) -o $@ $+ -lrt -lm $(REPORT)

test: forLoop.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT)

resolution : tr.o
	$(CC) -o $@ $+ -lrt

clean:
	rm -f *~ a.out *.o test sample resolution


