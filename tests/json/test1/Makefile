TOP=$(abspath ../../..)
include $(TOP)/defs.mak

PROGRAM = jsontest1

SOURCES = $(wildcard *.c)

INCLUDES = -I$(INCDIR)

CFLAGS = $(OEHOST_CFLAGS) $(GCOV_CFLAGS)

LDFLAGS = $(OEHOST_LDFLAGS) $(GCOV_LDFLAGS)

LIBS += $(LIBDIR)/libmysthost.a
LIBS += $(LIBDIR)/libjson.a
LIBS += $(LIBDIR)/libmystutils.a

REDEFINE_TESTS=1

CLEAN = rootfs ramfs

include $(TOP)/rules.mak

tests: test1 test2

test1:
	$(RUNTEST) $(SUBBINDIR)/jsontest1 sample.json

test2:
	@ $(MKROOTFS) $(SUBBINDIR)/$(PROGRAM) rootfs sample.json
	@ $(RUNTEST) $(MYST_EXEC) rootfs /bin/$(PROGRAM) sample.json
