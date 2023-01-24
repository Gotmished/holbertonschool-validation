build:	## Compiles source code of application to a binary
	mkdir awesome-api
	cd awesome-api
	go mod init github.com/Gotmished/awesome-api
	go build -o awesome-api main.go
	
run:	## Run application in background
	go run main.go ./awesome-api >./awesome.log 2>&1 &

stop:	## Stop the application
	pgrep main | xargs kill

clean:	## Deletes the binary and log file
	rm -rf ./awesome-api
	rm awesome.log
	rm go.mod

test:	## Testing the project
	curl http://localhost:9999
	curl http://localhost:9999/health

help:	## Prints a list of targets and their use
	cat Makefile | grep '##' | tr -d '##' | head -n -1