HELP_FUN = \
	%help; \
	while(<>) { push @{$$help{$$2 // 'options'}}, [$$1, $$3] if /^([a-zA-Z\-]+)\s*:.*\#\#(?:@([a-zA-Z\-]+))?\s(.*)$$/ }; \
	print "usage: make [target]\n\n"; \
	for (sort keys %help) { \
	print "${WHITE}$$_:${RESET}\n"; \
	for (@{$$help{$$_}}) { \
	$$sep = " " x (32 - length $$_->[0]); \
	print "  ${YELLOW}$$_->[0]${RESET}$$sep${GREEN}$$_->[1]${RESET}\n"; \
	}; \
	print "\n"; }

UID:=$(shell id -u)
GID:=$(shell id -g)
PWD:=$(shell pwd)

.PHONY: help
help: ##@other Show this help.
	@perl -e '$(HELP_FUN)' $(MAKEFILE_LIST)

.PHONY: setup
setup: ##@setup builds the docker image for the cli make cmd
	docker build -t elixir-hex ./docker/cli/

.PHONY: cli
cli: ##@setup set up a docker container with mounted source where you can execute all elixir commands
	docker run -it --rm  -u $(UID):$(GID) -v $(PWD):/source -w /source elixir-hex bash
