# Comment/uncomment the following line to disable/enable debugging
# DEBUG = y

# Add your debugging flag (or not) to CFLAGS
ifeq ($(DEBUG),y)
  EXTRA_CFLAGS += -O -g -DSCULL_DEBUG
else
  EXTRA_CFLAGS += -O2
endif

#----------------------------------------------------------------------
# When built from kernel (Buildroot calls this way)
#----------------------------------------------------------------------
ifneq ($(KERNELRELEASE),)
scull-objs := main.o pipe.o access.o
obj-m := scull.o

#----------------------------------------------------------------------
# When built manually (developer convenience)
#----------------------------------------------------------------------
else
KERNELDIR ?= /lib/modules/$(shell uname -r)/build
PWD       := $(shell pwd)

modules:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) modules

clean:
	rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions modules.order *.symvers

endif