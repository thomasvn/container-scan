help: ## Show this help
	@egrep -h '\s##\s' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-20s\033[0m %s\n", $$1, $$2}'

rebuild: ## Rebuild the UBI7 container
	- docker stop ubi7
	- docker rm ubi7
	- docker rmi thomasvn3.jfrog.io/ubi-7/ubi7:test
	docker build -t thomasvn3.jfrog.io/ubi-7/ubi7:test .

stop: ## Stop UBI7 container
	- docker stop ubi7
	- docker rm ubi7

debug: ## Get a shell in the UBI7 container
	make stop
	docker run -it --name ubi7 thomasvn3.jfrog.io/ubi-7/ubi7:test bash