AC_INIT(README)
AC_CANONICAL_SYSTEM
AM_INIT_AUTOMAKE(monoskel, 0.1)
AM_MAINTAINER_MODE

AC_PROG_INSTALL

dnl pkg-config
AC_PATH_PROG(PKG_CONFIG, pkg-config, no)
if test "x$PKG_CONFIG" = "xno"; then
	AC_MSG_ERROR([You need to install pkg-config])
fi

dnl C# compiler
AC_PATH_PROG(CSC, csc, no)
AC_PATH_PROG(MCS, mcs, no)
AC_PATH_PROG(MONO, mono, no)

CS="C#"
if test "x$CSC" = "xno" -a "x$MCS" = "xno"  ; then
	dnl AC_MSG_ERROR([You need to install a C# compiler])
	AC_MSG_ERROR([No $CS compiler found])
fi

if test "x$MCS" = "xno" ; then
	MCS=$CSC
fi

if test "x$MONO" = "xno"; then
	AC_MSG_ERROR([No mono runtime found])
fi

dnl gtk-sharp
#AJL - Disabled this until I work out why it fails
#GTKSHARP_REQUIRED_VERSION=1.0
#PKG_CHECK_MODULES(GTKSHARP, gtk-sharp >= $GTKSHARP_REQUIRED_VERSION)

AC_SUBST(MCS)

AC_OUTPUT([
Makefile
man/Makefile
src/Makefile
src/AssemblyInfo.cs
resources/Makefile
])