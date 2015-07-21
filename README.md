# docker-rabbitmq-mongodb

This image will automatically stream new items from the queue `RABBITMQ_QUEUE_NAME` into mongodb `MONGODB_COLLECTION` with the help of nodejs' [amqp-to-mongo](https://www.npmjs.com/package/amqp-to-mongo)

# Usage

To stream the queue `amqp://RABBITMQ_HOSTNAME/RABBITMQ_QUEUE_NAME` into `mongodb://MONGODB_HOSTNAME/MONGODB_DATABASE/MONGODB_COLLECTION`
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
