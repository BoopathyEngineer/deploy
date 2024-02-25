FROM node:alpine3.18 as build
workdir /app
COPY package.json .
RUN  npm install
COPY . .
RUN npm run build

FROM ngnix:1.23-alpine
WORKDIR /usr/share/ngnix/html
RUN rm -rf *
COPY --from=build /app/build .
EXPOSE 80
ENTRYPOINT ["ngnix","-g","doemonn off"]
