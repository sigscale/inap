## Makefile.am
##
## Process this file with automake to produce Makefile.in

noinst_DATA =	inap_codec.erl
einclude_DATA = inap_codec.hrl

inap_codec.hrl: inap_codec.erl

inap_codec.erl:	$(top_srcdir)/asn_src/inap_codec.set.asn1
	$(ERLC) $(ERLCFLAGS) +noobj $<

CLEANFILES = $(noinst_DATA) inap_codec.asn1db inap_codec.hrl

