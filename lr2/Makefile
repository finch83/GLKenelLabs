obj-m := hello.o

KERNELDIR := /lib/modules/`uname -r`/build

all:
	$(MAKE) -C $(KERNELDIR) SUBDIRS=$(CURDIR) modules

