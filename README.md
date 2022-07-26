# devcontainer-go
Repository for creating Go devcontainer

Install VSCode [Dev Container CLI](https://github.com/devcontainers/cli#dev-container-cli)

```node
npm install -g @devcontainers/cli
```

Build the image

```shell
devcontainer build --workspace-folder=. --image-name=edgehub/devcontainer-go:v0.0.1 --platform=linux/amd64,linux/arm64 --push
```
