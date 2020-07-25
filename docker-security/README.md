# docker-security

# Docker configuration 

```
vi etc/sysconfig/docker
```

# cgroups & namespaces 

```
liminiting the cpu utilization by 20% by applying --cpu flag and memory by 500mb
docker run --rm -it --security-opt seccomp=unconfined --cpus="0.2" --memory="500m" docker.io/python
```

