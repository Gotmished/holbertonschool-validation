build:	## Generates website from markdown and configuration files in dist/ directory
	@hugo

post:	## Creates a new blog post whose name and title come from env variables
	@hugo new posts/$(POST_NAME).md
	@sed -i '2s/.*/title: "$(POST_TITLE)"/' content/posts/$(POST_NAME).md

clean:	## Cleans up the content of the dist/ directory
	@rm -rf dist/*

package:	## Creates a zip file containing binary and dist/ directory
	@make build
	@zip awesome-website.zip dist/

unit-tests:	## Tests various make recipes
	@make package
	@make clean

help:	## Prints a list of targets and their usage
	@cat Makefile | grep '##' | tr -d '##' | head -n -1
