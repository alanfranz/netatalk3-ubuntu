# Makefile.am for top level of netatalk package

SUBDIRS = include libatalk bin config etc contrib distrib doc man macros test

EXTRA_DIST = CONTRIBUTORS COPYRIGHT COPYING NEWS VERSION abigen.sh

ACLOCAL_AMFLAGS = -I macros
AUTOMAKE_OPTIONS = foreign

if RUN_LDCONFIG
install-exec-hook:
	@printf "Running ldconfig to ensure libraries installed in system library directories are added to the dynamic linker cache ... "
	@-@NETA_LDCONFIG@
	@printf "done\n"
endif

if DEVELOPER
abi-clean:
	@echo "Removing ABI file libatalk/libatalk-$(NETATALK_VERSION).abi"
	@rm -f libatalk/libatalk-$(NETATALK_VERSION).abi
endif
