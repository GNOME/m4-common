aclocaldir = $(prefix)/share/aclocal

# sorted, please
dist_aclocal_DATA = \
	autoconf-archive/m4/ax_append_compile_flags.m4			\
	autoconf-archive/m4/ax_append_flag.m4				\
	autoconf-archive/m4/ax_check_compile_flag.m4			\
	autoconf-archive/m4/ax_is_release.m4				\
	autoconf-archive/m4/ax_code_coverage.m4				\
	autoconf-archive/m4/ax_compiler_flags.m4			\
	autoconf-archive/m4/ax_compiler_flags_cflags.m4			\
	autoconf-archive/m4/ax_compiler_flags_cxxflags.m4		\
	autoconf-archive/m4/ax_compiler_flags_ldflags.m4		\
	autoconf-archive/m4/ax_compiler_flags_gir.m4			\
	autoconf-archive/m4/ax_cxx_compile_stdcxx_11.m4			\
	autoconf-archive/m4/ax_pkg_check_modules.m4			\
	autoconf-archive/m4/ax_require_defined.m4			\
	$(NULL)

all-local: $(dist_aclocal_DATA)
	cat $^ | grep -v '^#' | grep -v 'AX_PACKAGE_REQUIRES' | sed -e 's/\<dnl\>.*//' | grep -o '\<AX_[A-Z0-9_]*[A-Z0-9]\>' | sort | uniq > used
	cat $^ | grep ^AC_DEFUN | grep -o '\<AX_[A-Z0-9_]*\>' | sort | uniq > defined
	diff -u used defined
	rm -f used defined

dist-hook:
	@echo
	@echo
	@echo "       Don't dist this package.  See README."
	@echo
	@echo
	@false
