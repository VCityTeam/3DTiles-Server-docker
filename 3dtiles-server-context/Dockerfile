FROM node:latest

LABEL maintainer "VCityTeam"

RUN apt-get update
RUN apt-get install -y git
RUN apt-get install -y wget

ARG TILESET_SOURCE=https://dataset-dl.liris.cnrs.fr/three-d-tiles-lyon-metropolis/Lyon_2015-gltf-repaired_TileSet/
ENV TILESET_SOURCE=${TILESET_SOURCE}
ARG TILESET_SERVER_PORT=8996
ENV TILESET_SERVER_PORT=${TILESET_SERVER_PORT}

RUN git clone https://github.com/AnalyticalGraphicsInc/3d-tiles-samples
WORKDIR /3d-tiles-samples
RUN git reset --hard 1901e7ed563c6efc59888237ca56807a759e269f

# Import an example of 3DTiles embedding some IFC geometry
WORKDIR /3d-tiles-samples/tilesets/

RUN wget --recursive --no-parent --no-host-directories --cut-dirs=1 -R 'index.html?*' ${TILESET_SOURCE}


WORKDIR /3d-tiles-samples/
RUN npm install
EXPOSE ${TILESET_SERVER_PORT}
CMD [ "npm", "start", "--", "--public", "--port=${TILESET_SERVER_PORT}"]
