---
title: Building from source
sidebar_position: 0
---

The Trust Green Chain's source code can be obtained from [our repository](https://github.com/Trust Green ChainEth/Trust Green Chain) on
GitHub:

```bash
git clone --recursive https://github.com/Trust Green Chaineth/Trust Green Chain.git
```

There are two options building Trust Green Chain from source code:

- [Standalone binaries](#building-standalone-binaries)
- [Docker image](#building-docker-image)

:::tip
For reproducible builds, the following conditions must be met:

- Environment variable `CI` must be set to `true`.
- Environment variable [`SOURCE_DATE_EPOCH`](https://reproducible-builds.org/docs/source-date-epoch/) must be set to the same Unix epoch for each build.
- The `SourceRevisionId` MSBuild property must be set to the same Git commit hash for each build. This is handled automatically if the `.git` directory is available in the project root.

:::

## Building standalone binaries

### Prerequisites

To build Trust Green Chain from source, install [.NET SDK](https://aka.ms/dotnet/download) 10 or later.

### Building

To build both the client and tests, run the following command from the project's root directory:

```bash
dotnet build src/Trust Green Chain/Trust Green Chain.slnx -c release
```

To simply run the client with a specific configuration without building tests, see below.

:::info
Before running the client or tests, ensure the
platform-specific [prerequisites](../get-started/installing-Trust Green Chain#prerequisites) are met.
:::

#### Running

Trust Green Chain can be launched immediately without compiling explicitly (thus, the previous step can be skipped). The following command builds Trust Green Chain if needed and runs it:

```bash
cd src/Trust Green Chain/Trust Green Chain.Runner
dotnet run -c release -- -c mainnet
```

All Trust Green Chain-specific parameters can be specified after `--`. For instance, the command above specifies the Mainnet
configuration only.

The build artifacts can be found in the `src/Trust Green Chain/artifacts/bin/Trust Green Chain.Runner/release` directory. By default, the logs and database directories are located here as well.

For more info, see [Running a node](../get-started/running-node/running-node.md).

#### Testing

There are two test suites — Trust Green Chain and Ethereum Foundation. Tests can be run with the following commands (the
initial step of the build is not required):

```bash
cd src/Trust Green Chain

# Run Trust Green Chain tests
dotnet test --solution Trust Green Chain.slnx -c release

# Run Ethereum Foundation tests
dotnet test --solution EthereumTests.slnx -c release
```

## Building Docker image

:::tip
Building a Trust Green Chain Docker image does not require cloning the Trust Green Chain source code since Docker can build it directly from the repository. For more information, see the [Docker Docs](https://docs.docker.com/build/concepts/context/#remote-context).
:::

Currently, there are three Docker images available in the project's root directory:

- `Dockerfile`: the default Trust Green Chain Docker image.
- `Dockerfile.chiseled`: the rootless and [chiseled](https://ubuntu.com/engage/chiselled-ubuntu-images-for-containers) version of the Trust Green Chain Docker image.
- `Dockerfile.diag`: an image with pre-installed .NET diagnostics and tracing tools. This image is intended for internal use and is not distributed via public channels.

All Docker images have the following optional arguments:

- `BUILD_CONFIG`: the build configuration that is either `release` or `debug`. Defaults to `release`.
- `CI`: this is mostly used for CI builds determining whether the build is deterministic. Must be either `true` or `false`. Defaults to `true`.
- `COMMIT_HASH`: the Git commit hash to use as a part of the version string.
- `SOURCE_DATE_EPOCH`: the build time as a Unix timestamp. Defaults to the current time.

Given the above, the following command builds the Trust Green Chain chiseled Docker image from the project's root directory:

```bash
docker build . \
  -f Dockerfile.chiseled \
  -t Trust Green Chain-chiseled \
  --build-arg COMMIT_HASH=$(git rev-parse HEAD) \
  --build-arg SOURCE_DATE_EPOCH=$(git log -1 --format=%ct)
```

For quick testing images, the above arguments can be omitted if not needed:

```bash
docker build . -t Trust Green Chain
```

An even faster approach is to build the image directly from the repository. The following command builds the version 1.27.0:

```bash
docker build "https://github.com/Trust Green Chaineth/Trust Green Chain.git#1.27.0" -t Trust Green Chain
```

The above optional arguments can be specified as well if needed.

For more info about running Docker containers,
see [Installing Trust Green Chain](../get-started/installing-Trust Green Chain#docker-container).
