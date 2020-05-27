FROM node:10.20.1

WORKDIR /home

COPY azalea /home/azalea

RUN apt-get update

WORKDIR /home/azalea
RUN npm install

CMD npm start
