SHELL := /bin/bash

BRANCH ?= $$(git rev-parse --abbrev-ref HEAD 2> /dev/null)

# Create TYPO3 view helper schema from this TYPO3 branch
TYPO3_BRANCH = "11.5"

.PHONY: env install update generate clean

env:
	@echo "UID=$$(id -u)" > .env
	@echo "GID=$$(id -g)" >> .env

install: env
	@echo "Install TYPO3 View Helper schema generator environment [branch: $(BRANCH)]"
	@docker-compose build --force-rm
	@docker-compose run install

update: env
	@echo "Update TYPO3 View Helper schema generator environment [branch: $(BRANCH)]"
	@docker-compose run update

generate: env
	@echo "Generate TYPO3 $(TYPO3_BRANCH) View Helper schema [branch: $(BRANCH)]"
	@docker-compose run -e "BRANCH=$(TYPO3_BRANCH)" generate

clean:
	@echo "Remove TYPO3 View Helper schema generator environment"
	@docker-compose down --rmi all --volumes
