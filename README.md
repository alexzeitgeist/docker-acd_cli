# zeitgeist/docker-acdcli

[acd_cli](https://github.com/yadayada/acd_cli) in a Docker container.

## Requirements

* [Docker](https://www.docker.com/) 1.81+ (previous versions may work fine, but I haven't tried)

## Installation

Get the [trusted build on the docker hub](https://registry.hub.docker.com/u/zeitgeist/docker-acdcli/):

```bash
$ docker pull zeitgeist/docker-acdcli
```

or download and compile the source yourself from Github:

```bash
$ git clone https://github.com/alexzeitgeist/docker-acd_cli.git
$ cd docker-acd_cli
$ docker build -t zeitgeist/docker-acdcli .
```

## Usage

[acd_cli](https://github.com/yadayada/acd_cli) is a command line for read and write accessing Amazon Cloud Drive. Related instructions can be found on its project page.

Since the acd_cli cache directory contains the OAuth token to access your files, I highly recommend mapping a local directory as a volume to permanently store the contents of the acd_cli cache directory. Example:

```bash
$ docker run --rm \
  -v ~/.cache/acd_cli:/home/user/.cache/acd_cli \
  -v /tmp:/tmp \
  zeitgeist/docker-acdcli
```

## TIP

To simplify the commandline, set a bash alias in ~/.bash_aliases:

```bash
alias acd_cli="docker run --rm -v ~/.cache/acd_cli:/home/user/.cache/acd_cli -v /tmp:/tmp zeitgeist/docker-acdcli"
alias acdcli=acd_cli
```

Note: FUSE dependencies are not installed.
