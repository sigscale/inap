## Makefile.am
##
## Process this file with automake to produce Makefile.in

appdir = $(beamdir)
app_DATA = inap.app
EXTRA_DIST = inap.app

beam_DATA = inap_codec.beam

inap_codec.beam:	$(top_builddir)/src/inap_codec.erl
	$(ERLC) $(ERLCFLAGS) $<

%.beam:	$(top_srcdir)/src/%.erl
	$(ERLC) $(ERLCFLAGS) -I $(top_builddir)/src $<

%.app:   %.app-in
	sed -e 's/%APP_NAME%/$(PACKAGE_NAME)/' \
			-e 's/%APP_VERSION%/$(PACKAGE_VERSION)/' < $< > $@ 

CLEANFILES = $(beam_DATA) $(app_DATA)

