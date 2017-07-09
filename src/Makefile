# Copyright (C) 2012-2017 Hideaki Narita

PROJECTROOT=../

BINROOT=$(PROJECTROOT)bin/
BINDIR=$(BINROOT)$(PLATFORM)/$(CONFIGURATION)/
OBJROOT=obj/
OBJDIR=$(OBJROOT)$(PLATFORM)/$(CONFIGURATION)/

DESTROOT=/usr/local/
DESTBINDIR=$(DESTROOT)bin/
DESTMANDIR=$(DESTROOT)share/man/

PLATFORM=linux
CONFIGURATION=debug

######################################################################

COMPILE=$(CC) $(CFLAGS) $(CPPFLAGS) -c
LINK=$(LD) $(LDFLAGS)

CC=g++
CFLAGS=$(STDCFLAGS) $(USRCFLAGS) $(EXTCFLAGS)
CPPFLAGS=$(STDCPPFLAGS) $(USRCPPFLAGS) $(EXTCPPFLAGS)
LD=g++
LDFLAGS=$(STDLDFLAGS) $(USRLDFLAGS) $(EXTLDFLAGS)

STDCFLAGS=-Wall -Werror
STDCPPFLAGS=-DLINUX -D_GNU_SOURCE
STDLDFLAGS=

ifeq ($(CONFIGURATION), release)
USRCFLAGS=-O3
USRCPPFLAGS=
INSTALLEXEFLAGS=-m 755 -s
else
USRCFLAGS=-g
USRCPPFLAGS=-D_DEBUG
INSTALLEXEFLAGS=-m 755
endif
USRLDFLAGS=-Wl,-rpath,/usr/local/lib
USRLIBS=
INSTALLMANFLAGS=-m 644

######################################################################

RM=rm -f
RMALL=rm -fr
MKDIR=mkdir
MKDIRS=mkdir -p
INSTALL=install

######################################################################

$(OBJDIR)%.o: %.cc
	@test -d $(@D) || $(MKDIRS) $(@D)
	$(COMPILE) -o $@ $<

######################################################################

all::

clean distclean::
	$(RM) *~

clean::
	$(RMALL) $(OBJDIR)

distclean::
	$(RMALL) $(OBJROOT)

distclean::
	$(RMALL) $(BINROOT)

both:: release debug

release debug::
	$(MAKE) all CONFIGURATION=$@

release-clean::
	$(MAKE) clean CONFIGURATION=release

debug-clean::
	$(MAKE) clean CONFIGURATION=debug

release-install::
	$(MAKE) install CONFIGURATION=release

debug-install::
	$(MAKE) install CONFIGURATION=debug

######################################################################

PROG1=potmerge
PROJ1=$(BINDIR)$(PROG1)
OBJS1=\
$(OBJDIR)potmerge.o \
$(OBJDIR)MsgItem.o \
$(OBJDIR)PoFile.o
LIBS1=$(STDLIBS) $(USRLIBS) $(EXTLIBS)

$(PROJ1): $(OBJS1)
	@test -d $(@D) || $(MKDIRS) $(@D)
	$(LINK) -o $@ $(OBJS1) $(LIBS1)

all:: $(PROJ1)

install:: $(PROJ1)
	$(INSTALL) $(INSTALLEXEFLAGS) $(PROJ1) $(DESTBINDIR)$(PROG1)

install::
	$(INSTALL) $(INSTALLMANFLAGS) $(PROG1).man $(DESTMANDIR)man1/$(PROG1).1

######################################################################

PROG2=poupdate
PROJ2=$(BINDIR)$(PROG2)
OBJS2=\
$(OBJDIR)poupdate.o \
$(OBJDIR)MsgItem.o \
$(OBJDIR)PoFile.o
LIBS2=$(STDLIBS) $(USRLIBS) $(EXTLIBS)

$(PROJ2): $(OBJS2)
	@test -d $(@D) || $(MKDIRS) $(@D)
	$(LINK) -o $@ $(OBJS2) $(LIBS2)

all:: $(PROJ2)

install:: $(PROJ2)
	$(INSTALL) $(INSTALLEXEFLAGS) $(PROJ2) $(DESTBINDIR)$(PROG2)

install::
	$(INSTALL) $(INSTALLMANFLAGS) $(PROG2).man $(DESTMANDIR)man1/$(PROG2).1

######################################################################

PROG3=pocheck
PROJ3=$(BINDIR)$(PROG3)
OBJS3=\
$(OBJDIR)pocheck.o \
$(OBJDIR)MsgItem.o \
$(OBJDIR)PoFile.o
LIBS3=$(STDLIBS) $(USRLIBS) $(EXTLIBS)

$(PROJ3): $(OBJS3)
	@test -d $(@D) || $(MKDIRS) $(@D)
	$(LINK) -o $@ $(OBJS3) $(LIBS3)

all:: $(PROJ3)

install:: $(PROJ3)
	$(INSTALL) $(INSTALLEXEFLAGS) $(PROJ3) $(DESTBINDIR)$(PROG3)

install::
	$(INSTALL) $(INSTALLMANFLAGS) $(PROG3).man $(DESTMANDIR)man1/$(PROG3).1

######################################################################
