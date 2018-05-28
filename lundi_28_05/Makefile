FILES=slides

TEX_SRC=$(addsuffix .tex, $(FILES))
PDF_RES=$(addsuffix .pdf, $(FILES))
BIB_SRC=$(addsuffix .bib, $(FILES))

IMG_SRC=$(shell find img/ -iname "*.dot")
IMG_CODE=$(IMG_SRC:.dot=.tex)
TIKZ_SRC=$(shell find img/ -iname "*.tex")

.PHONY: all clean

all: $(PDF_RES)

%.pdf: %.tex %.blg $(IMG_CODE)
	pdflatex $(basename $<).tex

%.blg: %.bib
	pdflatex $(basename $<).tex
	bibtex $(basename $<)
	pdflatex $(basename $<).tex
	pdflatex $(basename $<).tex

%.tex: %.dot
	dot2tex --figonly -ftikz $< > $@

clean:
	rm -rf *.aux \
  			 *.log \
  			 *.nav \
  			 *.out \
  			 *.snm \
  			 *.toc \
  			 *.bbl \
  			 *.blg \
  			 img/*.tex

proper: clean
	rm -rf *.pdf
