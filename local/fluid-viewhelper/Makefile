SHELL := /bin/bash

BRANCH ?= $$(git rev-parse --abbrev-ref HEAD 2> /dev/null)

.PHONY: env build generate clean

env:
	@echo "UID=$$(id -u)" > .env
	@echo "GID=$$(id -g)" >> .env

build: env
	@echo "Build TYPO3 View Helper schema generator environment [branch: $(BRANCH)]"
	@docker-compose build --force-rm
	@docker-compose run install

generate: env
	@echo "Generate TYPO3 View Helper schema [branch: $(BRANCH)]"
	@docker-compose run generate

clean:
	@echo "Remove TYPO3 View Helper schema generator environment"
	@docker-compose down --rmi all --volumes
