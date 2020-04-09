# sops-helm-wrapper
Helm Wrapper with Sops written in Go, which decrypts encrypted value files with Sops 

## Installation

### Prerequisites
Helm is required for the wrapper to work: to install [helm](https://helm.sh/docs/intro/install/).
Make sure to add **Helm** to your *$PATH* for the wrapper to work.

### Build
you can build using the command.
```sh
$> go build
```
### Setup
This wrapper checks for Helm in *$PATH*.
If you decide to rename **sops-helm-wrapper** as Helm you can rename `helm` as `_helm` and make sure that **_helm** path in in you **$PATH

## Usage

Create a secrets values file `secrets.yaml` and encrypt it with [sops](https://github.com/mozilla/sops/)

Use the wrapper to decrypt:

```sh
$> sops-helm-wrapper template . --values ./secrets.yaml`
```

or

```sh
$> helm template . --values ./secrets.yaml
```

if you are using the wrapper as helm.

## How it Works

The wrapper uses [sops](https://github.com/mozilla/sops/) `decrypt.go` to decrypt any encrypted values file before invoking helm 

### Note 
Encrypted values must match the following RegEx: 
```
"^((?:.*/)?secrets(?:(?:-|\\.|_).+)?.yaml)$"
```

