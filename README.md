# Edgenesis VSCode Development Container for Go

Repository for creating Go devcontainer

For reference: [devcontainer feature repo](https://github.com/devcontainers/features)

Install VSCode [Dev Container CLI](https://github.com/devcontainers/cli#dev-container-cli)

```node
npm install -g @devcontainers/cli
```

Build the image

```shell
devcontainer build --workspace-folder=. --image-name=edgenesis/devcontainer-go:v0.0.1 --platform=linux/amd64,linux/arm64 --push
```
