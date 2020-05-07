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

## Create /etc/docker directory.
mkdir /etc/docker

# Setup daemon.
# This configuration is recommended by K8s
cat > /etc/docker/daemon.json <<EOF
{
  "exec-opts": ["native.cgroupdriver=systemd"],
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "100m"
  },
  "storage-driver": "overlay2",
  "storage-opts": [
    "overlay2.override_kernel_check=true"
  ]
}
EOF

mkdir -p /etc/systemd/system/docker.service.d

# Restart Docker
systemctl daemon-reload
systemctl restart docker
```

Says the [Kubernetes official site](https://kubernetes.io/docs/setup/production-environment/container-runtimes/):
> Changing the settings such that your container runtime and kubelet use `systemd` as the cgroup driver stabilized the system.

## Installing kubeadm, kubelet and kubectl on CentOS

```bash
cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-\$basearch
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
exclude=kubelet kubeadm kubectl
EOF

# Set SELinux in permissive mode (effectively disabling it)
setenforce 0
sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config

dnf install -y kubelet kubeadm kubectl --disableexcludes=kubernetes

systemctl enable --now kubelet
```
