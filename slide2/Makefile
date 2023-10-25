## コンパイルする TeX ファイルの名前（拡張子は除く）
FILE=slide

LATEX=latexmk -pvc
DVIPDFM=dvipdfmx

.PHONY: all clean

all: $(FILE).tex
	$(LATEX) $(FILE).tex

## make clean で LaTeX が出力する中間ファイルを削除（pdf は削除しない）
clean:
	rm -rf *.acn *.acr *.alg *.aux *.bbl *.blg *.dvi *.fdb_latexmk *.glg *.glo *.gls *.idx *.ilg *.ind *.ist *.lof *.log *.lot *.maf *.mtc *.mtc0 *.nav *.nlo *.out *.pdfsync *.ps *.snm *.synctex.gz *.toc *.vrb *.xdy *.tdo *.fls
