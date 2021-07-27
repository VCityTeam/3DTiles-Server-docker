# 3DTiles Server

## General information

In the context of development (e.g. on your desktop)and if you need to handle over [3DTiles tilesets](https://github.com/AnalyticalGraphicsInc/3d-tiles) for your client to display then you can deploy a local (on your desktop computer) web (http) server. A quick and easy way to do so (on your desktop) consists in installing a (node.js based) [3d-tiles-samples](https://github.com/AnalyticalGraphicsInc/3d-tiles-samples) server.

## Simple to install 3DTiles web server ([node.js](https://nodejs.org/en/) based) 

### Manual installation
A quick manual installation goes
```
   git clone https://github.com/AnalyticalGraphicsInc/3d-tiles-samples
   cd 3d-tiles-samples
   npm install
   npm start
```
The tileset examples will then browsable at the `http://localhost:8003/tilesets/` 
address (since `8003` is the default port).

Run
```
   npm start -- help
```
for further server options e.g. `npm start -- --port 8080` will have the server
listen to the `8080` port

### Using docker
Use the [Dockerfile](Dockerfile) provided within the 3dtiles-server-context directory e.g. with
the commands
```
   docker build 3dtiles-server-context -t 3dtiles-server
   docker run 3dtiles-server
```
The server content will then be available at the `http://localhost:8996/tilesets/` address.

If you need to configure the tileset you want to upload or the port where the server will be available, you have 2 options :
 - You can modify the dockerfile directly to change the default ARG variables content to suit your needs. you will not need to add anything to the initial command line shown above.
 - You can add parameters to the docker build command line as shown below :
 ```
   docker build 3dtiles-server-context -t 3dtiles-server --build-arg TILESET_SOURCE=<Your_Tileset_Source>
 ```
See [this page](https://docs.docker.com/engine/reference/commandline/build/#set-build-time-variables---build-arg) for further instructions.

Please refer to the [example .env file](./Example/.env) for the complete list of environment variables available and what they are used for.


### Using docker-compose

 - Copy the context folder provided in this directory in your compose folder.
 - Create a .env file in your compose folder (if one already exists, do not create another).
 - Add the code located in this [example .env file](./Example/.env) to your own .env file.
 - Configure the variables to suit your needs. A brief description is located above each variable to describe its role in the .env file.
 - Add the located in this [example docker compose file](./Example/docker-compose.yml) code to your docker-compose.yml file as a service
 - Build and launch your docker-compose.
 - Your tileset should now be available at the following address : localhost:<YOUR_SERVER_PORT>/tilesets/<YOUR_TILESET_NAME>
