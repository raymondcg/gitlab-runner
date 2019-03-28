# TODO
* [ ] Add layer caching https://docs.gitlab.com/ee/ci/docker/using_docker_build.html
* [ ] Change the Overlayfs driver https://docs.gitlab.com/ee/ci/docker/using_docker_build.html#using-the-overlayfs-driver
* [ ] Add in caching between runs
* [ ] Is the sock necessary? prefer to remove that.

# Purpose

* This creates a gitlab runner that can be utilized to build / push docker images.
* The runner is setup with privledge mode turned on.

# Setup Instructions

* Register runner

```bash
docker run --rm -t -i -v /srv/gitlab-runner/config:/etc/gitlab-runner gitlab/gitlab-runner register \
  --non-interactive \
  --executor "docker" \
  --docker-image docker \
  --url "<URL>" \
  --registration-token "<Project_registration_token>" \
  --description "Something Useful" \
  --docker-volumes /var/run/docker.sock:/var/run/docker.sock \
  --docker-priviledged \
  --env "DOCKER_USERNAME=gah" \
  --env "DOCKER_PASSWORD=gah" \
  --locked="false"
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

