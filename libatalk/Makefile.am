# Makefile.am for libatalk/

# This is the version info for the libatalk binary API.  It has three
# numbers:
#
#   Current  -- the number of the binary API that we're implementing
#   Revision -- which iteration of the implementation of the binary
#               API are we supplying?
#   Age      -- How many previous binary API versions do we also
#               support?
#
# To increment a VERSION_INFO (current:revision:age):
#    If the ABI didn't change, but any library code changed:
#        current:revision+1:age
#    If the ABI changed, but it's backward-compatible:
#        current+1:0:age+1
#    If the ABI changed and it isn't backward-compatible:
#        current+1:0:0
#

VERSION_INFO = 18:0:0

# History:          VERSION_INFO
#
#   3.0.0-alpha1    0:0:0
#   3.0.0-alpha2    0:0:0
#   3.0.0-alpha3    0:0:0
#   3.0.0-beta1     0:0:0
#   3.0.0-beta2     1:0:0
#   3.0             1:0:0
#   3.0.1           2:0:0
#   3.0.2           3:0:0
#   3.0.3           4:0:0
#   3.0.4           5:0:0
#   3.0.5           6:0:0
#   3.0.6           7:0:0

#   3.1.0           12:0:0
#   3.1.1           13:0:0
#   3.1.2           14:0:0
#   3.1.3           15:0:0
#   3.1.4           16:0:0
#   3.1.5           16:0:0
#   3.1.6           16:0:0
#   3.1.7           forgotten
#   3.1.8           17:0:0
#   3.1.9           17:0:0
#   3.1.10          18:0:0
#   3.1.11          18:0:0
#   3.1.12          18:0:0
#   3.1.13          18:0:0

SUBDIRS = acl adouble bstring compat cnid dsi iniparser talloc util unicode vfs

lib_LTLIBRARIES = libatalk.la

libatalk_la_SOURCES = dummy.c

libatalk_la_CFLAGS = \
	@PTHREAD_CFLAGS@

libatalk_la_LIBADD  = \
	@WRAP_LIBS@ @ACL_LIBS@ @PTHREAD_LIBS@ @MYSQL_LIBS@ \
	acl/libacl.la \
	adouble/libadouble.la	\
	bstring/libbstring.la \
	cnid/libcnid.la \
	compat/libcompat.la	\
	dsi/libdsi.la		\
	iniparser/libiniparser.la \
	talloc/libtalloc.la       \
	unicode/libunicode.la \
	util/libutil.la		\
	vfs/libvfs.la

libatalk_la_DEPENDENCIES = \
	acl/libacl.la \
	adouble/libadouble.la	\
	bstring/libbstring.la \
	cnid/libcnid.la \
	compat/libcompat.la	\
	dsi/libdsi.la		\
	talloc/libtalloc.la       \
	iniparser/libiniparser.la \
	unicode/libunicode.la \
	util/libutil.la		\
	vfs/libvfs.la

libatalk_la_LDFLAGS = -version-info $(VERSION_INFO)

if USE_BUILTIN_TDB
SUBDIRS += tdb
libatalk_la_LIBADD += tdb/libtdb.la
libatalk_la_DEPENDENCIES += tdb/libtdb.la
endif

if DEVELOPER
all-local: .libs/libatalk.so
	@$(top_srcdir)/abigen.sh .libs/libatalk.so > libatalk.abi.tmp
	@if [ ! -f libatalk-$(NETATALK_VERSION).abi ] ; then \
		cp libatalk.abi.tmp libatalk-$(NETATALK_VERSION).abi ; \
		echo "**********************************************************************************************************" ; \
		echo "                                created ABI file libatalk-$(NETATALK_VERSION).abi" ; \
		echo "    check https://sourceforge.net/apps/mediawiki/netatalk/index.php?title=Developer_Infos#ABI_checking" ; \
		echo "**********************************************************************************************************" ; \
		exit 1 ; \
	fi
	@diff -u libatalk-$(NETATALK_VERSION).abi libatalk.abi.tmp || ( \
		echo '**********************************************************************************************************' && \
		echo '***                                     libatalk ABI changed                                           ***' && \
		echo '*** check https://sourceforge.net/apps/mediawiki/netatalk/index.php?title=Developer_Infos#ABI_checking ***' && \
		echo '**********************************************************************************************************' && \
		exit 1 )

endif

EXTRA_DIST = \
	libatalk-3.0beta1.abi \
	libatalk-3.0beta2.abi \
	libatalk-3.0.abi \
	libatalk-3.0.1.abi \
	libatalk-3.0.2.abi \
	libatalk-3.0.3.abi \
	libatalk-3.0.4.abi \
	libatalk-3.0.5.abi \
	libatalk-3.0.6.abi \
	libatalk-3.1.0.abi \
	libatalk-3.1.1.abi \
	libatalk-3.1.2.abi \
	libatalk-3.1.3.abi \
	libatalk-3.1.4.abi \
	libatalk-3.1.5.abi \
	libatalk-3.1.6.abi \
	libatalk-3.1.8.abi \
	libatalk-3.1.10.abi \
	libatalk-3.1.12.abi \
	libatalk-3.1.13.abi
