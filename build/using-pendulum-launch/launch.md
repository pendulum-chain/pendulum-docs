---
description: In this section we discuss using pendulum-launch to launch a parachain.
---

# 🚀 Launch

The following command details how pendulum-launch is used.  The `--config` option can be used to set the path of a config file.  The `--log` option can be used to set an alternate logging directory.

{% hint style="info" %}
`pendulum-launch help`
{% endhint %}

```
pendulum-launch 0.2.0

USAGE:
    pendulum-launch [FLAGS] [OPTIONS] [SUBCOMMAND]

FLAGS:
    -h, --help       Prints help information
    -q, --quiet
    -V, --version    Prints version information

OPTIONS:
    -c, --config <config>
    -l, --log <log>

SUBCOMMANDS:
    export-genesis     Export genesis data
    generate-docker    Generate docker-compose.yml
    generate-specs     Generate specs
    help               Prints this message or the help of the given subcommand(s)
```

As an example, we might want to launch our parachain as follows `./bin/pendulum-launch --config ./launch-local.json --log ./tmp/local` in order to provide an alternate config and log directory.
