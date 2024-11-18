# About
This stack integrate Docker Swarm with extra features such as cron jobs, automatically updating deployed services and others.

## Features
- Ability to run cron like job using [crazymax/swarm-cronjob]
- Automatically updating your services whenever their image is refreshed using [containrrr/shepherd]

## Usages

### One-click deployment
You can also deploy the stack directly from the web:

```sh
curl -L https://raw.githubusercontent.com/swarmlibs/dockerswarm/main/docker-stack.yml | docker stack deploy -c - dockerswarm
```

### Deploy
First, retrieve the stack YML manifest:
```sh
curl -L https://raw.githubusercontent.com/swarmlibs/dockerswarm/main/docker-stack.yml -o dockerswarm-stack.yml
```

Then use the downloaded YML manifest to deploy your stack:
```sh
docker stack deploy -c swarmlibs-stack.yml dockerswarm
```

Docker Swarm Stack have now been installed. You can check to see whether the all services have started by running `docker service ls`:
```sh
root@manager01:~# docker service ls
ID             NAME                                                 MODE         REPLICAS               IMAGE
xp9o6s49abjd   dockerswarm_cronjob_service                          replicated   1/1                    crazymax/swarm-cronjob:latest
```

### Remove
```sh
docker stack rm dockerswarm
```

[crazymax/swarm-cronjob]: https://github.com/crazy-max/swarm-cronjob
[containrrr/shepherd]: https://github.com/containrrr/shepherd
