build-dir    = ../../_build/cmp-tex/


source-files = \
	cmp.tex \
	cmp_macros.tex  \
	cmp_lmacros.tex \
	cmp_bound.tex   \
	cmp_elaboration.tex \
	cmp_inductive.tex \
	cmp_pattern_match.tex


# Generate a pdf from scratch:
#     make pdf			1st pass collect all references
#     make bib			extract from bib database
#     make pdf			2nd pass update references


# Run pdflatex and generate the pdf file (only once)
# Run it twice to get crossreferences correct if new labels have been
# introduced.
.PHONY: pdf
pdf:
	rm $(build-dir)*.tex;  \
	cp $(source-files) $(build-dir); \
	(cd $(build-dir); pdflatex cmp.tex)


# Extract citations for the bib database. Run always, if a new citation has been
# added.
.PHONY: bib
bib:
	(cd $(build-dir); bibtex cc)
