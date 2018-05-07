# ubuntu-init


Ubuntu bionic with init systemd running without the --privileged option.

You can run it privileged too.

e.g. service myservice start , in docker

## Usage

* Start an ubuntu server without privileges
  init runs, but you have to start services
  uuidd doesn't run.

```bash
docker run --name init-server -d --tmpfs /tmp --tmpfs /run -v /sys/fs/cgroup:/sys/fs/cgroup:ro danielguerra/ubuntu-init
```

* Start an ubuntu with SYS_ADMIN capability
  init runs, but you have to start services
  uuidd runs.

```bash
docker run --cap-add=SYS_ADMIN --name init-server -d --tmpfs /tmp --tmpfs /run -v /sys/fs/cgroup:/sys/fs/cgroup danielguerra/ubuntu-init
```

* Start an ubuntu with --privileged
  init runs, services start automatic
  uuidd runs.

```bash
docker run --privileged --name init-server -d  danielguerra/ubuntu-init
```

* Get a terminal on the init host

```bash
docker exec -ti init-server bash
```
--cap-add=SYS_ADMIN -e "container=docker" -v /sys/fs/cgroup:/sys/fs/cgroup
