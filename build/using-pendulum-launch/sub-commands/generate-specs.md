---
description: In this section we discuss using pendulum-launch to generate collator specs.
---

# generate-specs

The following command details how to generate collator specs.  The path to your collator binary must be passed.  The name option specifies the output file name, the outdir option specifies the directory to output specs, and the para-id option will replace the para\_id of the plain spec inline, before generating the raw spec.

{% hint style="info" %}
`pendulum-launch help generate-specs`
{% endhint %}

```
pendulum-launch-generate-specs 0.1.0
Generate specs

USAGE:
    pendulum-launch generate-specs [OPTIONS] <bin>

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
    -n, --name <name>
    -o, --outdir <outdir>
    -i, --para-id <para-id>

ARGS:
    <bin>
```
