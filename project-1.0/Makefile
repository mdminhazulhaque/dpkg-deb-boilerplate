#!/usr/bin/make -f

.PHONY: all clean
all:
	$(MAKE) -C src/project
	$(MAKE) -C src/project install

clean:
	$(MAKE) -C src/project clean
	rm -f build/*