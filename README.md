# Usase
podman_exec [OPTIONS ...] CONTAINER COMMAND [ARGS...]

This is a wrapper script for "podman exec" command. 
It ensures container subprocesses receive SIGTERM when the Podman exec process is terminated.
(Standard podman exec does not propagate signals to container subprocesses as of v4.9.4.)

NOTE:
Process termination is handled via pkill.
Therefore, when used with generic command lines like `bash`,
there is a risk of inadvertently affecting other processes.
