.DEFAULT_GOAL := help

DOCKER_COMPOSE := docker-compose
DOCKER_COMPOSE_FILE_INFRA := docker-compose-infra.yml

DOCKER_INFRA := $(DOCKER_COMPOSE) -f $(DOCKER_COMPOSE_FILE_INFRA)

help: ## Help dialog.
	@grep -E '^([a-zA-Z_/%\-]+:.*?## .*$$|###)' $(MAKEFILE_LIST) | awk 'BEGIN {FS = ":.*?## "}; {printf "  \033[36m%-30s\033[0m %s\n", $$1, $$2}'

####################################################################
####################        DOCKER COMPOSE      ####################
####################################################################

up_infra: ## Create and start containers
	docker pull yandex/clickhouse-server:21.12 && \
	$(DOCKER_INFRA) up -d

down_infra: ## Stop and remove all containers
	$(DOCKER_INFRA) down

logs: ## View the output from containers
	$(DOCKER_INFRA) logs -f --tail=2000

ps: ## View the running containers
	$(DOCKER_INFRA) ps