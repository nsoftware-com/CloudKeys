#
# Cloud Keys 2024 .NET Edition - Sample Project
#
# This sample project demonstrates the usage of Cloud Keys in a 
# simple, straightforward way. It is not intended to be a complete 
# application. Error handling and other checks are simplified for clarity.
#
# www.nsoftware.com/cloudkeys
#
# This code is subject to the terms and conditions specified in the 
# corresponding product license agreement which outlines the authorized 
# usage and restrictions.
#

ifeq ($(shell uname -s), Darwin) # MACOS
R_PATH=-Wl,-rpath,../../lib64/,-rpath,.

FRAMEWORK = -framework Carbon -framework Security
LD_FLAGS = -lcloudkeys.24.0 -L../../lib64/ -lresolv
LD_FLAGS_SRC = -lz -lresolv
OS_CFLAGS = -D UNIX -arch arm64
MACOS = "darwin% Darwin% macos%"

all:
	g++ $(OS_CFLAGS) -D UNIX -o azurekeys azurekeys.cpp  -I../../include/ $(LD_FLAGS) $(FRAMEWORK) $(R_PATH)

src: ../../src/cloudkeys.o
	g++ $(OS_CFLAGS) -o azurekeys ../../src/cloudkeys.o azurekeys.cpp  $(LD_FLAGS_SRC) $(FRAMEWORK)

../../src/cloudkeys.o:
	g++ -c -fno-exceptions -fno-rtti -fPIC -arch arm64 -o ../../src/cloudkeys.o ../../src/cloudkeys.cpp

else # LINUX
ifeq ($(shell uname -m), x86_64)
  LIB=lib64
else
  LIB=lib
endif

R_PATH=-Wl,-rpath,../../$(LIB)/,-rpath,.
LD_FLAGS = -lcloudkeys  -L../../$(LIB)/ 
LD_FLAGS_SRC = -lz 

all:
	g++ -D UNIX -o azurekeys azurekeys.cpp  -I../../include/ $(LD_FLAGS) $(R_PATH) 

src: ../../src/cloudkeys.o
	g++ -D UNIX -o azurekeys ../../src/cloudkeys.o azurekeys.cpp  -I../../include/ $(LD_FLAGS_SRC)

../../src/cloudkeys.o:
	g++ -c -fno-exceptions -fno-rtti -fPIC -o ../../src/cloudkeys.o ../../src/cloudkeys.cpp

clean:
	rm -f ../../src/*.o
	rm -f azurekeys *.o
endif