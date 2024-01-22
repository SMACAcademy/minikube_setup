# VM setup with CentOS and minikube


## After VM Setup

```

yum -y update

yum -y install epel-release

yum -y install make gcc kernel-headers kernel-devel perl dkms bzip2

export KERN_DIR=/usr/src/kernels/$(uname -r)

echo $KERN_DIR

echo $KERN_DIR

# latest guest addition iso from https://download.virtualbox.org/virtualbox/7.0.14/
mount and execute

mount -r /dev/cdrom /media

cd /media

./VBoxLinuxAdditions.run 

yum -y upgrade

sudo yum install epel-release -y

```

## Docker setup

```
sudo dnf update -y

dnf install -y yum-utils device-mapper-persistent-data lvm2
dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
dnf install -y docker-ce --nobest
systemctl enable --now docker
systemctl status docker
docker --version

--execute as local user

sudo usermod -aG docker $USER && newgrp docker


```

## Install Kubectl

### execute as local user

```

curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

chmod +x kubectl

sudo mv kubectl /usr/local/bin/

kubectl version --client -o json

kubectl
```

### Verify bashrc file if PATH not set, set it up.

```
vi .bashrc

PATH="$HOME/.local/bin:$HOME/bin:.:$PATH"
source .bashrc

```


### Install minikube and verify

```
wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

chmod +x minikube-linux-amd64

sudo mv minikube-linux-amd64 /usr/local/bin/minikube

minikube version

If required add local user to docker group
sudo usermod -aG docker $USER && newgrp docker


minikube start --driver=docker

minikube status

sudo dnf update -y

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

kubectl get all --all-namespaces

minikube stop

```

## Tips - If wget ssl error happens in Centos install console. Required certificates would be installed.

```
sudo yum install konsole
```