# You must have jekyll and R installed, and they must be in PATH. For R, you
# need to install the servr package.

all:
	Rscript -e "servr::jekyll(
	  input = c('..', '../_source/tutorial', '../_source/documentation',
	    '../_source/recipes', '../_source/recipes/tcltk', '../_source/blog'),
	  output = c('..', '../_posts/tutorial', '../_posts/documentation',
	    '../_posts/recipes', '../_posts/recipes/tcltk', '../_posts/blog'))"

clean:
	rm -r ../_site
