
INKSCAPE=inkscape

all-ads.pdf : genesis-does-1.pdf customer.pdf Makefile
	gs -o genesis-does-left.pdf \
	   -sDEVICE=pdfwrite \
	   -c "[/CropBox [0 0 612 792]" \
	   -c " /PAGES pdfmark" \
	   -f genesis-does-1.pdf
	gs -o genesis-does-right.pdf \
	   -sDEVICE=pdfwrite \
	   -c "[/CropBox [612 0 1224 792]" \
	   -c " /PAGES pdfmark" \
	   -f genesis-does-1.pdf
	pdfunite \
		customer.pdf \
		genesis-does-left.pdf \
		genesis-does-right.pdf \
		all-ads.pdf



%.pdf : %.svg
	$(INKSCAPE) --batch-process --export-type=pdf --export-area-page --export-background=white --export-background-opacity=1.0 --export-pdf-version=1.4 --export-text-to-path --export-filename='$@' '$<'

genesis-does-1.svg : hardware.png
