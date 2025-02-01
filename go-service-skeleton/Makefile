export BINARY_NAME = "go-service"
packages = \
	./data\
	./server\

# global command
all: dependencies build test

dependencies:
	go mod download

build:
	go build -o bin/${BINARY_NAME}

start:
	bin/${BINARY_NAME}

docker:
	docker build -t go-service-image .

docker-push:
	docker push go-service-image

docker-run:
	docker run -p 8080:8080 go-service-image

clean:
	rm -fr bin

test:
	@$(foreach package,$(packages), \
    		set -e; \
    		go test $(package);)

.PHONY: all dependencies start build test
