BUILD_DIR = _build
SRC_DIR = src

WEB_BUILD = $(BUILD_DIR)/web
LATEX_BUILD = $(BUILD_DIR)/latex
EPUB_BUILD = $(BUILD_DIR)/epub

ARGS = $(shell ls -1 $(SRC_DIR) | sed -e "s/^/$(SRC_DIR)\//")

all:
	# Make options: latex, web, epub, clean

latex:
	mkdir -p $(LATEX_BUILD)
	pandoc -sS --toc --variable=fontsize:12pt --template=templates/latex.tex -o $(LATEX_BUILD)/index.tex templates/title.txt \
		$(ARGS)
	xelatex $(LATEX_BUILD)/index.tex

web:
	mkdir -p $(WEB_BUILD)
	pandoc -sS --toc --css=style.css -o $(WEB_BUILD)/index.html --chapters templates/title.txt \
		$(ARGS)
	cp templates/style.css $(WEB_BUILD)/style.css

epub:
	mkdir -p $(EPUB_BUILD)
	pandoc -sS -o $(EPUB_BUILD)/index.epub --chapters templates/title.txt \
		$(ARGS)

clean:
	rm -rf $(BUILD_DIR)
	rm *.log *.aux *.toc *.pdf
