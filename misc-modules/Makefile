# Optional debugging flags
EXTRA_CFLAGS += -O2

# Include path for headers (only used when manually building)
LDDINC := $(PWD)/../include

#----------------------------------------------------------------------
# When built from within the kernel (Buildroot path)
#----------------------------------------------------------------------
ifneq ($(KERNELRELEASE),)
# List of all module object files to build
obj-m := hello.o hellop.o seq.o jiq.o sleepy.o complete.o \
         silly.o faulty.o kdatasize.o kdataalign.o jit.o

#----------------------------------------------------------------------
# When built manually (developer convenience)
#----------------------------------------------------------------------
else

KERNELDIR ?= /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

modules:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) modules

clean:
	rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions modules.order *.symvers

.PHONY: modules clean

endif
