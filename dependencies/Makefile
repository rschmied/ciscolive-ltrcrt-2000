USER := ralphschmieder
NAME := ltrcrt2000
VERSION := 26.1.0

.PHONY: all

all: .built

.built: Dockerfile pyproject.toml uv.lock
	docker buildx build -t $(USER)/$(NAME) .
	touch $@

push: .built
	# -docker image remove $(USER)/$(NAME):latest
	docker tag $(USER)/$(NAME):latest $(USER)/$(NAME):$(VERSION)
	docker push $(USER)/$(NAME)
	docker push $(USER)/$(NAME):$(VERSION)
	uv export --format requirements-txt --no-hashes >requirements.txt
