.PHONY: install run check deploy down build-api logs-%

# Default environment
default:
    $(eval env ?= dev)

# Allowed environments
env ?= dev stage prod
ifeq (,$(filter $(env),dev stage prod))
	$(error Error: env variable must be dev, stage or prod)
endif

$(info [$(env) environment])

# Version based on environment
ifeq ($(env),prod)
	export VERSION := $(shell git describe --tags --abbrev=0)
else
	export VERSION := $(shell git rev-parse --short HEAD)
endif

# Docker Compose file selection
ifeq ($(env),dev)
	FILE_ARGS=-f docker-compose.dev.yaml
else
	FILE_ARGS=-f docker-compose.prod.yaml
endif

log_lines := 10

install:
	@echo "🚀 Setting up virtual environment..."
	@uv venv --python 3.13
	@uv sync
	@uv run pre-commit install

run:
	@echo "🚀 Starting FastAPI server on localhost..."
	@uv run uvicorn src.main:app --reload

check:
	@echo "🚀 Running all pre-commit checks..."
	@uv run pre-commit run -a

deploy: build-api
	@echo "🚀 Deploying services via docker..."
	docker compose $(FILE_ARGS) up -d

down:
	@echo "🚀 Down services..."
	docker compose $(FILE_ARGS) down

build-api:
	@echo "🚀 Building api image..."
	docker build -t "first-project/api:$(VERSION)" .

logs-%:
	@echo "🚀 Showing logs for $*..."
	@docker compose $(FILE_ARGS) logs -t -f --tail $(log_lines) $(*)
