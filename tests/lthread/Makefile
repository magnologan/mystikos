TOP=$(abspath ../..)
include $(TOP)/defs.mak

PROGRAM = enc

SOURCES = $(SUBOBJDIR)/run_t.c enc.c

INCLUDES = $(OEENCLAVE_INCLUDES) -I$(SUBOBJDIR) -I$(BUILDDIR)/include

CFLAGS = $(OEENCLAVE_CFLAGS)

LDFLAGS = $(OEENCLAVE_LDFLAGS) -L$(LIBDIR) -llthread

CLEAN = $(SUBOBJDIR)/run_t.h $(SUBOBJDIR)/run_t.c $(SUBOBJDIR)/run_args.h

include $(TOP)/rules.mak

$(SUBOBJDIR)/run_t.c:
	$(EDGER8R) $(EDGER8R_TRUSTED_OPTS) ../run/run.edl

tests:
	$(RUNTEST) $(BINDIR)/run $(SUBBINDIR)/enc
