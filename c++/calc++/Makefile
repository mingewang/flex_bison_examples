TARGET = calc++

FLEX = flex
FLEX_OPTS = 

BISON = bison
BISON_OPTS = 

CPPSRCS = calc++.cc calc++-driver.cc calc++-parser.cc calc++-scanner.cc

CPPOBJS := $(CPPSRCS:.cpp=.o)

CPPFLAGS = -g -O3 

LDFLAGS = -s

LIBS =

all:  ${TARGET}

clean:
	@rm -rf $(TARGET)
	@rm -rf *.o
	@rm -rf calc++-parser.cc calc++-scanner.cc location.hh position.hh stack.hh

${TARGET}: ${CPPOBJS}
	$(CXX) $(LDFLAGS) -o $@ $^

calc++-scanner.cc: calc++-scanner.ll 
	${FLEX} ${FLEX_OPTS} -o calc++-scanner.cc calc++-scanner.ll 

calc++-parser.cc: calc++-parser.yy 
	${BISON} ${BISON_OPTS} --defines=calc++-parser.hh -o calc++-parser.cc calc++-parser.yy 


%.o:%.cpp
	g++ -std=c++11 $(CPPFLAGS) -c -o $@ $<

#	gcc -std=c11 $(CFLAGS) -c -o $@ $<
%.o:%.c
	g++ -x c -std=c11 $(CPPFLAGS) -c -o $@ $<
