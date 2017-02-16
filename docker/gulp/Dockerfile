FROM node:7.5

RUN mkdir /app
COPY package.json ./package.json
COPY gulpfile.js ./gulpfile.js
RUN npm install && \
	npm install gulp -g
