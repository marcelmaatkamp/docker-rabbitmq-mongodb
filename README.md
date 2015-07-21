# docker-rabbitmq-mongodb

This image will automatically stream new items from the queue `RABBITMQ_QUEUE_NAME` into mongodb `MONGODB_COLLECTION` with the help of nodejs' [amqp-to-mongo](https://www.npmjs.com/package/amqp-to-mongo). This image is based on the lightweigth [Alpine Linux](https://www.alpinelinux.org/) and is just 55 MB in size.

This is the source for building the docker image [marcelmaatkamp/rabbitmq-mongodb](https://registry.hub.docker.com/u/marcelmaatkamp/rabbitmq-mongodb)

# Usage

To stream the queue `amqp://RABBITMQ_HOSTNAME/RABBITMQ_QUEUE_NAME` into `mongodb://MONGODB_HOSTNAME/MONGODB_DATABASE/MONGODB_COLLECTION` use:
```
  $ docker run -d \
    --restart=always \
    --name rabbitmq-mongodb \
    -e AMQPHOST=amqp://<RABBITMQ_HOSTNAME> \
    -e MONGODB=mongodb://<MONGODB_HOSTNAME>/<MONGODB_DATABASE> \
    -e MONGOCOLLECTION=<MONGODB_COLLECTION> \
    -e TRANSLATECONTENT=true \
    marcelmaatkamp/rabbitmq-mongodb <RABBITMQ_QUEUE_NAME>
```
