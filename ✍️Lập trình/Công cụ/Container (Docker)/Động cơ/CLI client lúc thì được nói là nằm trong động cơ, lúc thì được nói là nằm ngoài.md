---
share: true
updated: 2026-08-06T15:36
created: 2026-08-04T16:24
---
Khái niệm:: 
The documentation indeed says:

![](https://global.discourse-cdn.com/docker/original/3X/e/2/e2d03ad1f89c70390161df860b3d879ed8e31734.png) [Docker Documentation – 25 Sep 23](https://docs.docker.com/engine/ "04:59PM - 25 September 2023")

![](https://global.discourse-cdn.com/docker/original/3X/e/2/e2d03ad1f89c70390161df860b3d879ed8e31734.png)

### [Docker Engine overview](https://docs.docker.com/engine/)

Engine

> Docker Engine acts as a client-server application with:
> 
> - A server with a long-running daemon process [`dockerd`](https://docs.docker.com/engine/reference/commandline/dockerd).
> - APIs which specify interfaces that programs can use to talk to and instruct the Docker daemon.
> - A command line interface (CLI) client [`docker`](https://docs.docker.com/engine/reference/commandline/cli/).

So it includes the CLI, but if you check the [Docker Desktop overview](https://docs.docker.com/desktop/), it mentiones the Engine and the CLI although the CLI is not linked:

> ## What’s included in Docker Desktop?
> 
> - [Docker Engine](https://docs.docker.com/engine/)
> - Docker CLI client
> - [Docker Buildx](https://docs.docker.com/build/)  
>     …

You can also install the client without daemon even though it is part of the Engine. I guess the reason is something historical.
Nguồn:: [Difference between Docker Desktop and Docker Engine - General - Docker Community Forums](https://forums.docker.com/t/difference-between-docker-desktop-and-docker-engine/124612/14)
