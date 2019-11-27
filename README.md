# aksctl
![GitHub All Releases](https://img.shields.io/github/downloads/adfolks/aksctl/total)  ![GitHub](https://img.shields.io/github/license/adfolks/aksctl)  ![GitHub closed pull requests](https://img.shields.io/github/issues-pr-closed/adfolks/aksctl)  ![GitHub closed issues](https://img.shields.io/github/issues-closed/adfolks/aksctl)  ![GitHub issues](https://img.shields.io/github/issues/adfolks/aksctl)  [![Go Report Card](https://goreportcard.com/badge/github.com/adfolks/aksctl)](https://goreportcard.com/report/github.com/adfolks/aksctl)
 `aksctl` is an easy to use CLI(Command Line Utility) for creating and managing Kubernetes Cluster on Azure AKS ( Azure Kubernetes Service). It is written in Go.
## Getting Started
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.
### Prerequisites
You will need to have Azure credentials configured. What works for AZ CLI should be sufficient. If you dont have Azure CLI installed, you can refer [here](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
### Installation
#### Option 1:
To install aksctl from source code with building by yourself, clone the repository using:
```bash
git clone https://github.com/adfolks/aksctl
```
Then, initiate module with:
```bash
go mod init github.com/adfolks/aksctl
```
This will create a module config file `go.mod`.
Finally, use
```bash
go build
```
to fetch the latest dependencies.

#### Option 2:
To install aksctl on linux bash from release binary:
```bash
release=v0.1.0 ## choose the available release version
curl --silent --location "https://github.com/adfolks/aksctl/releases/download/$release/aksctl-$(uname -s)-amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/aksctl /usr/local/bin
```

## Basic usage
 A default cluster can be created by running:
  ```bash
     aksctl create cluster
  ```
  This command will be using values from `default.yaml` located at the root directory,
  edit `default.yaml` with reference to keys from `template.yaml` for specifying more parameters
  A cluster's mandatory parameters can be overridden using flags while running the command.
  ```bash
     aksctl create cluster --name
                           --rgroupname
                           --rgroupregion
  ```
  Example:
  Running the code
  ```bash
     aksctl create cluster --rgroupname myresourcegroup
  ```
  Flags can be used with shorthand name as well
  ```bash
     aksctl create cluster -r myresourcegroup
  ```
  above code will create a resource group with the name `myresourcegroup`.
  You can also customize your cluster by using a config file.
  For this, create a `.yaml` a file like `config.yaml` with reference to keys from `template.yaml`.
  Next, run the command:
  ```bash
     aksctl create cluster --file config
  ```
  to apply the `config.yaml` file.
  This will create a cluster as described in the file.
A cluster can be deleted by running:
  ```bash
      aksctl delete cluster
  ```
Get the list of clusters by running:
  ```bash
     aksctl get cluster
  ```
`aksctl` can be installed by following the above instructions.
Check [aksctl.io](https://www.aksctl.io) to learn more about what aksctl can do and its features.
## Built With
* Go
