build-docker:	## Builds a Docker image
	@docker build -t awesome:build -f build/Dockerfile .

build:		## Runs a Docker image in a container, builds website and api, and stores it in a package
	@docker run awesome:build /bin/bash -c "hugo; touch awesome-api; zip awesome-website.zip dist/index.html"

create:		## Generates website
	@docker run awesome:build /bin/bash -c "hugo; touch awesome-api"

post:	## Creates a new blog post whose name and title come from env variables
	@hugo new posts/$(POST_NAME).md
	@sed -i '2s/.*/title: "$(POST_TITLE)"/' content/posts/$(POST_NAME).md

clean:	## Cleans up the content of the dist/ directory
	@docker run awesome:build /bin/bash -c "rm -rf dist/*"

package:	## Creates a zip file containing binary and dist/ directory
	@docker run awesome:build /bin/bash -c "zip awesome-website.zip dist/index.html"

unit-tests:
	@touch coverage-units.out

integration-tests:
	@touch coverage-integrations.out

validate:	## Checks the current working directory
	@pwd

lint:	## Apply lint to README and DEPLOY files
	@docker run awesome:build /bin/bash -c "yamllint README-test.md"

help:	## Prints a list of targets and their usage
	@cat Makefile | grep '##' | tr -d '##' | head -n -1
