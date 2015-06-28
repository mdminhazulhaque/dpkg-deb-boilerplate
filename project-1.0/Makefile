#!/usr/bin/make -f

.PHONY: all clean

RM=rm -rf

all:
	$(MAKE) -C src/project
	$(MAKE) -C src/project install

clean:
	$(MAKE) -C src/project clean
	$(RM) debian/files
	$(RM) debian/project
	$(RM) build/*