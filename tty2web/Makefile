DOCKER_REPO := lracz/tty2web
VERSION := 1.0.0

.PHONY: build
build:
	docker buildx create --use --name tty2web-builder
	docker buildx build --platform linux/amd64,linux/arm64 \
		-t $(DOCKER_REPO):$(VERSION) \
		-t $(DOCKER_REPO):latest \
		--push .

.PHONY: push
push:
	docker push $(DOCKER_REPO):$(VERSION)
	docker push $(DOCKER_REPO):latest

.PHONY: clean
clean:
	docker buildx rm tty2web-builder

.PHONY: all
all: build push clean
