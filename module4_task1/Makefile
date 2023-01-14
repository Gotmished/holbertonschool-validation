build-docker:	## Builds a Docker image
	@docker build -t awesome:build -f build/Dockerfile .

build:		## Runs a Docker image and builds website and api
	@mkdir dist
	@docker run -dp 1313:1313 awesome:build make build-website
	@docker run -dp 1313:1313 awesome:build touch awesome-api

build-website:# Build the website
	@hugo --source . --destination dist

post:	## Creates a new blog post whose name and title come from env variables
	@hugo new posts/$(POST_NAME).md
	@sed -i '2s/.*/title: "$(POST_TITLE)"/' content/posts/$(POST_NAME).md

clean:	## Cleans up the content of the dist/ directory
	@rm -rf dist/*

package:	## Creates a zip file containing binary and dist/ directory
	@zip awesome-website.zip dist/index.html

unit-tests:
	@touch coverage-units.out

integration-tests:
	@touch coverage-integrations.out

validate:	## Checks the current working directory
	@pwd

lint:	## Apply lint to README and DEPLOY files
	@make build
	@yamllint README-test.md

help:	## Prints a list of targets and their usage
	@cat Makefile | grep '##' | tr -d '##' | head -n -1
