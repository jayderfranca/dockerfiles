TAG ?= 1.0.0
IMAGE ?= sambaad
CONTAINER ?= sambaad
CUSTOM ?= /.local/opt/custom

default: build

build:
	docker image rm $(NAMESPACE)$(IMAGE):$(TAG) || exit 0
	docker buildx build --no-cache --tag $(NAMESPACE)$(IMAGE):$(TAG) --file Dockerfile .

shell:
	docker run --rm --name $(CONTAINER) --hostname $(CONTAINER) --interactive --tty $(PORTS) $(VOLUMES) $(ENV) $(NAMESPACE)$(IMAGE):$(TAG) /bin/sh

run:
	docker run --rm --name $(CONTAINER) --hostname $(CONTAINER) --interactive --tty $(PORTS) $(VOLUMES) $(ENV) $(NAMESPACE)$(IMAGE):$(TAG)

push:
	docker push $(NAMESPACE)$(IMAGE):$(TAG)
