# make ... for both libusb and libsg
#
# make CONFIG_USE_LIBSG=0 ...
# for just libusb
#

PRG := st-util
OBJS = gdb-remote.o gdb-server.o

CFLAGS+=-g -Wall -Werror -std=gnu99 -I../src
CFLAGS+=-DCONFIG_USE_LIBUSB=1
LDFLAGS=-lusb-1.0 -L.. -lstlink 

ifeq ($(CONFIG_USE_LIBSG),)
CONFIG_USE_LIBSG=1
endif

ifneq ($(CONFIG_USE_LIBSG),0)
CFLAGS+=-DCONFIG_USE_LIBSG=1
LDFLAGS+=-lsgutils2
endif

all: $(PRG)

$(PRG): $(OBJS)
	$(CC) -o $@  $^ $(LDFLAGS)

clean:
	rm -rf $(OBJS)
	rm -rf $(PRG)

.PHONY: clean all
