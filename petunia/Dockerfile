FROM node:10.20.1

WORKDIR /home

COPY petunia /home/

RUN apt-get update
RUN apt-get install -y sqlite3 vim

WORKDIR /home/petunia
RUN npm install

CMD npm start

