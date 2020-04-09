`howto` is a script for simplifying running commands from Docker and
Singularity images.

# Installation

First install Docker and/or Singularity. The `howto` script used
Singularity by default, but this can be override by setting the
following environment variable,

    export HOWTO_BACKEND=dockerw

The `howto` script is written in Perl and relies on a handful of
external libraries that should be part of the Perl core.

Just put the script somewhere on your `$PATH`.

# Configuration

The `howto` script looks for a YAML file that lists the known Docker
packages and the commands that each provide. The `howto` scripts looks
for the YAML file in each of these locations, in this order:

- The file specified with the `-f` argument.
- `./howto.yaml`
- `./.howto.yaml`
- `~/.howto.yaml`

An example YAML file, `howto.sample.yaml`, is provided here.

<!-- FIXME - document the YAML file content -->

# Usage

<!-- FIXME - expands this -->

The basic way to run a command that is provided by a container is,

    howto cmd arg1 arg2 ...

The script is able to map commands to containers using 'howto.yaml' (also attached).

Here's how it might work,

    # select the Docker backend; Singularity is the default
    export HOWTO_BACKEND=dockerw

    # pull all of the containers specified in howto.yaml. Both
    # Singularity and Docker containers are cached, so you should only
    # have to do this once.
    howto -p '*'

    # List all known commands (and their containers)
    howto -l

    # Run a command, in this case, `SearchGUI` from the
    # `pvstodghill/searchgui:3.2.6__2017-02-01`
    howto SearchGUI --help

    # List all of the options
    howto -h
