#!/usr/bin/make -f

CC=g++
CFLAGS=-Wall -I. -L.
EXECUTABLE=project
CP=cp -f
RM=rm -f
BUILD_DIR=../../build

all:	libproject binary
binary:
	$(CC) $(CFLAGS) main.cpp -o $(EXECUTABLE) -lproject
libproject:
	$(CC) -fPIC -c project.cpp
	$(CC) -shared -o libproject.so project.o
install:
	$(CP) libproject.so $(BUILD_DIR)
	$(CP) $(EXECUTABLE) $(BUILD_DIR)
	$(CP) project.h $(BUILD_DIR)
clean:
	$(RM) *.o libproject.so* $(EXECUTABLE)

.PHONY: all binary libproject install clean