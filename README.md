# onetimesecret

'Keep sensitive info out of your email and chat logs'

Launch [One-Time Secret](http://onetimesecret.com) as a Docker container

## Usage


Either use `docker-compose up`

or run manually:


```bash

docker run --name=onetimesecret -p 7143:7143 --link redis:redis mcrmonkey/docker-onetimesecret

```

The container expects to be able to connect to `redis` as the redis hostname
for the storage of secrets.
You can override this in the configuration file.


Or build it yourself:

```bash

docker build . -t='my_onetimesecret'

docker run -d --name redis redis

docker run --name=onetimesecret -p 7143:7143 --link redis:redis -t my_onetimesecret

```

Access it through your browser at `http://localhost:7143`

## Limitations and things to be aware of

* The application generates a link that uses a preconfigured domain and port.
  Right now it is only generating using `localhost:4173`

* The default secret is set to `CHANGEME` in the configuration file. Its
  probably a good idea to change this to something more complex

* The container has a default configuration file. You can either re-build the
  container or map your own configuration file in to the container using the
  docker volume option.


### Credit

Some of the configuration and inspiration for this came from https://github.com/carlasouza/docker-onetimesecret

