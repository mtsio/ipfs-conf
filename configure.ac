AC_INIT([libipfs_api], [0.1], [https://github.com/marshalljp/ipfs/issues])
AM_INIT_AUTOMAKE([foreign -Wall -Werror subdir-objects])

GCC_MAJOR=4
GCC_MINOR=8
CLANG_MAJOR=3
CLANG_MINOR=4

AC_LANG([C++])
AC_PROG_CXX([g++ clang])
dnl add CXX and CXXCPP if needed for C++11
AX_CXX_COMPILE_STDCXX_11
AC_PROG_GREP

AC_SUBST(GCC_MAJOR_VERSION)
AC_SUBST(GCC_MINOR_VERSION)
AC_SUBST(CLANG_MAJOR_VERSION)
AC_SUBST(CLANG_MINOR_VERSION)

dnl if the compiler is not supported print error and abort
gxx_version=`$CXX -v 2>&1 | $GREP "^.*g.. version" | \
    sed -e 's/^.*g.. version *//' -e 's/cygnus-//' -e 's/egcs-//' -e 's/ .*//'`
if test "x$ac_ct_CXX" = "xg++"; then
   AS_VERSION_COMPARE([$GCC_MAJOR.$GCC_MINOR], [$gxx_version], [], [],
    AC_MSG_ERROR([old g++]))
fi

dnl check if curl is installed
AC_CHECK_LIB([curl], [curl_easy_init], [], [AC_MSG_ERROR([curl is missing])])
dnl check for the json library
AC_CHECK_HEADER([json.hpp], [],
	[AC_MSG_ERROR([json lib missing, if not in standard path specify it])])
AC_PROG_RANLIB([libipfs-api.a])


AM_PROG_AR
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_FILES([Makefile src/Makefile src/http/Makefile])
AC_OUTPUT

