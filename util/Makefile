CXXFLAGS += -Wall -D_GNU_SOURCE -std=c++11 -g -O2 \
            $(shell pkg-config --cflags libwallet)
LDFLAGS  += -L../build/ -g
LIBS     += -labc -lpthread \
            $(shell pkg-config --libs libwallet)

objects = \
	build/Commands.o \
	build/Main.o \
	build/Otp.o \
	build/Washer.o

build/abc: $(objects)
	@mkdir -p build
	$(CXX) $(LDFLAGS) -o $@ $^ $(LIBS)

clean:
	$(RM) -r build

# Automatic dependency rules:
build/%.o: %.cpp
	@mkdir -p build
	$(CXX) -c -MMD $(CXXFLAGS) -o $@ $<

include $(shell find build -name *.d)
%.h: ;
%.hpp: ;
