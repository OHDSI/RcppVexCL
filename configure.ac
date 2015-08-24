# Process this file with autoconf to produce a configure script.
AC_INIT(RcppVexCL, 0.1, msuchard@ucla.edu)

# find R home and set CC/CFLAGS
: ${R_HOME=`R RHOME`}
if test -z "${R_HOME}"; then
  echo "could not determine R_HOME"
  exit 1
fi

# platform check
RHOST=`"${R_HOME}/bin/Rscript" -e 'cat(Sys.info()[["sysname"]])'`

# Check for which host we are on and setup a few things
# specifically based on the host
case $RHOST in
  Darwin* )
        # Do something specific for mac
        OPENCL_LIB="-framework OpenCL"
        VEXCL_FLAGS=""
        ;;
  Linux*)
        # Do something specific for linux
        OPENCL_LIB="-lOpenCL"
        VEXCL_FLAGS="-Wno-unused-local-typedefs"
        ;;
   *BSD*)
        # Do something specific for BSD
        AC_MSG_ERROR([BSD is not currently supported])
        ;;
    *)
        #Default Case
        AC_MSG_ERROR([Your platform is not currently supported])
        ;;
esac

AC_SUBST(OPENCL_LIB)
AC_SUBST(VEXCL_FLAGS)

AC_CONFIG_FILES([src/Makevars])
AC_OUTPUT
