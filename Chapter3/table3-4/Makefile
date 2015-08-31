CC = gcc
CFLAGS = -O3 -Wall -pedantic

INCLUDE = -I../../Timing/

TIMING = ../../Timing/timing.o
REPORT = ../../Timing/report.o

TRIALS = 10000000

# default rule to build C files
.c.o: 
	$(CC) -c $(CFLAGS) $(INCLUDE) $*.c


EXECS = IntTime StringTime DivTimeInt DivTimeDouble DivTimeFloat \
	MulTimeInt MulTimeShort MulTimeDouble MulTimeFloat \
	MulTimeLongDouble SqrtTimeFloat SqrtTimeDouble

TABLE = table3-4.dat

all: $(EXECS)

DivTimeInt : DivTimeInt.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT)

DivTimeFloat : DivTimeFloat.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT)

SqrtTimeFloat : SqrtTimeFloat.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT) -lm

SqrtTimeDouble : SqrtTimeDouble.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT) -lm

DivTimeDouble : DivTimeDouble.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT)

MulTimeShort : MulTimeShort.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT)

MulTimeInt : MulTimeInt.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT)

MulTimeFloat : MulTimeFloat.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT)

MulTimeDouble : MulTimeDouble.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT)

MulTimeLongDouble : MulTimeLongDouble.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT)

IntTime : buildInt.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT)

StringTime : buildString.o
	$(CC) -o $@ $+ $(TIMING) $(REPORT)

table3-4:
	@rm -f $(TABLE)
	@echo -n "32-bit integer comparison	" >> $(TABLE)
	./IntTime -n $(TRIALS) | head -1 | sed 's/secs//' >> $(TABLE)

	@echo -n "32-bit integer multiplication	" >> $(TABLE)
	./MulTimeInt -n $(TRIALS) | head -1 | sed 's/secs//' >> $(TABLE)



	@echo -n "32-bit float multiplication	" >> $(TABLE)
	./MulTimeFloat -n $(TRIALS) | head -1 | sed 's/secs//' >> $(TABLE)

	@echo -n "64-bit double multiplication	" >> $(TABLE)
	./MulTimeDouble -n $(TRIALS) | head -1 | sed 's/secs//' >> $(TABLE)

	@echo -n "8-bit integer multiplication	" >> $(TABLE)
	./MulTimeShort -n $(TRIALS) | head -1 | sed 's/secs//' >> $(TABLE)

	@echo -n "128-bit double multiplication	" >> $(TABLE)
	./MulTimeLongDouble -n $(TRIALS) | head -1 | sed 's/secs//' >> $(TABLE)



	@echo -n "32-bit integer division, " >> $(TABLE)
	./DivTimeInt -n $(TRIALS) | head -1 | sed 's/secs//' >> $(TABLE)

	@echo -n "32-bit float division	" >> $(TABLE)
	./DivTimeFloat -n $(TRIALS) | head -1 | sed 's/secs//' >> $(TABLE)

	@echo -n "64-bit double division	" >> $(TABLE)
	./DivTimeDouble -n $(TRIALS) | head -1 | sed 's/secs//' >> $(TABLE)




	@echo -n "32-bit double square root, " >> $(TABLE)
	./SqrtTimeFloat -n $(TRIALS) | head -1 | sed 's/secs//' >> $(TABLE)

	@echo -n "64-bit double square root, " >> $(TABLE)
	./SqrtTimeDouble -n $(TRIALS) | head -1 | sed 's/secs//' >> $(TABLE)

test:
	@echo "No tests for Table 3-4"

clean:
	rm -f *.o *.class
	rm -f *~
	rm -f a.out Comparison Example_3_2 $(EXECS) $(TABLE)
