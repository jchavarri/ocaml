TOPDIR = ../../..
include $(TOPDIR)/Makefile.tools

LD_PATH = "$(TOPDIR)/otherlibs/str:$(TOPDIR)/otherlibs/unix"

TOOLS = ../../tools
CAMLLATEX = $(SET_LD_PATH) \
  $(OCAMLRUN) $(TOOLS)/caml-tex2 \
  -caml "TERM=norepeat $(OCAML)" -n 80 -v false
TEXQUOTE = $(TOOLS)/texquote2
TRANSF = $(SET_LD_PATH) $(OCAMLRUN) $(TOOLS)/transf


FILES = coreexamples.tex lablexamples.tex objectexamples.tex \
  moduleexamples.tex advexamples.tex polymorphism.tex


etex-files: $(FILES)
all: $(FILES)


%.gen.tex: %.etex
	$(CAMLLATEX) $< -o $@

%.tex: %.gen.tex
	$(TEXQUOTE) < $< > $*.texquote_error.tex
	mv $*.texquote_error.tex $@


.PHONY: clean
clean:
	rm -f *.tex
