

all:
	pandoc				\
	  --filter pandoc-citeproc	\
	  --csl=turabian.csl		\
	  --standalone			\
	  --smart                       \
	  -t native                     \
	  --filter smallcaps.py    	\
	  somalia-stability.md		\
	|				\
	pandoc				\
	  -f native                     \
	  --latex-engine=lualatex	\
	  --template=template.tex	\
          --variable fontsize=12pt      \
	  --no-tex-ligatures            \
	  --smart                       \
	  -o ss.tex

	lualatex ss.tex

markdown:
	pandoc --filter pandoc-citeproc \
	--csl=turabian.csl \
	--standalone \
	--filter ./smallcaps.py \
	-o ss2.md \
	somalia-stability.md



tex:

	pandoc --filter pandoc-citeproc \
	--csl=turabian.csl \
	--standalone \
	--template=template.tex \
	--filter ./smallcaps.py \
	--from=markdown+yaml_metadata_block \
	-o somalia-stability.tex \
	somalia-stability.md
