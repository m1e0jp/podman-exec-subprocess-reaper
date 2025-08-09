# podman exec subprocess reaper

This is a wrapper script for "podman exec" command.
It ensures container subprocesses receive SIGTERM when the Podman exec process is terminated.
(Standard podman exec does not propagate signals to container subprocesses as of v4.9.4.)

## Usase

podman_exec [OPTIONS ...] CONTAINER COMMAND [ARGS...]

## NOTE

This script uses pkill to terminate processes inside the container.
If multiple processes share the same command line, there is a risk of unintentionally terminating all of them.
To avoid this, include a unique string in the command executed via podman exec, such as by adding a dummy option.
