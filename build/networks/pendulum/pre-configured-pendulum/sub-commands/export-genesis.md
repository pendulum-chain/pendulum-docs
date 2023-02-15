---
description: >-
  In this section we discuss using pendulum-launch to export collator genesis
  data.
---

# export-genesis

The following command details how to export genesis data.  The path to your collator binary and raw chain spec must be passed.  The name option specifies the output file prefix and the outdir option specifies the directory to output genesis data.

{% hint style="info" %}
`pendulum-launch help export-genesis`
{% endhint %}

```
pendulum-launch-export-genesis 0.2.0
Export genesis data

USAGE:
    pendulum-launch export-genesis [OPTIONS] <bin> <chain>

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
    -n, --name <name>
    -o, --outdir <outdir>

ARGS:
    <bin>
    <chain>
```
