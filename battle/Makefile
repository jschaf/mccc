INPUT = hammelburg
BUILDDIR = build
all: builddir update-bib
	pandoc				\
	  --filter pandoc-citeproc	\
	  --csl=turabian.csl		\
	  --standalone			\
	  --smart                       \
	  -t native                     \
	  --filter smallcaps.py    	\
	  $(INPUT).md		\
	|				\
	pandoc				\
	  -f native                     \
	  --latex-engine=lualatex	\
	  --template=template.tex	\
          --variable fontsize=12pt      \
          --variable linkcolor=black    \
          --variable urlcolor=black     \
          --variable citecolor=black    \
	  --no-tex-ligatures            \
	  --smart                       \
	  -o $(BUILDDIR)/$(INPUT).tex

	rubber --into build --warn all --pdf $(BUILDDIR)/$(INPUT).tex

docx:
	pandoc				\
	  --filter pandoc-citeproc	\
	  --csl=turabian.csl		\
	  --standalone			\
	  --smart                       \
	  --filter smallcaps.py    	\
	  $(INPUT).md			\
          -o instability.docx

builddir:
	mkdir -p build

update-bib:
	curl --silent --show-error http://localhost:23119/better-bibtex/collection?/0/SNIW7H7Q.biblatex > battle.bib
