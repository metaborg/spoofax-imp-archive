SYNTAX     = PHP5
EXTENSIONS = php,php5
PACKAGE    = org.strategoxt.imp.editors.php
SOURCE     = $(SYNTAX).def # get this somewhere
START      = Document

SDF2IMP = ../org.strategoxt.imp.metatooling/sdf2imp
ESVS       = ${wildcard *.esv}

all : eclipse-deps

clean :
	rm -f src/parser/$(SYNTAX)ParseController.java
	rm -rf src/parser/ast
	# ...

eclipse-deps : plugin.xml # and others

plugin.xml : $(SYNTAX).def $(SYNTAX).tbl $(SDF2IMP) Makefile $(ESVS)
	$(SDF2IMP) -i $< -p $(SYNTAX).tbl -e $(EXTENSIONS) -m $(SYNTAX) -s $(START) -n $(PACKAGE) -r --verbose 2

$(SYNTAX).tbl : $(SYNTAX).def
	sdf2table -i $< -o $@ -m $(SYNTAX)

