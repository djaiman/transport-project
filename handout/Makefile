FILE := transport-handout

TEX	 := $(wildcard *.tex)

all:	$(FILE).pdf 

transport-handout.pdf: $(TEX) 
	pdflatex $(FILE)
#	bibtex $(FILE)
	pdflatex $(FILE)
	pdflatex $(FILE)


clean:
	rm -f *.aux *.blg *.log *.bbl *.out *.syntex.gz $(FILE).pdf

spell:
	@for i in $(TEX); do aspell --mode=tex -p ./aspell.words -c $$i; done
	@for i in $(TEX); do perl bin/double.pl $$i; done
	@for i in $(TEX); do perl bin/abbrv.pl  $$i; done
	@# bash bin/weasel.sh  $(TEX)
	@# bash bin/passive.sh $(TEX)
	@bash bin/hyphens.sh $(TEX)
	@( head -1 aspell.words ; tail -n +2 aspell.words | sort ) > aspell.words~
	@mv aspell.words~ aspell.words

%-bw.pdf: %.pdf
	( ./bin/pdftobw $< $@ && cp $@ .missing/$@ ) || cp .missing/$@ $@

