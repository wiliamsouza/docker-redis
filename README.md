docker-redis
------------

Docker redis server generic image source. This is based on `ubuntu:12.04` image.

Image
-----

You can `pull` a ready to use image from Docker
[index](https://index.docker.io/u/wiliamsouza/) running:

```
$ docker.io pull wiliamsouza/redis
```

Or build this repository:

```
$ git clone https://github.com/wiliamsouza/docker-redis.git
$ cd docker-redis/
$ docker.io build -t wiliamsouza/redis .
```

Change `wiliamsouza/redis` to your Docker index username.

Container
---------

This image uses volumes and environment variables to control the redis server
configuration.

Volumes:

* `/etc/redis`: Change server configurations using it.
* `/var/lib/redis`: Data goes here.
* `/var/log/redis`: Access log from the container using it.

You pass with `-v` docker option. Don't forget to use absolute path here.

Shell access:

```
$ docker.io run -p 6379:6379 -i \
-v `pwd`/volumes/log:/var/log/redis \
-v `pwd`/volumes/lib:/var/lib/redis \
-v `pwd`/volumes/etc:/etc/redis/conf.d \
-t wiliamsouza/redis /bin/bash
```

The command above will start a container give you a shell. Don't
forget to start the service running the `startup &` script.

Usage:

```
$ docker.io run --name redis -p 6379:6379 -d \
-v `pwd`/volumes/log:/var/log/redis \
-v `pwd`/volumes/lib:/var/lib/redis \
-v `pwd`/volumes/etc:/etc/redis \
-t wiliamsouza/redis
```

The command above will start a container and return its ID.
