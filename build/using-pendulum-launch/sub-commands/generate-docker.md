---
description: >-
  In this section we discuss using pendulum-launch to generate a docker-compose
  configuration.
---

# generate-docker

The following command details how to generate a docker-compose configuration.  Node configurations in your launcher config, have an optional `dockerfile` value.  When set for each node, a docker-compose file will be generated in your current working directory or in the optional `outdir`.

{% hint style="info" %}
`pendulum-launch help generate-docker`
{% endhint %}

```
pendulum-launch-generate-docker 0.2.0
Generate docker-compose.yml

USAGE:
    pendulum-launch generate-docker [OPTIONS]

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
    -o, --outdir <outdir>
```
