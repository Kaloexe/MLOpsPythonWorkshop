FROM node:latest AS build
WORKDIR /build

COPY package.json package.json
COPY package-lock.json package-lock.json
RUN npm ci

COPY public/ public
COPY src/ src
COPY index.html intex.html # docker build . -t daemon
COPY vite.config.js vite.config.js
RUN npm run build

FROM nginx:alpine
COPY --from=build /build/build/ /usr/share/nginx/html