DOCUMENT = tracemodel
TEXFILES = $(wildcard *.tex)

# LaTeX/BiBTeX re-run conditions
RERUN = "Rerun to get (cross-references|the bars|citations)"
RERUNBIB = "No file.*\.bbl|Citation.*undefined"

LATEX = pdflatex
BIBTEX = bibtex
DEL = @rm -f

all:
	@$(LATEX) $(DOCUMENT).tex
	@grep -E $(RERUNBIB) $(DOCUMENT).log && ($(BIBTEX) $(DOCUMENT);$(LATEX) $(DOCUMENT).tex); true
	@grep -E $(RERUN) $(DOCUMENT).log && ($(LATEX) $(DOCUMENT).tex) ; true
	@grep -E $(RERUN) $(DOCUMENT).log && ($(LATEX) $(DOCUMENT).tex) ; true

bib:
	$(BIBTEX) $(DOCUMENT)

clean:
	$(DEL) $(TEXFILES:tex=aux)
	$(DEL) texput.log
	$(DEL) $(DOCUMENT).dvi $(DOCUMENT).idx $(DOCUMENT).log $(DOCUMENT).pdf
	$(DEL) $(DOCUMENT).ilg $(DOCUMENT).ind $(DOCUMENT).toc $(DOCUMENT).lox
	$(DEL) $(DOCUMENT).bbl $(DOCUMENT).blg $(DOCUMENT).out $(DOCUMENT).synctex.gz
	$(DEL) *~ # emacs temporary files