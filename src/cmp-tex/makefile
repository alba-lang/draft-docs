build-dir    = ../../_build/cmp-tex/
gh-pages-dir = ../../gh-pages


source-files = \
	cmp.tex \
	cmp_macros.tex      \
	cmp_lmacros.tex     \
	cmp_calculus.tex    \
	cmp_inductive.tex   \
	cmp_pattern_match.tex \
	cmp_ambiguity.tex   \
	cmp_find_terms.tex  \
	cmp_unification.tex \
	cmp_monads.tex \
	cmp_universes.tex   \
	cmp_bound.tex       \
	cmp_elaboration.tex


# Generate a pdf from scratch:
#     make pdf			1st pass collect all references
#     make bib			extract from bib database
#     make pdf			2nd pass update references


# Run pdflatex and generate the pdf file (only once)
# Run it twice to get crossreferences correct if new labels have been
# introduced.
.PHONY: pdf
pdf: mk-build-dir
	rm $(build-dir)*.tex;  \
	cp $(source-files) $(build-dir); \
	(cd $(build-dir); pdflatex cmp.tex)


# Extract citations for the bib database. Run always, if a new citation has been
# added.
.PHONY: bib
bib: mk-build-dir
	(cd $(build-dir); bibtex cmp)


.PHONY: mk-build-dir
mk-build-dir:
	test -d "$(build-dir)" || mkdir -p $(build-dir)




# Github Pages
#======================================================================

.PHONY: gh-pages
gh-pages:
	cp $(build-dir)/cmp.pdf $(gh-pages-dir); \
	(cd $(gh-pages-dir); git commit -a --amend --no-edit; git push -f)
