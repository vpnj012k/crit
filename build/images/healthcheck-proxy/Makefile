VERSION = v0.1.0
IMAGE_REGISTRY ?= docker.io
IMAGE_ORG ?= criticalstack
GCFLAGS = -gcflags "all=-trimpath=$(PWD)" -asmflags "all=-trimpath=$(PWD)"
GO_BUILD_ENV_VARS := GO111MODULE=on CGO_ENABLED=0

healthcheck-proxy:
	@cd ../../../; $(GO_BUILD_ENV_VARS) go build -o bin/healthcheck-proxy $(GCFLAGS) ./cmd/healthcheck-proxy

build:
	cd ../../../; docker build . -f build/images/healthcheck-proxy/Dockerfile -t $(IMAGE_REGISTRY)/$(IMAGE_ORG)/healthcheck-proxy:$(VERSION) --build-arg GOPROXY --build-arg GOSUMDB

push:
	@docker push $(IMAGE_REGISTRY)/$(IMAGE_ORG)/healthcheck-proxy:$(VERSION)
