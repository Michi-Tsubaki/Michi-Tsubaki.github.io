# Makefile for compiling Michitoshi Tsubaki's CV
# Usage: make [target]

# Variables
TEX_FILE = tsubaki_cv.tex
PDF_FILE = tsubaki_cv.pdf
LATEX_ENGINE = pdflatex
BIBTEX = bibtex

# Default target
.PHONY: all
all: $(PDF_FILE)

# Compile PDF from LaTeX source
$(PDF_FILE): $(TEX_FILE)
	$(LATEX_ENGINE) -interaction=nonstopmode $(TEX_FILE)
	$(LATEX_ENGINE) -interaction=nonstopmode $(TEX_FILE)  # Run twice for proper cross-references

# Alternative target using pdflatex (if XeTeX is not available)
.PHONY: pdflatex
pdflatex:
	pdflatex $(TEX_FILE)
	pdflatex $(TEX_FILE)

# Clean auxiliary files
.PHONY: clean
clean:
	rm -f *.aux *.log *.out *.toc *.fdb_latexmk *.fls *.synctex.gz

# Clean all generated files including PDF
.PHONY: cleanall
cleanall: clean
	rm -f $(PDF_FILE)

# View the PDF (Linux/macOS)
.PHONY: view
view: $(PDF_FILE)
	@if command -v evince >/dev/null 2>&1; then \
		evince $(PDF_FILE) & \
	elif command -v open >/dev/null 2>&1; then \
		open $(PDF_FILE); \
	elif command -v xdg-open >/dev/null 2>&1; then \
		xdg-open $(PDF_FILE) & \
	else \
		echo "No suitable PDF viewer found"; \
	fi

# Quick build and view
.PHONY: preview
preview: all view

# Help target
.PHONY: help
help:
	@echo "Available targets:"
	@echo "  all      - Compile CV to PDF (default)"
	@echo "  pdflatex - Compile using pdflatex instead of xelatex"
	@echo "  clean    - Remove auxiliary files"
	@echo "  cleanall - Remove all generated files including PDF"
	@echo "  view     - Open the PDF in default viewer"
	@echo "  preview  - Compile and view PDF"
	@echo "  help     - Show this help message"
	@echo ""
	@echo "Dependencies:"
	@echo "  - XeTeX (recommended) or pdfLaTeX"
	@echo "  - Required LaTeX packages: geometry, enumitem, titlesec, graphicx, array, tabularx, xcolor, fontspec, hyperref"