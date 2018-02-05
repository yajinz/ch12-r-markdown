SOURCES = $(wildcard *.rmd)
PDF = $(patsubst %.rmd, %.pdf, $(SOURCES))
HTML = $(patsubst %.rmd,%.html, $(SOURCES))
TEX = $(patsubst %.rmd, %.tex, $(SOURCES))
# tex versions of the files, just to clean up
$(info [${HTML}])

%.md: %.rmd
	Rscript -e "knitr::knit('$<', quiet=TRUE)"

%.pdf: %.md
	Rscript -e "rmarkdown::render('$<', output_format=\"all\")"

%.html: %.rmd
	Rscript -e "rmarkdown::render('$<', output_format=\"all\")"

all: $(HTML)

pdf: $(PDF)

clean:
	rm -vf $(TEX) *.rmd~
# -v : verbose
# -f: ignore non-existent files

db:
	rsync -avulP $(SLIDES) $(HOME)/Dropbox/Ott-Tiina/info201/
