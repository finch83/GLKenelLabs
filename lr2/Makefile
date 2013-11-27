obj-m := hello.o

KERNELDIR := /lib/module/`uname -r`/build

all:
      $(MAKE) -C $(KERNELDIR) SUBDIRS=$(CURDIR) modules

