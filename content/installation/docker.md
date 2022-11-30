---
type: "page"
creatordisplayname: "Rob Barnes"
creatoremail: ""
lastmodifierdisplayname: "Rob Barnes"
lastmodifieremail: ""
title: Docker
weight: 1
---

Rift is available as a Docker image on [Docker Hub](https://hub.docker.com/orgs/hashicorpdevadvocates)

In order to run this image the following prerequisistes will need to be met:

- [Boundary resources will need to be created.](/boundary)
- [Rift configuration file will be required](/rift-configuration)

### Example Using config.json File

```sh
docker run \
    -p 4444:4444 \
    -v ${PWD}/config:/config \
    hashicorpdevadvocates/rift:development
```

_**NOTE:** See [Rift Configuration Documentation](/rift-configuration) for details on writing a configuration file._

<!-- ### Example Using Environment Variables

```sh
docker run \
    -p 4444:4444 \
    -e "LOG_LEVEL=debug" \
    -e "BOUNDARY_ADDR=https://hcp.boundary-address.com" \
    -e "BOUNDARY_AUTH_METHOD=ampw_1234567890" \
    -e "BOUNDARY_AUTH_USERNAME=rift" \
    -e "BOUNDARY_AUTH_PASSWORD=rift-password" \
    -e "BOUNDARY_ORGANISATION=rift-org" \
    -e "PAGERDUTY_ENABLED=true" \
    -e "PAGERDUTY_TOKEN=pd-token" \
    hashicorpdevadvocates/rift:development
```

_**NOTE:** For details of all environment variables available to use, see the [Rift Configuration Documentation.](/rift-configuration)_ -->

### Example Docker Compose File

```yaml
version: "3.9"
services:
  rift:
    image: hashicorpdevadvocates/rift:development
    ports:
      - "4444:4444"
    volumes:
      - "./config:/rift"
    command:
      - "-config-file-directory=/rift"
      - "-config-file=config.json"
```

### Example Shipyard Blueprint

This example assumes you have a working installation of [shipyard](https://shipyard.run) and Docker installed.

```hcl
network "public" {
  subnet = "10.16.0.0/24"
}

container "rift" {
  image {
    name = "hashicorpdevadvocates/rift:development"
  }

  port {
      local  = 4444
      host   = 4444
      remote = 4444
  }
  volume {
      source      = "./config"
      destination = "/config"
  }

  network {
      name       = "network.public"
      ip_address = "10.16.0.203"
  }
}
```
