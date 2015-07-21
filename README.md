# rabbitmq-mongodb
A lightweigth docker container (55MB in size) which will automatically stream new items from the a rabbitmq queue `RABBITMQ_QUEUE_NAME` into mongodb collection `MONGODB_COLLECTION` with the help of nodejs' [amqp-to-mongo](https://www.npmjs.com/package/amqp-to-mongo). This is the source for building the docker image [marcelmaatkamp/rabbitmq-mongodb](https://registry.hub.docker.com/u/marcelmaatkamp/rabbitmq-mongodb)
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
