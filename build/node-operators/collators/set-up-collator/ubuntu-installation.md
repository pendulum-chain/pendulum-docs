# Ubuntu Installation

This guide will describe how to install and run a Collator node on an Ubuntu machine.\


## Install Collator node using the Ubuntu deb package installer.

Pendulum and amplitude is now available as an ubuntu installable package. The installer was tested on ubuntu 20 LTS and Ubuntu 22 LTS.

Visit [https://downloads.pendulumchain.tech/index.html](https://downloads.pendulumchain.tech/index.html) and locate the latest image under

Pendulum: **pendulum\_debian\_latest**,

Amplitude: **amplitude\_debian\_latest**

download the relevant installation package then install it with the following command:

```bash
sudo dpkg -i pendululum(version)_amd64.deb
- OR -
sudo dpkg -i ampitude(version)_amd64.deb
```

This installs the Pendulum collator. Once the installer is finished check if the **pendulum** service is running:

```bash
root@localhost:~# service pendulum status
● pendulum.service - pendulum
     Loaded: loaded (/etc/systemd/system/pendulum.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2023-03-09 11:36:20 UTC; 14min ago
   Main PID: 1090301 (pendulum-collat)
      Tasks: 18 (limit: 19015)
     Memory: 8.0G
     CGroup: /system.slice/pendulum.service
             └─1090301 /usr/local/bin/pendulum-collator --collator --no-private-ipv4 --rpc-cors all --force-authoring --enable-offchain-indexing=true --ws-p>

Mar 09 11:36:20 pencol-kus-03 systemd[1]: Starting pendulum...
Mar 09 11:36:20 pencol-kus-03 systemd[1]: Started pendulum.
```

The service will use the **/var/lib/pendulum** directory as the database location and the log files are located in **/var/log/pendulum** directory.

### Firewall Config

Configure your local firewall to allow communication for the required ports

```bash
sudo ufw allow 30335/tcp
sudo ufw allow 30334/tcp
sudo ufw allow https
sudo ufw enable
```
