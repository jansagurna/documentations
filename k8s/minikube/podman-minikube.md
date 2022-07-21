## Install Minikube with Podman M1

With this tutorial you can install Minikube with Podman and delete it again

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.
* HomeBrew
  ```sh
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```
* Podman
  ```sh
  brew install podman
  ```
* Minikube
  ```sh
  brew install minikube
  ```
### Installation

1. Configure Podman
   ```sh
   podman machine init --cpus 4 --memory 8192 --disk-size 80
   ```
2. Set Root Permissions
   ```sh
   npodman machine set --rootfull
   ```
3. Set Default Connection
   ```sh
   podman system connection default podman-machine-default-root
   ```
3. Start Minikube
   ```sh
   minikube start --cpus 4 --memory 7915 --disk-size=80G --driver=podman --network-plugin=cni --cni=auto
   ```
### Delete Enviroment

1. Delete Minikube Enviroment
   ```sh
   minikube delete --all --purge
   ```
2. Delete Podman Machine
   ```sh
   podman system prune -a --volumes
   ```