# Heroku Kafka Topic Viewer App

A simple Heroku java app that demonstrates viewing a Kafka Topic.
This demo app accepts HTTP POST requests and writes them to a topic, and has a simple page that shows the last 10 messages produced to that topic. You can also use my Kafka Demo Producer to crank out tons of messages instead of doing it manually

You'll need to [provision](#provisioning) the app.

## Quick Provisioning

Push this to your new Heroku app that has access to your Kafka cluster on Heroku (Common or Private Space)

Add a Config Var as follows:

KAFKA_TOPIC = messages

Restart the Heroku App and launch

Type a message in the app form field and see it come back from the Kafka Topic

## Normal Provisioning

Install the kafka cli plugin:

```
$ heroku plugins:install heroku-kafka
```

Create a heroku app with Kafka attached:

```
$ heroku create
$ heroku addons:create heroku-kafka:beta-dev
$ heroku kafka:wait
```

Create the sample topic, by default the topic will have 32 partitions.

```
$ heroku kafka:create messages
```

Set an environment variable referencing the new topic:

```
$ heroku config:set KAFKA_TOPIC=messages
```

Deploy to Heroku and open the app:

```
$ git push heroku master
$ heroku open
```
