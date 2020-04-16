# docker-k8s-notes

## Docker Installation on CentOS
Execute the commands as `root` or prefix commands with `sudo`.

```bash
# Install Docker CE
## Set up the repository
### Install required packages.
dnf install -y dnf-utils device-mapper-persistent-data lvm2

### Add Docker repository.
dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo

## Install Docker CE.
dnf install -y \
  https://download.docker.com/linux/centos/7/x86_64/stable/Packages/containerd.io-1.2.13-3.1.el7.x86_64.rpm \
  docker-ce \
  docker-ce-cli
```