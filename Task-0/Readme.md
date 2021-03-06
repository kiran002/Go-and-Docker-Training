# Task-0 : Setting up docker and golang

One of the first things to do before we get started, is to install all the tools we would need along the way. While this list is currently very basic. Over time as the material grows this is list is also expected to grow.

### Install docker-ce

[Installation Guide](https://www.docker.com/community-edition#/download)

### Install golang

[Guide](https://golang.org/doc/install)

```
curl -LO https://dl.google.com/go/go1.10.1.linux-amd64.tar.gz
tar xvf go1.10.1.linux-amd64.tar.gz
echo "export PATH=\$PATH:~/go/bin/" >> ~/.bash_profile
source ~/.bash_profile

```

### (Optional) IDE

[Installation link](https://www.jetbrains.com/go/) --> my preference

But you can also check out other IDE's available

[Official IDE list](https://github.com/golang/go/wiki/IDEsAndTextEditorPlugins)


### Install docker-compose

[Installation link](https://docs.docker.com/compose/install/)


### Minikube Installation

You only need this if you want to do the kubernetes task, You cannot run minikube if you are already running in a VM. Only Windows 10, Linux and mac os are supported


[Follow instructions here](https://kubernetes.io/docs/tasks/tools/install-minikube/)

