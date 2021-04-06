help: ## Show this help
	@egrep -h '\s##\s' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-20s\033[0m %s\n", $$1, $$2}'

go: ## Build and run!
	docker build -t oscap .
	docker run -it -v $$(pwd):/home oscap bash

build: ## Build the container image
	docker build -t oscap .

run: ## Run the container
	docker run -it -v $$(pwd):/home oscap bash

rh: ## Debug the RedHat UBi container
	docker run -it --rm ib-ubi7:7.9
