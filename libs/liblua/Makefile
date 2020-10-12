# Makefile for building Lua
# See ../doc/readme.html for installation and customization instructions.

# == CHANGE THE SETTINGS BELOW TO SUIT YOUR ENVIRONMENT =======================
-include $(TOPDIR)/Make.defs

# ifeq ($(CONFIG_LIBCXX),y)
# LIBXX=libcxx
# else
# LIBXX=libxx
# endif
LIBLUA=liblua
# Sources

ASRCS =

CSRCS =
CSRCS += lapi.c
CSRCS += lauxlib.c
CSRCS += lbaselib.c
CSRCS += lcode.c
CSRCS += lcorolib.c
CSRCS += lctype.c
CSRCS += ldblib.c
CSRCS += ldebug.c
CSRCS += ldo.c
CSRCS += ldump.c
CSRCS += lfunc.c
CSRCS += lgc.c
CSRCS += linit.c
CSRCS += liolib.c
CSRCS += llex.c
CSRCS += lmathlib.c
CSRCS += lmem.c
CSRCS += loadlib.c
CSRCS += lobject.c
CSRCS += lopcodes.c
CSRCS += loslib.c
CSRCS += lparser.c
CSRCS += lstate.c
CSRCS += lstring.c
CSRCS += lstrlib.c
CSRCS += ltable.c
CSRCS += ltablib.c
CSRCS += ltm.c
CSRCS += lundump.c
CSRCS += lutf8lib.c
CSRCS += lvm.c
CSRCS += lzio.c

CXXSRCS  = 

# CFLAGS += -DLUA_USE_LINUX -std=gnu99 -lm -O2 -Wall -Wextra -DLUA_COMPAT_5_3 -Wl,-E -ldl
# Some of the libs/libxx/ files are not need if uClibc++ or libcxx is installed
# because uClibx++ or libcxx will replace them

# Paths

DEPPATH = --dep-path .
VPATH = .

# Include the uClibc++ Make.defs file if selected.  If it is included,
# the uClibc++/Make.defs file will add its files to the source file list,
# add its DEPPATH info, and will add the appropriate paths to the VPATH
# variable
#
# Note that an error will occur if you select CONFIG_LIBXX_UCLIBCXX
# without installing the uClibc++ package.  This is intentional to let
# you know about the configuration problem.  Refer to the README.txt file
# in the NuttX uClibc++ GIT repository for more information

# ifeq ($(CONFIG_UCLIBCXX),y)
# include uClibc++/Make.defs
# endif

# ifeq ($(CONFIG_LIBCXX),y)
# include libcxx/Make.defs
# endif

# Object Files

AOBJS = $(ASRCS:.S=$(OBJEXT))
COBJS = $(CSRCS:.c=$(OBJEXT))
CXXOBJS = $(CXXSRCS:.cxx=$(OBJEXT))

SRCS = $(ASRCS) $(CSRCS) $(CXXSRCS)
OBJS = $(AOBJS) $(COBJS) $(CXXOBJS)

BIN = $(LIBLUA)$(LIBEXT)

all: $(BIN)
.PHONY: depend clean distclean

$(AOBJS): %$(OBJEXT): %.S
	$(call ASSEMBLE, $<, $@)

$(COBJS): %$(OBJEXT): %.c
	$(call COMPILE, $<, $@)

$(CXXOBJS): %$(OBJEXT): %.cxx
	$(call COMPILEXX, $<, $@)

$(BIN):	$(OBJS)
	$(call ARCHIVE, $@, $(OBJS))

.depend: Makefile $(SRCS) $(TOPDIR)$(DELIM).config
	$(Q) $(MKDEP) $(DEPPATH) "$(CXX)" -- $(CXXFLAGS) -- $(SRCS) >Make.dep
	$(Q) touch $@

depend: .depend

clean:
	$(call DELFILE, $(BIN))
	$(call CLEAN)

distclean: clean
	$(call DELFILE, Make.dep)
	$(call DELFILE, .depend)

-include Make.dep

# DO NOT DELETE

