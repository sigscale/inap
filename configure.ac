## configure.ac ## vim: ts=3
##
## Process this file with autoconf to produce a configure script.
##
## Boilerplate:  standard boilerplate code
##
AC_INIT([inap], [1.0.11], [issues@sigscale.org])
AC_COPYRIGHT([Copyright (c) 2025 SigScale Global Inc.])
AC_PREREQ(2.64)
#AC_CONFIG_SRCDIR([src/inap_app.erl])
AC_CONFIG_HEADERS([config.h])
AC_LANG([Erlang])
AM_INIT_AUTOMAKE([-Wno-portability])

##
## Options:  control options to configure, support code for the options
##
AC_ARG_WITH([tcap],
		[AS_HELP_STRING([--with-tcap=PATH], [specify location of tcap asn1 source])],
		[], [with_tcap=../../tcap/asn_src/ITU])
AC_ARG_ENABLE([debug],
		[AS_HELP_STRING([--disable-debug], [disable debugging (default is no)])])


##
## Programs:  check for programs needed by the configure process,
##            the build process, or by one of the programs being built
##
AC_ERLANG_NEED_ERL
AC_ERLANG_NEED_ERLC
if test -z "${ERLCFLAGS}" ; then
	ERLCFLAGS="-W -v"
fi
if test "x$disable_debug" != xyes ; then
	ERLCFLAGS="$ERLCFLAGS +debug_info"
fi
if test "x$with_tcap" != xno ; then
	ERLCFLAGS="$ERLCFLAGS -I $with_tcap"
fi
AC_ERLANG_SUBST_LIB_DIR
if test -z "${ERLANG_INSTALL_LIB_DIR}" ; then
	ERLANG_INSTALL_LIB_DIR=$ERLANG_LIB_DIR
fi
AC_ERLANG_SUBST_ROOT_DIR
AC_PROG_MKDIR_P
AC_PROG_INSTALL
AC_PROG_LN_S
AC_ERLANG_SUBST_INSTALL_LIB_DIR
otpdir=$ERLANG_INSTALL_LIB_DIR/..
appdir=$ERLANG_INSTALL_LIB_DIR/$PACKAGE_NAME-$PACKAGE_VERSION
docdir=$ERLANG_INSTALL_LIB_DIR/$PACKAGE_NAME-$PACKAGE_VERSION/doc
erldir=$ERLANG_INSTALL_LIB_DIR/$PACKAGE_NAME-$PACKAGE_VERSION/src
beamdir=$ERLANG_INSTALL_LIB_DIR/$PACKAGE_NAME-$PACKAGE_VERSION/ebin
asndir=$ERLANG_INSTALL_LIB_DIR/$PACKAGE_NAME-$PACKAGE_VERSION/asn_src
eincludedir=$ERLANG_INSTALL_LIB_DIR/$PACKAGE_NAME-$PACKAGE_VERSION/include
reldir=$ERLANG_INSTALL_LIB_DIR/../releases
AC_SUBST(appdir)
AC_SUBST(erldir)
AC_SUBST(beamdir)
AC_SUBST(asndir)
AC_SUBST(eincludedir)
AC_SUBST(reldir)


##
## Libraries:  check for libraries
##
AC_ERLANG_SUBST_ERTS_VER
AC_ERLANG_CHECK_LIB([kernel], [], [AC_MSG_ERROR([kernel was not found!])])
AC_ERLANG_CHECK_LIB([stdlib],
		[AS_VERSION_COMPARE([$ERLANG_LIB_VER_stdlib], ["3.5"],
				[AC_MSG_ERROR([>= stdlib-3.5 required!])])],
		[AC_MSG_ERROR([stdlib was not found!])])
AC_ERLANG_CHECK_LIB([sasl], [], [AC_MSG_ERROR([sasl was not found!])])
AM_CONDITIONAL([MAKE_TAR_EXTRA_FILES],
		[AS_VERSION_COMPARE([$ERLANG_LIB_VER_sasl], ["4.0"], [false], [true], [true])])
AC_ERLANG_CHECK_LIB([asn1], [], [AC_MSG_ERROR([asn1 was not found!])])
AC_ERLANG_CHECK_LIB([tcap], [], [AC_MSG_ERROR([tcap was not found!])])
AC_ERLANG_CHECK_LIB([map], [], [AC_MSG_ERROR([map was not found!])])


##
## Headers:  check for header files
##


##
## Typedefs & Structures:  check for typedefs, structures,
##                         and compiler characteristics.
##


##
## Functions:  check for library functions
##


##
## Output:  create output files
##

AC_OUTPUT([Makefile src/Makefile ebin/Makefile asn_src/Makefile doc/Makefile
		sys.config $PACKAGE_NAME.rel ebin/$PACKAGE_NAME.appup])

