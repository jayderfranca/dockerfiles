TAG ?= 5.14.3
IMAGE ?= activemq
CONTAINER ?= activemq
CUSTOM ?= /.local/opt/custom
URL = https://archive.apache.org/dist/activemq/$(TAG)/apache-activemq-$(TAG)-bin.tar.gz

default: build

build:
	curl --insecure --location $(URL) --output activemq.tar.gz
	docker image rm $(NAMESPACE)$(IMAGE):$(TAG) || exit 0
	docker buildx build --no-cache --build-arg ACTIVEMQ_URL=$(URL) --build-arg ACTIVEMQ_VERSION=$(TAG) --tag $(NAMESPACE)$(IMAGE):$(TAG) --file Dockerfile .
	rm -f ./activemq.tar.gz

shell:
	docker run --rm --name $(CONTAINER) --interactive --tty $(PORTS) $(VOLUMES) $(ENV) $(NAMESPACE)$(IMAGE):$(TAG) /bin/sh

run:
	docker run --rm --name $(CONTAINER) --interactive --tty $(PORTS) $(VOLUMES) $(ENV) $(NAMESPACE)$(IMAGE):$(TAG)

push:
	docker push $(NAMESPACE)$(IMAGE):$(TAG)