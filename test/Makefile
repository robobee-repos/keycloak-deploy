include Makefile.help
include Makefile.functions

NAME := keycloak

test: setup ##@targets Starts test containers.
	docker-compose -p $(NAME) -f test.yaml up
.PHONY: up

stop: ##@targets Stops test containers.
	docker-compose -p $(NAME) -f test.yaml stop

stop-gitea: ##@targets Stops gitea container only.
	docker-compose -p $(NAME) -f test.yaml stop gitea

test-gitea: ##@targets Stops test gitea container only.
	docker-compose -p $(NAME) -f test.yaml up gitea

stop-nginx: ##@targets Stops nginx container only.
	docker-compose -p $(NAME) -f test.yaml stop nginx

test-nginx: ##@targets Stops test nginx container only.
	docker-compose -p $(NAME) -f test.yaml up nginx

rm: stop ##@targets Stops test containers.
	docker-compose -p $(NAME) -f test.yaml rm -f

clean: stop rm ##@targets Removes docker containers and created files.
	sudo rm -rf root

setup:
	for p in keycloak db; do \
	mkdir -p root/$$p; \
	sudo chmod o+rwX root/$$p ; \
	done
.PHONY: setup
