## Makefile.am
##
## Process this file with automake to produce Makefile.in

ASNCFLAGS = $(ERLCFLAGS) \
		-I ${ERLANG_LIB_DIR_tcap}/asn_src \
		-I ${ERLANG_LIB_DIR_map}/asn_src \
		+ber +noobj

noinst_DATA = CS2-SSF-SCF-pkgs-contracts-acs.erl \
		CS2-SCF-SRF-pkgs-contracts-acs.erl \
		CS2-SSF-SCF-ops-args.erl \
		CS2-SCF-SRF-ops-args.erl \
		CS2-object-identifiers.erl \
		CS2-operationcodes.erl \
		CS2-errorcodes.erl \
		CS2-datatypes.erl \
		CS2-errortypes.erl

einclude_DATA = CS2-object-identifiers.hrl \
		CS2-operationcodes.hrl \
		CS2-errorcodes.hrl

CS2-object-identifiers.erl CS2-object-identifiers.hrl:$(top_srcdir)/asn_src/CS2-object-identifiers.asn1
	$(ERLC) $(ASNCFLAGS) $<

CS2-operationcodes.erl CS2-operationcodes.hrl:$(top_srcdir)/asn_src/CS2-operationcodes.asn1
	$(ERLC) $(ASNCFLAGS) $<

CS2-errorcodes.erl CS2-errorcodes.hrl:$(top_srcdir)/asn_src/CS2-errorcodes.asn1
	$(ERLC) $(ASNCFLAGS) $<

%.erl:$(top_srcdir)/asn_src/%.asn1
	$(ERLC) $(ASNCFLAGS) +maps $<

CLEANFILES = $(noinst_DATA) \
		$(einclude_DATA) \
		*.asn1db

