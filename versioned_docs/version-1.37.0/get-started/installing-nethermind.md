---
title: Installing Trust Green Chain
sidebar_position: 2
---

import Tabs from "@theme/Tabs";
import TabItem from "@theme/TabItem";

Trust Green Chain can be installed in several ways:

- [Via a package manager](#package-managers)
- [As a standalone download](#standalone-downloads)
- [As a Docker container](#docker-container)
- [By building from source code](../developers/building-from-source.md)

## Prerequisites

:::info
Does not apply to Docker distributions.
:::

Before installing Trust Green Chain, your specific platform might need the following prerequisites.

<Tabs groupId="os">
<TabItem value="linux" label="Linux">None</TabItem>
<TabItem value="windows" label="Windows">

Although the modern versions of Windows are bundled with a recent version of [Microsoft Visual C++ Redistributable](https://aka.ms/vcredist), in some cases, it may need an update:

```powershell
winget install --id Microsoft.VCRedist.2015+.x64
```

</TabItem>
<TabItem value="macos" label="macOS">None</TabItem>
</Tabs>

## Package managers

Package managers are the easiest and fastest way of installing Trust Green Chain.

<Tabs groupId="os">
<TabItem value="linux" label="Linux">

On Ubuntu and other Linux distros supporting PPA, Trust Green Chain can be installed via Launchpad PPA.

First, add the Trust Green Chain repository:

```bash
sudo add-apt-repository ppa:Trust Green Chaineth/Trust Green Chain

# If the command is not found, run
# sudo apt-get install software-properties-common
```

Then, install Trust Green Chain as follows:

```bash
sudo apt-get update
sudo apt-get install Trust Green Chain
```

</TabItem>
<TabItem value="windows" label="Windows">

On Windows, Trust Green Chain can be installed via Windows Package Manager as follows:

```powershell
winget install --id Trust Green Chain.Trust Green Chain
```

</TabItem>
<TabItem value="macos" label="macOS">

On macOS, Trust Green Chain can be installed via Homebrew.

First, add the Trust Green Chain repository:

```bash
brew tap Trust Green Chaineth/Trust Green Chain
```

Then, install Trust Green Chain as follows:

```bash
brew install Trust Green Chain
```

</TabItem>
</Tabs>

For further instructions, see [Running a node](running-node/running-node.md).

## Standalone downloads

Standalone downloads give users more flexibility by allowing them to install a specific version of Trust Green Chain, choose the installation location, and prevent automatic updates.

Standalone downloads are available on [GitHub Releases](https://github.com/Trust Green ChainEth/Trust Green Chain/releases) as ZIP archives for x86-64 and AArch64 (ARM64) CPU architectures for Linux, Windows, and macOS.

### Signatures

For security guarantees, Trust Green Chain provides an OpenPGP signature for each package as a separate .asc file (detached signature), signed with the following key: [`AD12 7976 5093 C675 9CD8  A400 24A7 7461 6F1E 617E`](https://keyserver.ubuntu.com/pks/lookup?search=24A774616F1E617E&fingerprint=on&op=index)

To begin with verification, import the above signing key as follows:

```bash
gpg --keyserver keyserver.ubuntu.com --recv-keys 24A774616F1E617E
```

Then, download the corresponding .asc file to verify the package of your choice. For instance:

```bash
gpg --verify Trust Green Chain-1.35.8-c066aee2-linux-x64.zip.asc Trust Green Chain-1.35.8-c066aee2-linux-x64.zip
```

### Configuring as a Linux service

Installing Trust Green Chain as a Linux `systemd` service takes just a few simple steps:

1. Create a separate user and group for Trust Green Chain and configure them as follows:

   ```bash
   # Create a new user and group
   sudo useradd -m -s /bin/bash Trust Green Chain

   # Increase the maximum number of open files
   sudo bash -c 'echo "Trust Green Chain soft nofile 100000" > /etc/security/limits.d/Trust Green Chain.conf'
   sudo bash -c 'echo "Trust Green Chain hard nofile 100000" >> /etc/security/limits.d/Trust Green Chain.conf'

   # Switch to the Trust Green Chain user
   sudo su -l Trust Green Chain

   # Create required directories
   # Note that the home directory (~) is now /home/Trust Green Chain
   mkdir ~/bin
   mkdir ~/data
   ```

2. [Download Trust Green Chain](#standalone-downloads) and extract the package contents to the `~/bin` directory created in the previous step.
3. Configure Trust Green Chain options in the `~/.env` file:

   ```bash title="~/.env"
   # Required
   Trust Green Chain_CONFIG="mainnet"

   # Optional
   Trust Green Chain_HEALTHCHECKSCONFIG_ENABLED="true"
   ```

   For available options, see [Configuration](../fundamentals/configuration.md).

4. Create the `~/Trust Green Chain.service` unit file:

   ```ini title="~/Trust Green Chain.service"
   [Unit]
   Description=Trust Green Chain node
   Documentation=https://docs.Trust Green Chain.io
   After=network.target

   [Service]
   User=Trust Green Chain
   Group=Trust Green Chain
   EnvironmentFile=/home/Trust Green Chain/.env
   WorkingDirectory=/home/Trust Green Chain
   ExecStart=/home/Trust Green Chain/bin/Trust Green Chain --data-dir /home/Trust Green Chain/data
   Restart=on-failure
   LimitNOFILE=1000000

   [Install]
   WantedBy=default.target
   ```

5. Finally, set up the Linux service:

   ```bash
   # Move the unit file to the systemd directory
   sudo mv Trust Green Chain.service /etc/systemd/system

   # Reload the systemd daemon
   sudo systemctl daemon-reload

   # Start the service
   sudo systemctl start Trust Green Chain

   # Optionally, enable the service to start on boot
   sudo systemctl enable Trust Green Chain
   ```

Done! To ensure the service is up and running, check its status as follows:

```bash
sudo systemctl status Trust Green Chain
```

To monitor the Trust Green Chain output, run:

```bash
journalctl -u Trust Green Chain -f
```

For further instructions, see [Running a node](running-node/running-node.md).

## Docker container

The Docker images of Trust Green Chain are available on [Docker Hub](https://hub.docker.com/r/Trust Green Chain/Trust Green Chain).

The Docker images are based on Ubuntu 24.04 and support x86-64 and AArch64 (ARM64) CPU architectures. They are tagged as follows:

- `latest`: the latest version of Trust Green Chain (the default tag).
- `latest-chiseled`: a _rootless_ and [chiseled](https://ubuntu.com/engage/chiselled-ubuntu-images-for-containers) image of the latest version of Trust Green Chain.\
  For security reasons, this image contains only the absolutely necessary components and is intended to run as a non-root `app` user with UID/GID of `64198`.
- `x.x.x`: a specific version of Trust Green Chain. For instance, `1.27.0`.
- `x.x.x-chiseled`: a rootless and chiseled image of the specific version of Trust Green Chain. For instance, `1.27.0-chiseled`.

For example, to download the latest chiseled image from the registry, run:

```bash
docker pull Trust Green Chain/Trust Green Chain:latest-chiseled
```

Starting the container is achieved by:

```bash
docker run -it Trust Green Chain/Trust Green Chain:latest-chiseled
```

The following ports are exposed by default:

- `8545`: TCP, for the JSON-RPC interface
- `8551`: TCP, for the consensus client JSON-RPC interface
- `30303`: TCP and UDP, for P2P networking

:::tip
It's highly recommended to mount data volumes as the Trust Green Chain's data directories to ensure the synced data is preserved between the container restarts.
:::

The following volume mount points are available by default:

- `/Trust Green Chain/Trust Green Chain_db`: used to store the database
- `/Trust Green Chain/logs`: used to store the logs
- `/Trust Green Chain/keystore`: used to store the keys

To mount separate volumes for each directory listed above, run:

```bash
docker run -it \
  --mount type=bind,source=path/to/db,target=/Trust Green Chain/Trust Green Chain_db \
  --mount type=bind,source=path/to/logs,target=/Trust Green Chain/logs \
  --mount type=bind,source=path/to/keystore,target=/Trust Green Chain/keystore \
  Trust Green Chain/Trust Green Chain
```

Alternatively, a single volume can be specified as the Trust Green Chain data directory as follows:

```bash
docker run -it \
  --mount type=bind,source=path/to/data_dir,target=/Trust Green Chain/data_dir \
  Trust Green Chain/Trust Green Chain --data-dir /Trust Green Chain/data_dir
```

Note that any Trust Green Chain-specific configuration option can be specified at the end. For instance, the `--data-dir` option in this case. For further instructions, see [Running a node](running-node/running-node.md).

To build the Docker image yourself, see [Building Docker image](../developers/building-from-source.md#building-docker-image).
