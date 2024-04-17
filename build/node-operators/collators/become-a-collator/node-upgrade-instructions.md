---
description: Node upgrade instructions for Pendulum and Amplitude network respectively
---

# Node upgrade instructions

## Pendulum Nodes

### Introduction&#x20;

Node upgrades are required for all collators when a new node version is released. It is very important that all nodes on the network maintain the same node version.

We provide our partners with the following installables.

* Docker Image
* .deb Ubuntu package for Ubuntu 20/22
* Precompiled binary

### Docker image

The official Pendulum docker image is located in [https://hub.docker.com/repository/docker/pendulumchain/pendulum-collator/general](https://hub.docker.com/repository/docker/pendulumchain/pendulum-collator/general)

Always use the image with the “latest” tag when you upgrade, that will have the recently pushed docker image.

```javascript
docker pull pendulumchain/pendulum-collator:latest
```

### .deb package for Ubuntu amd64 20/22

Navigate to the Pendulum Download page:

[https://downloads.pendulumchain.tech/index.html](https://downloads.pendulumchain.tech/index.html)

The latest package provided for Ubuntu is located in **pendulum\_debian\_latest** folder.

<div data-full-width="false">

<figure><img src="../../../../.gitbook/assets/image.png" alt="" width="563"><figcaption></figcaption></figure>

</div>

Download the latest package onto your server using the following command, and replace VERSION with the version provided on the page.

```bash
wget https://downloads.pendulumchain.tech/pendulum_debian_latest/pendulum_VERSION_amd64.deb
```

Once you obtained the package, navigate into the directory where the file is and use the following command sentence to install/upgrade the product:

```yaml
sudo dpkg -i pendulum_VERSION_amd64.deb
sudo service pendulum status

● amplitude.service - pendulum
     Loaded: loaded (/etc/systemd/system/pendulum.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2023-09-14 10:03:08 UTC; 52ms ago
   Main PID: 1061 (pendulum-colla)
      Tasks: 4 (limit: 4620)
     Memory: 5.7M
        CPU: 26ms
     CGroup: /system.slice/pendulum.service
             └─1061 /usr/local/bin/pendulum-collator --collator --base-path /var/lib/pendulum --no-private-ipv4 --rpc-cors all --force-authoring --enable-offchain-indexing=true --ws-port 8844 --ws-max-connections 200 --port 30335 --rpc-port 9955 --chain /var/lib/amplitude/amplitude-spec-raw.json --execution=wasm --state-cache-size 0 --prometheus-external -- --port 30334 --chain /var/lib/amplitude/kusama.json --execution=wasm -d /var/lib/pendulum/ --prometheus-external
```

### Pre-compiled binary

Navigate to the Pendulum Download page:

[https://downloads.pendulumchain.tech/index.html](https://downloads.pendulumchain.tech/index.html)&#x20;

<figure><img src="../../../../.gitbook/assets/image (2).png" alt="" width="563"><figcaption></figcaption></figure>

the latest binary package is located in **pendulum\_binary\_latest** folder.

Download the binary file and replace it with the binary you are currently running on your system.

***

## Amplitude Nodes

### Introduction

Node upgrades are required for all collators when a new node version is released. It is very important that all nodes on the network maintain the same node version.

We provide our partners with the following installables.

* Docker Image
* .deb Ubuntu package for Ubuntu 20/22
* Precompiled binary

### Docker image

The official Amplitude docker image is located in [https://hub.docker.com/repository/docker/pendulumchain/amplitude-collator/general](https://hub.docker.com/repository/docker/pendulumchain/amplitude-collator/general)

Always use the image with the “latest” tag when you upgrade, that will have the recently pushed docker image.

```javascript
docker pull pendulumchain/amplitude-collator:latest
```

### .deb package for Ubuntu amd64 20/22

Navigate to the Pendulum Download page:

[https://downloads.pendulumchain.tech/index.html](https://downloads.pendulumchain.tech/index.html)

The latest package provided for Ubuntu is located in **amplitude\_debian\_latest** folder.

<figure><img src="../../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Download the latest package onto your server using the following command, and replace **VERSION** with the version provided on the page.

```javascript
wget [<https://downloads.pendulumchain.tech/amplitude_debian_latest/amplitude_VERSION_amd64.deb>](<https://downloads.pendulumchain.tech/amplitude_debian_latest/amplitude_0.9.40-1_amd64.deb>)
```

Once you obtained the package, navigate into the directory where the file is and use the following command sentence to install/upgrade the product:

```yaml
sudo dpkg -i amplitude_VERSION_amd64.deb
sudo service amplitude status

● amplitude.service - amplitude
     Loaded: loaded (/etc/systemd/system/amplitude.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2023-09-14 10:03:08 UTC; 52ms ago
   Main PID: 1061 (amplitude-colla)
      Tasks: 4 (limit: 4620)
     Memory: 5.7M
        CPU: 26ms
     CGroup: /system.slice/amplitude.service
             └─1061 /usr/local/bin/amplitude-collator --collator --base-path /var/lib/amplitude --no-private-ipv4 --rpc-cors all --force-authoring --enable-offchain-indexing=true --ws-port 8844 --ws-max-connections 200 --port 30335 --rpc-port 9955 --chain /var/lib/amplitude/amplitude-spec-raw.json --execution=wasm --state-cache-size 0 --prometheus-external -- --port 30334 --chain /var/lib/amplitude/kusama.json --execution=wasm -d /var/lib/amplitude/ --prometheus-external
```

### Pre-compiled binary

Navigate to the Pendulum Download page:

[https://downloads.pendulumchain.tech/index.html](https://downloads.pendulumchain.tech/index.html)

The latest package provided for Ubuntu is located in **amplitude\_binary\_latest** folder.

<figure><img src="../../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

Download the binary file and replace it with the binary you are currently running on your system.
