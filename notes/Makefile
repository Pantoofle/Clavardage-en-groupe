SRC=$(wildcard *.pandoc)
PDF=$(SRC:%.pandoc=%.pdf)

all: $(PDF)
	
%.pdf: %.pandoc
	@echo Building $@
	pandoc $< -o $@

clean:
	rm -rf *.pdf
	
