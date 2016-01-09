SUBDIRS = src .

ACLOCAL_AMFLAGS = -I m4
include Common.am

_ltk_SOURCES =

#bin_PROGRAMS = test
#test_LDADD = libltk-${PACKAGE_VERSION}.la

LIBRARY_VERSION = 1:0:0

CONLIBS = src/libltk.la

lib_LTLIBRARIES = libltk-0.1.la
libltk_0_1_la_SOURCES = ${_ltk_SOURCES}
libltk_0_1_la_LDFLAGS = -version-info $(LIBRARY_VERSION)
libltk_0_1_la_LIBADD  = $(AM_LIBS_ALL) ${CONLIBS}

#pkgconfigdir   = $(libdir)/pkgconfig
#pkgconfig_DATA = libltk-${PACKAGE_VERSION}.pc

