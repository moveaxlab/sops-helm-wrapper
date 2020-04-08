# sops-helm-wrapper
Helm Wrapper with Sops written in Go, which decrypts encrypted value files with Sops 

## Installation

### Prerequisites
Helm is required for the wrapper to work, to install [helm](https://helm.sh/docs/intro/install/).

## build
you can build using the `go build` command.

## Usage
create ur secrets values file *-secrets.yaml OR secrets.yaml and encrypt it with [sops](https://github.com/mozilla/sops/)
to decrypt
sops-helm-wrapper template . --values helm_vars/values.yaml --values helm_vars/secrets.yaml
or
helm template . --values helm_vars/values.yaml --values helm_vars/secrets.yaml

## How it Works
The wrapper uses [sops](https://github.com/mozilla/sops/) decrypt.go to decrypt any encrypted values file before invoking helm 
(encrypted values has to be named secrets.yaml *secrets*.yaml)

