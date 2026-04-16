# Belmontpark HOA Governing Documents
This repository holds the governing documents for the HOA.  Currently those are
- CCRs
- Bylaws

## Document format
The documents under the docs directory are written in [pandoc](https://www.pandoc.org)
[markdown format](https://pandoc.org/MANUAL.html#pandocs-markdown).  This
allows the content to be addressed without worrying about formatting.  For example, the PDF and HTML outputs
each format to their specific layouts independent of the source document text.

## How to build locally
In order to build the documents locally, you'll need both [pandoc](https://www.pandoc.org) and
[pandoc-crossref](https://github.com/lierdakil/pandoc-crossref).  The process will vary depending on the
operating system choice so follow the directions each project provides (the documentation is quite good).
Once both are installed, you can build the documents into a PDF as follows from the root directory of this repo:

    pandoc --from=markdown  -F pandoc-crossref -N  --toc=true --toc-depth=2 -s -o output/bylaws.pdf docs/bylaws.md
    pandoc --from=markdown  -F pandoc-crossref -N  --toc=true --toc-depth=2 -s -o output/ccrs.pdf docs/ccrs.md

This will produce the PDF output of the bylaws and ccrs in the output directory.  There's a git ignore in place
for the output directory to prevent any output being checked in.

## Github actions build
The github action build_docs will create the PDF output of the bylaws and CCRs on every commit on any branch.  If you are
not able to create a local environment to build the docs, you can commit to your branch and then check the artifacts
produced to see the finished rendered document.