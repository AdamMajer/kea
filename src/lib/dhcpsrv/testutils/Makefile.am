SUBDIRS = .

AM_CPPFLAGS = -I$(top_builddir)/src/lib -I$(top_srcdir)/src/lib
AM_CPPFLAGS += -DDATABASE_SCRIPTS_DIR=\"$(abs_top_srcdir)/src/share/database/scripts\"
AM_CPPFLAGS += $(BOOST_INCLUDES)

AM_CXXFLAGS = $(KEA_CXXFLAGS)

CLEANFILES = *.gcno *.gcda

if HAVE_GTEST

noinst_LTLIBRARIES = libdhcpsrvtest.la

libdhcpsrvtest_la_SOURCES  = config_result_check.cc config_result_check.h
libdhcpsrvtest_la_SOURCES += dhcp4o6_test_ipc.cc dhcp4o6_test_ipc.h

if HAVE_MYSQL
libdhcpsrvtest_la_SOURCES += schema.cc schema.h
else
if HAVE_PGSQL
libdhcpsrvtest_la_SOURCES += schema.cc schema.h
else
if HAVE_CQL
libdhcpsrvtest_la_SOURCES += schema.cc schema.h
endif
endif
endif

if HAVE_MYSQL
libdhcpsrvtest_la_SOURCES += mysql_schema.cc mysql_schema.h
endif
if HAVE_PGSQL
libdhcpsrvtest_la_SOURCES += pgsql_schema.cc pgsql_schema.h
endif
if HAVE_CQL
libdhcpsrvtest_la_SOURCES += cql_schema.cc cql_schema.h
endif

libdhcpsrvtest_la_CXXFLAGS = $(AM_CXXFLAGS)
libdhcpsrvtest_la_CPPFLAGS = $(AM_CPPFLAGS) $(GTEST_INCLUDES)
if HAVE_MYSQL
libdhcpsrvtest_la_CPPFLAGS += $(MYSQL_CPPFLAGS)
endif
if HAVE_PGSQL
libdhcpsrvtest_la_CPPFLAGS += $(PGSQL_CPPFLAGS)
endif
if HAVE_CQL
libdhcpsrvtest_la_CPPFLAGS += $(CQL_CPPFLAGS)
endif

libdhcpsrvtest_la_LDFLAGS  = $(AM_LDFLAGS)
if HAVE_MYSQL
libdhcpsrvtest_la_LDFLAGS  += $(MYSQL_LIBS)
endif
if HAVE_PGSQL
libdhcpsrvtest_la_LDFLAGS  += $(PGSQL_LIBS)
endif
if HAVE_CQL
libdhcpsrvtest_la_LDFLAGS  += $(CQL_LIBS)
endif

libdhcpsrvtest_la_LIBADD   = $(top_builddir)/src/lib/cc/libkea-cc.la
libdhcpsrvtest_la_LIBADD  += $(top_builddir)/src/lib/log/libkea-log.la

endif
