SHELL = /bin/sh
MANFILES = automx.conf.5.rst automx_ldap.5.rst automx_sql.5.rst automx_script.5.rst automx-test.1.rst
DOCFILES = BASIC_CONFIGURATION_README.rst INSTALL.rst
SOURCES = $(MANFILES) $(DOCFILES)
MANS= $(patsubst %.rst,%,$(MANFILES))
HTMLS= $(patsubst %.rst,%.html,$(SOURCES))
PDFS = $(patsubst %.rst,%.pdf,$(SOURCES))
TXTS = $(patsubst %.rst,%.txt,$(SOURCES))

all:	html txt man pdf

man:	$(MANS)

pdf:	$(PDFS)

txt:	$(TXTS)

html:	$(HTMLS)

%.html:	%.rst
	rst2html $< $@

%.txt:	%.html
	w3m -cols 80 -dump $< > $@

%:	%.rst
	rst2man $< $@

%.pdf:	%.rst
	rst2pdf $< -o $@

install:
	cp -p *.5 ../../doc/man/man5/
	cp -p *.1 ../../doc/man/man1/
	cp -p *.html ../../doc/html/
	cp -p automx*.txt ../../doc/txt/
	cp -p INSTALL.txt ../../INSTALL
	cp -p BASIC_CONFIGURATION_README.txt ../../BASIC_CONFIGURATION_README

.PHONY:	clean

clean:	
	rm -f *.html *.txt *.pdf *.5 *.1 BASIC_CONFIGURATION_README INSTALL
