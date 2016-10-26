Running the development setup
=============================

Developing in Windows
---------------------

1. Download an install [Docker Toolbox](https://www.docker.com/products/docker-toolbox).
2. Download and install [Consul](https://www.consul.io/downloads.html).
3. Create a directory in `C:\Users\git2consul.d` and copy the `config.json` file.
4. Clone the projects:
	1. [cfs-core](https://github.com/commonms/cfs-core)
	2. [cfs-connector](https://github.com/commonms/cfs-connector)
5. Run *consul* using the script in `cfs-core/run-consul.cmd`.
6. Run *git2consul* running the script in `cfs-core/run.git2consul.sh` **within the Docker Toolbox bash**.
7. Run *mongodb* with the following command in docker:

	```
	docker run --name cfs-db -p 27017:27017 -d mongo
	```
8. Set the environment variable to running the projects:

	```
	CFS_CONFIG_CONSUL_SERVER=192.168.99.100
	```
9. Run the projects (*cfs-core* and *cfs-connector*) with the following system variables:

	```
	-Dspring.cloud.consul.host=192.168.99.1 -Dspring.cloud.consul.discovery.prefer-ip-address=true -Dspring.cloud.consul.discovery.ip-address=127.0.0.1
	```
10. You can inspect the running services in http://192.168.99.1:8500/ui/#/dc1/services
and the properties in http://192.168.99.1:8500/ui/#/dc1/kv/