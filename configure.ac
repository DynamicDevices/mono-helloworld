AC_INIT(helloworld,0.1)
AC_CONFIG_SRCDIR(README)
AM_INIT_AUTOMAKE

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

AC_ARG_ENABLE([winformdemo],
[  --enable-winformdemo    Build winform demo],
[case "${enableval}" in
  yes) winformdemo=true ;;
  no)  winformdemo=false ;;
  *) AC_MSG_ERROR([bad value ${enableval} for --enable-winformdemo]) ;;
esac],[winformdemo=false])
AM_CONDITIONAL([BUILD_WINFORMDEMO], [test x$winformdemo = xtrue])

AC_ARG_ENABLE([gtkdemo],
[  --enable-gtkdemo    Build gtkdemo],
[case "${enableval}" in
  yes) gtkdemo=true ;;
  no)  gtkdemo=false ;;
  *) AC_MSG_ERROR([bad value ${enableval} for --enable-gtkdemo]) ;;
esac],[gtkdemo=false])
AM_CONDITIONAL([BUILD_GTKDEMO], [test x$gtkdemo = xtrue])

AC_SUBST(GTKSHARP_LIBS)

AC_SUBST(MCS)

AC_OUTPUT([
Makefile
man/Makefile
src/Makefile
src/AssemblyInfo.cs
resources/Makefile
])
