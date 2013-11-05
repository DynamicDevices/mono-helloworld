SUBDIRS = man resources src
bin_SCRIPTS = helloworld helloworldform
EXTRA_DIST = script.in

REWRITE = \
        sed -e "s|\@prefix\@|$(prefix)|g"               \
            -e "s|\@pkglibdir\@|$(pkglibdir)|g"         \
            -e "s|\@bindir\@|$(bindir)|g"		\
	    -e "s|\@MONO\@|/usr/bin/mono|g"                   \
	    -e "s|\@APP\@|$@|g"                   

$(bin_SCRIPTS): $(srcdir)/script.in Makefile
	$(REWRITE) $(srcdir)/script.in > $@.tmp
	mv $@.tmp $@


