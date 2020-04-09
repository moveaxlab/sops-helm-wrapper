# sops-helm-wrapper
Helm Wrapper with Sops written in Go, which decrypts encrypted value files with Sops 

## Installation

### Prerequisites
Helm is required for the wrapper to work, to install [helm](https://helm.sh/docs/intro/install/).
make sure to add **Helm** to your *$PATH* for the wrapper to work.
## build
you can build using the `go build` command.
 `go build .`
## Usage
**Setup Binary**
the wrapper checks for Helm in $PATH , or you can rename helm binary `/usr/local/bin/_helm`, and Use/Export **sops-helm-wrapper** as Helm.

create a secrets values file *-secrets.yaml OR secrets.yaml and encrypt it with [sops](https://github.com/mozilla/sops/)
to decrypt
`sops-helm-wrapper template . --values helm_vars/values.yaml --values helm_vars/secrets.yaml`
or
`helm template . --values helm_vars/values.yaml --values helm_vars/secrets.yaml`   **if using t

## How it Works
The wrapper uses [sops](https://github.com/mozilla/sops/) decrypt.go to decrypt any encrypted values file before invoking helm 
(encrypted values has to be named secrets.yaml *secrets*.yaml)

