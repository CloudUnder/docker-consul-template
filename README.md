# Docker Consul Template

More information will follow soon.

## Usage examples

```
docker run --rm cloudunder/consul-template -version
```

```
docker run \
    --rm \
    --link consul:consul \
    -v /on/the/host/nginx.ctmpl:/templates/nginx.ctmpl:ro \
    cloudunder/consul-template -consul consul:8500 -template="/templates/nginx.ctmpl:/output/default.conf" -dry -once
```

```
docker run \
    -d \
    --name consul_template \
    -v /on/the/host/nginx.ctmpl:/templates/nginx.ctmpl:ro \
    -v /on/the/host/output:/output:rw \
    -v /var/run/docker.sock:/var/run/docker.sock \
    --link consul:consul \
    cloudunder/consul-template -consul consul:8500 -template="/templates/nginx.ctmpl:/output/default.conf:docker kill -s HUP nginx || true"
```
