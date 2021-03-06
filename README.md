# Requirements

In order to build the PDF, you will need to install

- [pandoc](https://pandoc.org/installing.html)
- The pandoc filter [pandoc-crossref](https://github.com/lierdakil/pandoc-crossref) 
- A TeX distribution such as [TeX Live](https://www.tug.org/texlive/)
    (`pdflatex` is used to convert tex to PDF)
- The [biber](https://ctan.org/pkg/biber?lang=en) package

# What's what?

I hacked this template together for [my ICASSP 2018 paper](http://epubs.surrey.ac.uk/845998/), so I am using the
content of that work as an example (see [this repo](https://github.com/CVSSP/perceptual-study-source-separation) if you are interested).

- `paper.md`: The paper content, written in Markdown
- `metadata.yaml`: Authors, abstract, and some configuration settings
- `icassp_template.latex`: The latex template used by pandoc to generate the tex
    file
- `refs.bib`: bibtex formatted references
- `images`: Directory with three images corresponding to Figures 1-3 in the
    paper

# Building

You can either replace `refs.bib` with your own bibtex file, or specify the path
to your own file for the value of `bibliography` in `metadata.yaml` (in which
case ignore `refs.bib`).

Then enter `make`, which calls pandoc to run `paper.md` and `metadata.yaml`
through the latex template `icassp_template.latex`, generating
`build/paper.tex`, where `build` is the output directory. In `build` you will
find various intermediate files generated by the `pdflatex` and `biber`
commands, in addition to the built PDF file `paper.pdf` and a copy of all cited
bibtex entries `paper_biber.bib`.

Enter `make clean` to remove the `build` directory.

# Acknowledgements

[ieee-pandoc-template](https://github.com/stsewd/ieee-pandoc-template) was used as a starting point.

Note that the bibliography is not correctly formatted when using the ieee CSL
file, hence why I use the `--biblatex` flag when calling pandoc.
