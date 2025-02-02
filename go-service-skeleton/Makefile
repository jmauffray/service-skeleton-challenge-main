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

docker-build:
	docker build -t go-service-image:0.1 -f Dockerfile .

docker-push:
	docker push go-service-image:0.1

docker-run:
	docker run -p 8080:8080 go-service-image:0.1

k3s-build:
	docker run --privileged  --name k3s-server --hostname k3s-server --network=host -d rancher/k3s:v1.32.1-k3s1 server
	sleep 20
	mkdir -p dist/k3s/
	docker cp k3s-server:/etc/rancher/k3s/k3s.yaml dist/k3s/config.yaml
	export KUBECONFIG=dist/k3s/config.yaml
	kubectl get pods -A

k3s-start:
	export KUBECONFIG=dist/k3s/config.yaml
	kubectl run service-go --image=go-service-image:0.1 --port=8080

helm-install:
	export KUBECONFIG=dist/k3s/config.yaml
	helm upgrade --install --namespace default service-go ./helm/service-go -f helm/service-go/values.yaml

clean:
	rm -fr bin

test:
	@$(foreach package,$(packages), \
    		set -e; \
    		go test $(package);)

.PHONY: all dependencies start build test
