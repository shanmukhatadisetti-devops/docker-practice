FROM node:20 AS builder
WORKDIR /opt/server
COPY *.js .
COPY package.json .
RUN install npm

FROM node:20
WORKDIR /opt/server
EXPOSE 8080
LABEL project="practice" \
      env="dev"
ENV MONGO=true \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
COPY --from=builder /opt/server /opt/server
RUN useradd practice
RUN chown -R practice:practice /opt/server
USER practice
ENTRYPOINT ["node", "server.js"]