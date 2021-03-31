rerun:
	- docker stop ubi7
	- docker rm ubi7
	- docker rmi thomasvn3.jfrog.io/ubi-7/ubi7:test
	docker build -t thomasvn3.jfrog.io/ubi-7/ubi7:test .
	docker run -d --name ubi7 thomasvn3.jfrog.io/ubi-7/ubi7:test

stop:
	- docker stop ubi7
	- docker rm ubi7

debug:
	make stop
	docker run -it --name ubi7 thomasvn3.jfrog.io/ubi-7/ubi7:test bash