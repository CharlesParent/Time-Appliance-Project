
#obj-$(CONFIG_PTP_OCP)		+= ptp_ocp.o
obj-m		+= ptp_ocp.o

KERNELDIR ?= /lib/modules/$(shell uname -r)/build

all default: modules
install: modules_install

modules modules_install help clean:
	$(MAKE) -C $(KERNELDIR) M=$(shell pwd) $@

start:
	sudo modprobe mtd
	sudo insmod ptp_ocp.ko

stop:
	sudo rmmod ptp_ocp

ioctl:
	gcc -std=gnu99 -o test_ioctl test_ioctl.c
	sudo ./test_ioctl


.PHONY: start stop ioctl

