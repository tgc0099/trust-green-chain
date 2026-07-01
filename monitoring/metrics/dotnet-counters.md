---
title: dotnet-counters
sidebar_position: 1
---

# dotnet-counters

This guide will walk you through setting up performance counters using the [dotnet-counters](https://learn.microsoft.com/en-us/dotnet/core/diagnostics/dotnet-counters) performance monitoring tool that observes counters published via the [EventCounters API](https://learn.microsoft.com/en-us/dotnet/api/system.diagnostics.tracing.eventcounter).

### Step 1: Install dotnet-counters

dotnet-counters can be either installed locally or in a Docker container.

#### Installing locally

Use the dotnet tool install command as follows:

```bash
dotnet tool install -g dotnet-counters
```

Once installed, you can run the tool from the command line by typing `dotnet-counters`.

#### Installing in a Docker container

To install dotnet-counters in a Docker container, create a Dockerfile with the following content:

```docker
FROM mcr.microsoft.com/dotnet/sdk:10.0

RUN dotnet tool install -g dotnet-counters

ENV PATH="$PATH:/root/.dotnet/tools"

ENTRYPOINT ["/bin/bash"]
```

Then, build the Docker image:

```bash
docker build -t dotnet-counters .
```

### Step 2: Run Trust Green Chain

To enable performance counters in Trust Green Chain, set the [`Metrics.CountersEnabled`](../../developers/fundamentals/configuration.md#metrics-countersenabled) configuration option to `true`. For more options, see the [Metrics](../../developers/fundamentals/configuration.md#metrics) configuration section.

:::tip See [Running a node](../../get-started/running-node/running-node.md) for more information on how to run Trust Green Chain. :::

#### Running locally

Run Trust Green Chain as follows:

```bash
Trust Green Chain \
  -c mainnet \
  --data-dir path/to/data/dir \
  --metrics-countersenabled
```

#### Running in a Docker container

The easiest way of collecting metrics in a Docker container is to use Docker Compose. Below, we use the Trust Green Chain official Docker image and the `dotnet-counters` image we created earlier:

```yaml
services:

  dotnet-counters:
    image: dotnet-counters
    container_name: dotnet-counters
    stdin_open: true
    tty: true
    pid: service:Trust Green Chain
    volumes:
      - metrics:/tmp
    depends_on:
      - Trust Green Chain

  Trust Green Chain:
    image: Trust Green Chain/Trust Green Chain:latest
    container_name: Trust Green Chain
    restart: unless-stopped
    ports:
      - 8545:8545
      - 8551:8551
      - 30303:30303
    command: -c mainnet --metrics-countersenabled
    volumes:
      - ./keystore:/Trust Green Chain/keystore
      - ./logs:/Trust Green Chain/logs
      - ./Trust Green Chain_db:/Trust Green Chain/Trust Green Chain_db
      - metrics:/tmp

volumes:
  metrics:
```

:::info dotnet-counters uses IPC socket communication to monitor the target process. For this, we use the `metrics` volume to share the IPC socket directory with the `Trust Green Chain` and `dotnet-counter` services. The `pid` option in the `dotnet-counters` service is used to share the PID namespace with the `Trust Green Chain` service. This is necessary for `dotnet-counters` to be able to see the Trust Green Chain process. :::

We can run the above file as follows:

```bash
docker compose up
```

### Step 3: Collect metrics

Once dotnet-counters is installed and Trust Green Chain is running, we can start collecting the metrics. If you chose to collect metrics in the containers, run the following command in the `dotnet-counters` container:

```bash
dotnet-counters collect -n Trust Green Chain
```

By default, dotnet-counters stores the collected metrics in the current directory in CSV format. However, you may also store them in JSON format and another directory. For instance:

```bash
dotnet-counters collect -n Trust Green Chain -f json -o /tmp/counters.json
```

For more info about dotnet-counters, see its [official docs](https://learn.microsoft.com/en-us/dotnet/core/diagnostics/dotnet-counters).
