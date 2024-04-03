TAG ?= 1.0.0
IMAGE ?= servergit
CONTAINER ?= servergit
CUSTOM ?= /.local/opt/custom

default: build

build:
	docker image rm $(NAMESPACE)$(IMAGE):$(TAG) || exit 0
	docker buildx build --no-cache --tag $(NAMESPACE)$(IMAGE):$(TAG) --file Dockerfile .

shell:
	docker run --rm --name $(CONTAINER) --interactive --tty $(PORTS) $(VOLUMES) $(ENV) $(NAMESPACE)$(IMAGE):$(TAG) /bin/sh

run:
	docker run --rm --name $(CONTAINER) --interactive --tty $(PORTS) $(VOLUMES) $(ENV) $(NAMESPACE)$(IMAGE):$(TAG)

push:
	docker push $(NAMESPACE)$(IMAGE):$(TAG)