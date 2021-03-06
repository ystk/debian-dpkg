## Process this file with automake to produce Makefile.in

localedir = $(datadir)/locale
pkgconfdir = $(sysconfdir)/@PACKAGE@

AM_CPPFLAGS = \
	-DLOCALEDIR=\"$(localedir)\" \
	-DADMINDIR=\"$(admindir)\" \
	-idirafter $(top_srcdir)/lib/compat \
	-I$(top_builddir) \
	-I$(top_srcdir)/lib


EXTRA_DIST = \
	$(test_cases)

bin_PROGRAMS = \
	dpkg \
	dpkg-divert \
	dpkg-query \
	dpkg-statoverride \
	dpkg-trigger

dpkg_SOURCES = \
	archives.c archives.h \
	cleanup.c \
	configure.c \
	depcon.c \
	enquiry.c \
	errors.c \
	filesdb.c filesdb.h \
	filters.c filters.h \
	divertdb.c \
	statdb.c \
	help.c \
	main.c main.h \
	packages.c \
	processarc.c \
	remove.c \
	select.c \
	trigproc.c \
	update.c

dpkg_LDADD = \
	../lib/dpkg/libdpkg.a \
	../lib/compat/libcompat.a \
	$(LIBINTL) \
	$(SELINUX_LIBS)

dpkg_divert_SOURCES = \
	glob.c glob.h \
	filesdb.c filesdb.h \
	divertdb.c \
	divertcmd.c

dpkg_divert_LDADD = \
	../lib/dpkg/libdpkg.a \
	../lib/compat/libcompat.a \
	$(LIBINTL)

dpkg_query_SOURCES = \
	filesdb.c filesdb.h \
	divertdb.c \
	querycmd.c

dpkg_query_LDADD = \
	../lib/dpkg/libdpkg.a \
	../lib/compat/libcompat.a \
	$(LIBINTL)

dpkg_statoverride_SOURCES = \
	glob.c glob.h \
	filesdb.c filesdb.h \
	statdb.c \
	statcmd.c

dpkg_statoverride_LDADD = \
	../lib/dpkg/libdpkg.a \
	../lib/compat/libcompat.a \
	$(LIBINTL)

dpkg_trigger_SOURCES = \
	trigcmd.c

dpkg_trigger_LDADD = \
	../lib/dpkg/libdpkg.a \
	../lib/compat/libcompat.a \
	$(LIBINTL)

install-data-local:
	$(mkdir_p) $(DESTDIR)$(pkgconfdir)/dpkg.cfg.d
	$(mkdir_p) $(DESTDIR)$(admindir)/info
	$(mkdir_p) $(DESTDIR)$(admindir)/updates

TEST_VERBOSE = 0

test_tmpdir = t.tmp

test_cases = \
	t/100_dpkg_divert.t

include $(top_srcdir)/Makecheck.am

clean-local: check-clean
