
########################
## CONFIG FILE FOR AC ##
########################

# M4 PREABLE

# uLib version:
m4_define([ltk_major_version], [0])
m4_define([ltk_minor_version], [1])
# if the minor version number is odd, then we want debugging.  Otherwise
# we only want minimal debugging support.
##m4_define([ltk_debug_default],
##	  [m4_if(m4_eval(IB_minor_version % 2), [1], [yes])])


########### INIT #######################################
AC_INIT([ltk],[uLib_major_version.uLib_minor_version],[andrea.rigoni@igi.cnr.it]) 
AM_INIT_AUTOMAKE([subdir-objects])

##AC_PREREQ([2.67])
AC_CONFIG_MACRO_DIR([m4])


AC_CONFIG_SRCDIR([src/ltk.h])
AC_CONFIG_HEADERS([config.h])

# Checks for programs.
AC_PROG_CC
AC_PROG_CXX


######### LIBTOOL ########################################
AC_PROG_LIBTOOL
LIBADD_DL="-ldl"
AC_SUBST(LIBADD_DL)

AC_SEARCH_LIBS([strerror],[cposix])

LT_INIT()
AC_SUBST([LIBTOOL_DEPS])



######### CHECKS ########################################
# Checks for header files.
AC_CHECK_HEADERS([stdlib.h string.h assert.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_HEADER_STDBOOL
AC_C_INLINE
AC_TYPE_SIZE_T

# Checks for library functions.
AC_FUNC_MALLOC
AC_CHECK_FUNCS([fesetround floor pow sqrt strdup strstr])
AC_SEARCH_LIBS([strerror],[cposix])

########## CONDITIONALS ##################################


# Configure script arguments
dnl declare --enable-* args and collect ac_help strings
AC_ARG_ENABLE(debug,
		AS_HELP_STRING([--enable-debug=no/yes],[turn on debugging, default: no]),
[case "${enableval}" in
             yes) debug=true ;;
             no)  debug=false ;;
             *)   AC_MSG_ERROR([bad value ${enableval} for --enable-debug]) ;;
esac],
		[debug=false])

AC_ARG_ENABLE(parallel,
		AS_HELP_STRING([--enable-parallel=no/yes],[turn on openMP parallel processing, default: yes]),
[case "${enableval}" in
             yes) parallel=true ;;
             no)  parallel=false ;;
             *)   AC_MSG_ERROR([bad value ${enableval} for --enable-parallel]) ;;
esac],
		[parallel=true])

AC_ARG_ENABLE(autovector,
                AS_HELP_STRING([--enable-autovector=no/yes],[turn on gcc auto vectorize loops with simd instructions, default: no]),
[case "${enableval}" in
             yes) autovector=true ;;
             no)  autovector=false ;;
             *)   AC_MSG_ERROR([bad value ${enableval} for --enable-autovector]) ;;
esac],
                [autovector=false])

AM_CONDITIONAL(DEBUG, test x"$debug" = x"true")
AM_CONDITIONAL(PARAL_MP, test x"$parallel" = x"true")
AM_CONDITIONAL(SIMD_AUTOVECTOR, test x"$autovector" = x"true")


######### MAKEFILES #########################################

AC_CONFIG_FILES([
	Makefile
	src/Makefile
	])
AC_OUTPUT