# lapi.o: lapi.c lprefix.h lua.h luaconf.h lapi.h llimits.h lstate.h \
#  lobject.h ltm.h lzio.h lmem.h ldebug.h ldo.h lfunc.h lgc.h lstring.h \
#  ltable.h lundump.h lvm.h
# lauxlib.o: lauxlib.c lprefix.h lua.h luaconf.h lauxlib.h
# lbaselib.o: lbaselib.c lprefix.h lua.h luaconf.h lauxlib.h lualib.h
# lcode.o: lcode.c lprefix.h lua.h luaconf.h lcode.h llex.h lobject.h \
#  llimits.h lzio.h lmem.h lopcodes.h lparser.h ldebug.h lstate.h ltm.h \
#  ldo.h lgc.h lstring.h ltable.h lvm.h
# lcorolib.o: lcorolib.c lprefix.h lua.h luaconf.h lauxlib.h lualib.h
# lctype.o: lctype.c lprefix.h lctype.h lua.h luaconf.h llimits.h
# ldblib.o: ldblib.c lprefix.h lua.h luaconf.h lauxlib.h lualib.h
# ldebug.o: ldebug.c lprefix.h lua.h luaconf.h lapi.h llimits.h lstate.h \
#  lobject.h ltm.h lzio.h lmem.h lcode.h llex.h lopcodes.h lparser.h \
#  ldebug.h ldo.h lfunc.h lstring.h lgc.h ltable.h lvm.h
# ldo.o: ldo.c lprefix.h lua.h luaconf.h lapi.h llimits.h lstate.h \
#  lobject.h ltm.h lzio.h lmem.h ldebug.h ldo.h lfunc.h lgc.h lopcodes.h \
#  lparser.h lstring.h ltable.h lundump.h lvm.h
# ldump.o: ldump.c lprefix.h lua.h luaconf.h lobject.h llimits.h lstate.h \
#  ltm.h lzio.h lmem.h lundump.h
# lfunc.o: lfunc.c lprefix.h lua.h luaconf.h ldebug.h lstate.h lobject.h \
#  llimits.h ltm.h lzio.h lmem.h ldo.h lfunc.h lgc.h
# lgc.o: lgc.c lprefix.h lua.h luaconf.h ldebug.h lstate.h lobject.h \
#  llimits.h ltm.h lzio.h lmem.h ldo.h lfunc.h lgc.h lstring.h ltable.h
# linit.o: linit.c lprefix.h lua.h luaconf.h lualib.h lauxlib.h
# liolib.o: liolib.c lprefix.h lua.h luaconf.h lauxlib.h lualib.h
# llex.o: llex.c lprefix.h lua.h luaconf.h lctype.h llimits.h ldebug.h \
#  lstate.h lobject.h ltm.h lzio.h lmem.h ldo.h lgc.h llex.h lparser.h \
#  lstring.h ltable.h
# lmathlib.o: lmathlib.c lprefix.h lua.h luaconf.h lauxlib.h lualib.h
# lmem.o: lmem.c lprefix.h lua.h luaconf.h ldebug.h lstate.h lobject.h \
#  llimits.h ltm.h lzio.h lmem.h ldo.h lgc.h
# loadlib.o: loadlib.c lprefix.h lua.h luaconf.h lauxlib.h lualib.h
# lobject.o: lobject.c lprefix.h lua.h luaconf.h lctype.h llimits.h \
#  ldebug.h lstate.h lobject.h ltm.h lzio.h lmem.h ldo.h lstring.h lgc.h \
#  lvm.h
# lopcodes.o: lopcodes.c lprefix.h lopcodes.h llimits.h lua.h luaconf.h
# loslib.o: loslib.c lprefix.h lua.h luaconf.h lauxlib.h lualib.h
# lparser.o: lparser.c lprefix.h lua.h luaconf.h lcode.h llex.h lobject.h \
#  llimits.h lzio.h lmem.h lopcodes.h lparser.h ldebug.h lstate.h ltm.h \
#  ldo.h lfunc.h lstring.h lgc.h ltable.h
# lstate.o: lstate.c lprefix.h lua.h luaconf.h lapi.h llimits.h lstate.h \
#  lobject.h ltm.h lzio.h lmem.h ldebug.h ldo.h lfunc.h lgc.h llex.h \
#  lstring.h ltable.h
# lstring.o: lstring.c lprefix.h lua.h luaconf.h ldebug.h lstate.h \
#  lobject.h llimits.h ltm.h lzio.h lmem.h ldo.h lstring.h lgc.h
# lstrlib.o: lstrlib.c lprefix.h lua.h luaconf.h lauxlib.h lualib.h
# ltable.o: ltable.c lprefix.h lua.h luaconf.h ldebug.h lstate.h lobject.h \
#  llimits.h ltm.h lzio.h lmem.h ldo.h lgc.h lstring.h ltable.h lvm.h
# ltablib.o: ltablib.c lprefix.h lua.h luaconf.h lauxlib.h lualib.h
# ltm.o: ltm.c lprefix.h lua.h luaconf.h ldebug.h lstate.h lobject.h \
#  llimits.h ltm.h lzio.h lmem.h ldo.h lgc.h lstring.h ltable.h lvm.h
# lua.o: lua.c lprefix.h lua.h luaconf.h lauxlib.h lualib.h
# luac.o: luac.c lprefix.h lua.h luaconf.h lauxlib.h ldebug.h lstate.h \
#  lobject.h llimits.h ltm.h lzio.h lmem.h lopcodes.h lopnames.h lundump.h
# lundump.o: lundump.c lprefix.h lua.h luaconf.h ldebug.h lstate.h \
#  lobject.h llimits.h ltm.h lzio.h lmem.h ldo.h lfunc.h lstring.h lgc.h \
#  lundump.h
# lutf8lib.o: lutf8lib.c lprefix.h lua.h luaconf.h lauxlib.h lualib.h
# lvm.o: lvm.c lprefix.h lua.h luaconf.h ldebug.h lstate.h lobject.h \
#  llimits.h ltm.h lzio.h lmem.h ldo.h lfunc.h lgc.h lopcodes.h lstring.h \
#  ltable.h lvm.h ljumptab.h
# lzio.o: lzio.c lprefix.h lua.h luaconf.h llimits.h lmem.h lstate.h \
#  lobject.h ltm.h lzio.h

# (end of Makefile)
