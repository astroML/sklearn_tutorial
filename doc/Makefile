# Makefile for Sphinx documentation
#

# You can set these variables from the command line.
SPHINXOPTS    =
SPHINXBUILD   = sphinx-build
PAPER         =
BUILDDIR      = _build

# Internal variables.
PAPEROPT_a4     = -D latex_paper_size=a4
PAPEROPT_letter = -D latex_paper_size=letter
ALLSPHINXOPTS   = -d $(BUILDDIR)/doctrees $(PAPEROPT_$(PAPER)) $(SPHINXOPTS) .

.PHONY: help clean html dirhtml pickle json htmlhelp qthelp latex latexpdf chan

all: html-noplot

help:
	@echo "Please use \`make <target>' where <target> is one of"
	@echo "  html      to make standalone HTML files"
	@echo "  dirhtml   to make HTML files named index.html in directories"
	@echo "  pickle    to make pickle files"
	@echo "  json      to make JSON files"
	@echo "  htmlhelp  to make HTML files and a HTML help project"
	@echo "  qthelp    to make HTML files and a qthelp project"
	@echo "  latex     to make LaTeX files, you can set PAPER=a4 or PAPER=letter"
	@echo "  latexpdf   to make LaTeX files and run them through pdflatex"
	@echo "  changes   to make an overview of all changed/added/deprecated items"
	@echo "  linkcheck to check all external links for integrity"
	@echo "  doctest   to run all doctests embedded in the documentation (if enabled)"

clean:
	-rm -rf $(BUILDDIR)/*
	-rm -rf auto_examples/
	-rm -rf doc/generated/*
	-rm -rf modules/generated/*

html:
	$(SPHINXBUILD) -b html $(ALLSPHINXOPTS) $(BUILDDIR)/html
	touch $(BUILDDIR)/html .nojekyll
	@echo
	@echo "Build finished. The HTML pages are in $(BUILDDIR)/html."

html-noplot:
	$(SPHINXBUILD) -D plot_gallery=False -b html $(ALLSPHINXOPTS) $(BUILDDIR)/html
	touch $(BUILDDIR)/html .nojekyll
	@echo
	@echo "Build finished. The HTML pages are in $(BUILDDIR)/html."

dirhtml:
	$(SPHINXBUILD) -b dirhtml $(ALLSPHINXOPTS) $(BUILDDIR)/dirhtml
	touch $(BUILDDIR)/dirhtml .nojekyll
	@echo
	@echo "Build finished. The HTML pages are in $(BUILDDIR)/dirhtml."

pickle:
	$(SPHINXBUILD) -b pickle $(ALLSPHINXOPTS) $(BUILDDIR)/pickle
	@echo
	@echo "Build finished; now you can process the pickle files."

json:
	$(SPHINXBUILD) -b json $(ALLSPHINXOPTS) $(BUILDDIR)/json
	@echo
	@echo "Build finished; now you can process the JSON files."

htmlhelp:
	$(SPHINXBUILD) -b htmlhelp $(ALLSPHINXOPTS) $(BUILDDIR)/htmlhelp
	@echo
	@echo "Build finished; now you can run HTML Help Workshop with the" \
	      ".hhp project file in $(BUILDDIR)/htmlhelp."

latex:
	$(SPHINXBUILD) -b latex $(ALLSPHINXOPTS) $(BUILDDIR)/latex
	@echo
	@echo "Build finished; the LaTeX files are in $(BUILDDIR)/latex."
	@echo "Run \`make' in that directory to run these through (pdf)latex" \
	      "(use \`make latexpdf' here to do that automatically)."

latexpdf:
	$(SPHINXBUILD) -b latex $(ALLSPHINXOPTS) $(BUILDDIR)/latex
	@echo "Running LaTeX files through pdflatex..."
	make -C $(BUILDDIR)/latex all-pdf
	@echo "pdflatex finished; the PDF files are in $(BUILDDIR)/latex."

changes:
	$(SPHINXBUILD) -b changes $(ALLSPHINXOPTS) $(BUILDDIR)/changes
	@echo
	@echo "The overview file is in $(BUILDDIR)/changes."

linkcheck:
	$(SPHINXBUILD) -b linkcheck $(ALLSPHINXOPTS) $(BUILDDIR)/linkcheck
	@echo
	@echo "Link check complete; look for any errors in the above output " \
	      "or in $(BUILDDIR)/linkcheck/output.txt."

doctest:
	$(SPHINXBUILD) -b doctest $(ALLSPHINXOPTS) $(BUILDDIR)/doctest
	@echo "Testing of doctests in the sources finished, look at the " \
	      "results in $(BUILDDIR)/doctest/output.txt."

#zip: html pdf
#	mkdir -p _build/nisl ;
#	cp -r _build/html _build/nisl ;
#	cp -r data _build/nisl ;
#	cp nisl.pdf _build/nisl;
#	zip -r _build/nisl.zip _build/nisl

download-data:
	cd data/sdss_colors && python fetch_data.py
	cd data/sdss_colors && python fetch_data.py
	cd data/sdss_colors && python fetch_data.py

pdf: latexpdf
	cp $(BUILDDIR)/latex/AstroSklearn.pdf ./

nbconvert:
	cd notebooks && rm -f *.v2.ipynb && python nbconvert.py *.ipynb

tar: nbconvert
	tar -czvf exercises.tgz notebooks/soln/*.py notebooks/*.ipynb data/*/*.py skeletons solutions

tar-data: nbconvert download-data
	tar -czvf exercises_data.tgz notebooks/soln/*.py notebooks/*.ipynb data skeletons solutions

install-reclone: tar html #pdf
	rm -rf _build/sklearn_tutorial
	cd _build/ && \
        git clone git@github.com:astroML/sklearn_tutorial && \
	cd sklearn_tutorial && git checkout gh-pages && \
	rsync -r ../html/* . && \
	git add * && \
	git commit -a -m 'Make install' && \
	git push origin gh-pages

install: tar html #pdf
	if test -d _build/sklearn_tutorial; \
	then echo "using existing sklearn_tutorial directory"; \
	else cd _build && \
	git clone git@github.com:astroML/sklearn_tutorial; \
	fi && \
	cd _build/sklearn_tutorial && git checkout gh-pages && \
	rsync -r ../html/* ./ && \
	git add * && \
	git commit -a -m 'Make install' && \
	git push origin gh-pages
