# TODO
* [ ] Tweak the registration to remove all manual steps. Or at least most manual steps. Potentially even include a base config.toml in the git repo itself.
* [ ]  Setup secret management for loggin into a docker repo.

# Purpose

* This creates a gitlab runner that can be utilized to build / push docker images.
* The runner is setup with privledge mode turned on.

# Setup Instructions

* Register runner

```bash
docker run --rm -t -i -v /srv/gitlab-runner/config:/etc/gitlab-runner gitlab/gitlab-runner register
```

* Update config.toml

```
privledged = true
cache_dir = "cache"
volumes = ["/var/run/docker.sock:/var/run/docker.sock", "/cache"]
```

# Utilization

* Start Runner

```bash
docker-compose up
```

* Stop Runner

```bash
docker-compose down
```

