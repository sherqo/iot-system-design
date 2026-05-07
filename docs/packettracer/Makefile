MAIN ?= main
BUILDDIR = .build
OUTDIR = output
OUT ?= $(MAIN)
DATE := $(shell date +%Y-%m-%d)

all: $(BUILDDIR) $(OUTDIR)
	@rm -f main.aux main.log main.out main.toc main.fls main.fdb_latexmk main.synctex.gz main.pdf
	@cp -r ../imgs-cpt $(BUILDDIR)/imgs
	@cp ../imgs/0-uni-logo.png $(BUILDDIR)/
	@cd $(BUILDDIR) && pdflatex -interaction=nonstopmode ../$(MAIN).tex || true
	@cd $(BUILDDIR) && pdflatex -interaction=nonstopmode ../$(MAIN).tex || true
	@cp $(BUILDDIR)/$(MAIN).pdf $(OUTDIR)/$(OUT)_$(DATE).pdf
	@rm -f main.aux main.log main.out main.toc main.fls main.fdb_latexmk main.synctex.gz main.pdf

dated: all
	@ls -t $(OUTDIR)/$(MAIN)_*.pdf | head -1

$(BUILDDIR):
	mkdir -p $(BUILDDIR)

$(OUTDIR):
	mkdir -p $(OUTDIR)

clean:
	rm -rf $(BUILDDIR)

cleanall: clean
	rm -rf $(OUTDIR)

format:
	latexindent -w -s main.tex
	rm -f *.bak* indent.log

.PHONY: all clean cleanall format
