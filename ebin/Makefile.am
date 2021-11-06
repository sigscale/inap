## Makefile.am
##
## Process this file with automake to produce Makefile.in

appdir = $(beamdir)
app_DATA = inap.app
EXTRA_DIST = inap.app

beam_DATA = CS2-SSF-SCF-pkgs-contracts-acs.beam \
		CS2-SCF-SRF-pkgs-contracts-acs.beam \
		CS2-SSF-SCF-ops-args.beam \
		CS2-SCF-SRF-ops-args.beam \
		CS2-object-identifiers.beam \
		CS2-operationcodes.beam \
		CS2-errorcodes.beam \
		CS2-datatypes.beam \
		CS2-errortypes.beam

%.beam:$(top_builddir)/src/%.erl
	$(ERLC) $(ERLCFLAGS) -I $(top_builddir)/src $<

%.app:   %.app-in
	sed -e 's/%APP_NAME%/$(PACKAGE_NAME)/' \
			-e 's/%APP_VERSION%/$(PACKAGE_VERSION)/' < $< > $@ 

CLEANFILES = $(beam_DATA) $(app_DATA)

