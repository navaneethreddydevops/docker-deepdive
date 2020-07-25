# docker-security

# Docker configuration 

```
vi etc/sysconfig/docker
```

# cgroups & namespaces 

limiting the cpu utilization by 20% by applying --cpu flag and memory by 500mb

```
docker run --rm -it --security-opt seccomp=unconfined --cpus="0.2" --memory="500m" docker.io/python
```

# Host Limits
/etc/systemd/system/

```
cat > /etc/systemd/system/my_limits.slice << "EOF"
Description=my slice for docker resources
[Slice]
CPUAccounting=true
CPUQuota=20%
MemoryAccounting=true
MemoryLimit=200M
EOF
systemctl daemon-reload
```
# Creating a docker to run with specific cgroup limits 

```
docker run -it --cgroup-parent=my_limit.slice docker.io/python
```
# To apply a different set of climits to run different container with different limits create a new limits file 

```
cat > /etc/systemd/system/second_limits.slice << "EOF"
Description=my slice for docker resources
[Slice]
CPUAccounting=true
CPUQuota=30%
MemoryAccounting=true
MemoryLimit=500M
EOF
systemctl daemon-reload
```
# Creating a docker to run with second specific cgroup limits

```
docker run -it --cgroup-parent=second_limits.slice docker.io/python   #This will have a different limits applied on it
```

# Docker Security seccomp

```
grep SECCOMP /boot/config-$(uname -r)
```
These all flags should have yes flag to have additional security of Docker with seccomp 
CONFIG_HAVE_ARCH_SECCOMP_FILTER=y
CONFIG_SECCOMP_FILTER=Y
CONFIG_SECCOMP=Y

# Unit file of Docker
```
sudo systemctl cat docker
```
# seccompfile

```
cat /etc/docker/seccomp.json
# Create a new secomp file and start the new docker start with seccomp applied
docker run --rm \
             -it \
             --security-opt seccomp=/etc/docker/secuirytseccomp.json \
             docker.io/python
```

# All systemcalls and configuration are explained well here 
```
https://docs.docker.com/engine/security/seccomp/
https://suraj.io/post/docker-seccomp-manual/
```