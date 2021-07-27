# 3DTiles Server

## General information

In the context of development (e.g. on your desktop)and if you need to handle over [3DTiles tilesets](https://github.com/AnalyticalGraphicsInc/3d-tiles) for your client to display then you can deploy a local (on your desktop computer) web (http) server. 
A quick and easy way to do so (on your desktop) consists in installing a (node.js based) [3d-tiles-samples](https://github.com/AnalyticalGraphicsInc/3d-tiles-samples) server.

This repository offers the containerized version of [3d-tiles-samples](https://github.com/AnalyticalGraphicsInc/3d-tiles-samples) server.

## Building and running the container with docker

Use the [Dockerfile](3dtiles-server-context/Dockerfile) provided within the 3dtiles-server-context directory e.g. with the commands

```bash
   docker build 3dtiles-server-context -t 3dtiles-server
   docker run 3dtiles-server
```

The server content will then be available at the `http://localhost:8996/tilesets/` address.

If you need to configure the tileset you want to upload or the port where the server will be available, you have 2 options:

- directly modify the Dockerfile file in order to change the default ARG variables content to suit your needs. You will not need to add anything to the building docker command line shown above.
- add parameters to the docker build command line as shown below:

```bash
   docker build 3dtiles-server-context -t 3dtiles-server --build-arg TILESET_SOURCE=<Your_Tileset_Source>
```

Refer to the [docker documentation](https://docs.docker.com/engine/reference/commandline/build/#set-build-time-variables---build-arg) for further details on handling arguments.

Please refer to the [example .env file](./Example/.env) for the complete list of environment variables available and what they are used for.

## Illustrating the container arguments/parameters with docker-compose

- Copy the context folder provided in this directory in your compose folder.
- Create a .env file in your compose folder (except when one already exists).
- Add the code located in this [example .env file](./Example/.env) to your own .env file.
- Configure the variables to suit your needs. A brief description is located above each variable to describe its role in the .env file.
- Add the code located in this [example docker compose file](./Example/docker-compose.yml) to your docker-compose.yml file (within the `services` section)
- Build and launch your docker-compose.
- Your tileset should now be available at the following address: `localhost:<YOUR_SERVER_PORT>/tilesets/<YOUR_TILESET_NAME>`
