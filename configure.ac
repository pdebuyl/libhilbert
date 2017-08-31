dnl Process this file with autoconf to produce a configure script.
AC_INIT([libHilbert], [0.2-1], [chamilton@cs.dal.ca])

# Release	LibtoolVersion
# 0.2-1		2:0:0
AC_SUBST(libHilbert_la_version_info, 2:0:0)

AC_CONFIG_AUX_DIR(config)
AC_CONFIG_SRCDIR(src/Hilbert.cpp)

AM_INIT_AUTOMAKE

# Set our default flags. This is GNU specific!
CPPFLAGS="$CPPFLAGS -O2"
CFLAGS="$CFLAGS -O2"
CXXFLAGS="$CXXFLAGS -O2"

# Save the existing flags
OLDCPPFLAGS=$CPPFLAGS
OLDCFLAGS=$CFLAGS
OLDCXXFLAGS=$CXXFLAGS

# Check for the appropriate programs
AC_PROG_CXX
AC_PROG_LIBTOOL

# Restore them
CPPFLAGS=$OLDCPPFLAGS
CFLAGS=$OLDCFLAGS
CXXFLAGS=$OLDCXXFLAGS

AC_HEADER_STDC
AC_CHECK_HEADERS([inttypes.h string.h assert.h])

#####################################################################
# --enable-debug

# add checking message
AC_MSG_CHECKING(whether to build with debug information)

# create configure parameter and init variable $debuger
debugger=no
AC_ARG_ENABLE(debug,
	AC_HELP_STRING(
	    [--enable-debug],
	    [enable debug data generation [[default=no]]]
	),
  	debugger="$enableval"
)

# resulting value to screen (to complete checking message)
AC_MSG_RESULT($debugger)

# set DEBUG flag and introduce additional compiler flags
if test x"$debugger" = x"yes"; then
	AC_DEFINE(DEBUG)
	CPPFLAGS="$CPPFLAGS -g -Wall -Werror"
	CFLAGS="$CFLAGS -g -Wall -Werror"
	CXXFLAGS="$CXXFLAGS -g -Wall -Werror"
else
	AC_DEFINE(NDEBUG)
fi

#####################################################################

AC_OUTPUT(Makefile include/Makefile src/Makefile)
