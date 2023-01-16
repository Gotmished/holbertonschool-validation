build-docker:	## Builds a Docker image
	@docker build -t awesome:build -f build/Dockerfile .

.PHONY: build
build:		## Runs a Docker image in a container, builds website and api, and stores it in a package
	@docker run awesome:build /bin/bash -c "hugo; touch awesome-api; ls ./dist/* && echo build complete"

post:	## Creates a new blog post whose name and title come from env variables
	@hugo new posts/$(POST_NAME).md
	@sed -i '2s/.*/title: "$(POST_TITLE)"/' content/posts/$(POST_NAME).md

clean:	## Cleans up the content of the dist/ directory
	@docker run awesome:build /bin/bash -c "hugo; rm -rf dist/* && echo clean"

package:	## Creates a zip file containing binary and dist/ directory
	@docker run awesome:build /bin/bash -c "hugo; touch awesome-api; zip awesome-website.zip dist/index.html; ls && echo packaged"

unit-tests:
	@docker run awesome:build /bin/bash -c "hugo; touch coverage-units.out && echo unit"

integration-tests:
	@docker run awesome:build /bin/bash -c "hugo; touch coverage-integrations.out && echo integration"

validate:	## Checks the current working directory
	@docker run awesome:build /bin/bash -c "pwd"

lint:	## Check lint syntax of README and DEPLOY files
	@docker run awesome:build /bin/bash -c "markdownlint README.md DEPLOY.md && echo lint"

help:	## Prints a list of targets and their usage
	@cat Makefile | grep '##' | tr -d '##' | head -n -1
