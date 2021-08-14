# Prerequisites for reNgine

This document aims to provide detailed instructions on setting up and running the **reNgine**.


!!! info "Attention"
    If you wish to run reNgine on any debian Linux (like Ubuntu), there is a installation script that will ease your docker installation and does required setup for you. Consider using it. [Quick Installation](#quick-installation) You can skip prerequisites **if you are running Ubuntu**

This document is divided into 3 parts:

1. [Prerequisites](#prerequisites)

2. [Quick Installation](#quick-installation)

2. [reNgine Installation](#rengine-installation)


## Prerequisites

**reNgine** uses several scripts and tools, those tools or scripts rely on various tools to be installed like Go, Python, etc, and to avoid any dependency issues, we decided to use Docker. Using Docker will not only ease the dependency issues but will also ease the installation steps. As a penetration tester, you need not focus on solving the dependencies, installing required tools, etc. With few installation steps, you should be good to run **reNgine**.

**reNgine** requires 3 tools to be installed before you begin installing rengine. They are, docker, docker-compose and make utility.

### Docker
Docker provides very good documentation on how to install docker based on your Operating System. You can [follow the documentation here.](https://docs.docker.com/get-docker/)

#### Docker installation on Ubuntu/Linux Distributions

!!! warning
    The installation steps have been directly taken from [Docker Guide](https://docs.docker.com/engine/install/ubuntu/) with no modification.

* Update the `apt` package index and install the below packages

```
sudo apt-get update
```

```
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

* Add Docker official GPG key

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

* Use the following commands to setup the stable repository

```
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

* Finally install Docker Engine

```
sudo apt-get update && sudo apt-get install docker-ce docker-ce-cli containerd.io
```

* Test the Docker by running `docker` command on your console/terminal.

#### Docker installation on Windows

Docker requires [Docker Desktop](https://docs.docker.com/docker-for-windows/install/) to be installed on your Windows OS. Installing Docker Desktop is as easy as double clicking the `InstallDocker.msi` installer, [downloaded from here](https://hub.docker.com/editions/community/docker-ce-desktop-windows/).

#### Docker installation on Mac OS

Docker requires [Docker Desktop](https://docs.docker.com/docker-for-mac/install/) to be installed on your Mac OS. Follow the instruction from Docker hub to [install Docker on Mac OS](https://hub.docker.com/editions/community/docker-ce-desktop-mac/).

#### Docker installation on Windows WSL

Nick Janetakis has a well written blog and a Video guide on [how to install Docker on Windows Subsystem Linux](https://nickjanetakis.com/blog/a-linux-dev-environment-on-windows-with-wsl-2-docker-desktop-and-more). Please follow the video/blog guide on how to install Docker on WSL.

### Docker Compose

If you're running **Docker Desktop** you can skip installing `docker-compose` as `docker-compose` comes along with Docker Desktop. This applies for both Windows and Mac OS users.

If you're using Linux distributions or WSL, you will still need to install `docker-compose` and the [installation steps](https://docs.docker.com/compose/install) are similar.

#### Installing `docker-compose` on Linux systems

* Download the latest stable version of `docker-compose`

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

* Apply executable permission

```
sudo chmod +x /usr/local/bin/docker-compose
```

* Create a symbolic link

```
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

* Verify your installation by running

```
docker-compose --version
```

!!! info
    If `curl` is not working for some reason, there are [alternate installation steps](https://docs.docker.com/compose/install/#alternative-install-options) as well. You can use `pip` or install as a container. Follow the [alternate installation steps](https://docs.docker.com/compose/install/#alternative-install-options).

### make

#### make installation on Linux Distributions

Install the latest version of make using

```
sudo apt install make
```

Although it is optional, `build-essential` package can also be installed which contains `make` utility.

```
sudo apt install build-essential
```

## **reNgine** Installation

Installing **reNgine** on your favourite VPS or on your local machine is pretty straight forward process. Installation instruction for VPS and local machine is similar and same steps can be followed. If you have met all the above [Prerequisites](#prerequisites), you can begin installing **reNgine**.

* Let's begin by cloning the **reNgine**.

```
git clone https://github.com/yogeshojha/rengine
```

```
cd rengine
```

There are currently two different ways of installing **reNgine**.

* Using make
* Manually using `docker-compose`

 Using make is by far the easiest way to setup **reNgine** without encountering any errors. Using `docker-compose` is a tidious process and is only intended for development purpose. Unless otherwise you're developing **reNgine**, it is recommended that you use `make` to install **reNgine**. Installation steps using `docker-compose` can be found in Developer's section.

### dotenv file

Before we begin installing reNgine, it is necessary to make changes to the [dotenv](https://github.com/yogeshojha/rengine/blob/master/.env) file. You can edit the file using your favourite editor

```
nano .env
```

or

```
vim .env
```

The sample [.env](https://github.com/yogeshojha/rengine/blob/master/.env) file can be found [here](https://github.com/yogeshojha/rengine/blob/master/.env).

```
#
# General
#
COMPOSE_PROJECT_NAME=rengine

#
# SSL specific configuration
#
AUTHORITY_NAME=reNgine
AUTHORITY_PASSWORD=mySecurePassword
COMPANY=reNgine
DOMAIN_NAME=recon.example.com
COUNTRY_CODE=IN
STATE=Karnataka
CITY=Bangalore
```

### Generating SSL Certificates

reNgine runs on https unless otherwise used for development purpose. So using https is recommended. To generate the certificates you can use

```
make certs
```

!!! warning ""
    Please note, while running any `make` command, you must be inside the rengine/ directory.

### Build reNgine

To build the reNgine, use the following command

```
make build
```

The build process is a lengthy process and may take some time.

!!! info ""
    Thanks to [Baptiste MOINE](https://github.com/Creased) for sending the PR that made build process so much simpler.

### Run reNgine

Once the build process is successful, we're good to run reNgine. This can be done using below command

```
make up
```

**reNgine can now be accessed from https://127.0.0.1 or if you're on the VPS https://your_vps_ip_address**

### Registering an account

The recent upgrade bring authentication feature on reNgine. You will need to create a username and password in order to login to the reNgine.
To register reNgine, you will need to run the following command

```
make username
```

You will now be prompted with some personal details(optional), username and password. **We highly recommend that you set a strong password for reNgine.**

You may now login to the reNgine web portal using the username and password that you just provided.

## Checking logs

If you need to observe the logs, it can be done so by running the commmand

```
make logs
```

!!! note
    If you encounter any issues while setup or scan, we advice you to [raise an issue in Github](https://github.com/yogeshojha/rengine/issues) and attach the log. While raising any new issues on Github, it is also adviced that you to look for any open issues on Github as well.

## Stopping the reNgine

If you wish to stop the reNgine, it can be done so by using the command

```
make stop
```

## Restarting the reNgine

reNgine can be restarted using the command

```
make restart
```

## Removing all the reNgine Data

If you wish to delete all your recon data, it can be done using

!!! danger
    This is a irreversible process and once pruned, you may never get back your recon data.
    Use with caution.

```
make prune
```
