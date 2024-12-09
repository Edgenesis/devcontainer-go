ARG VARIANT="dev-1"
FROM mcr.microsoft.com/devcontainers/go:${VARIANT}

ARG KIND_VERSION="v0.25.0"

RUN curl -Lo ./kind https://kind.sigs.k8s.io/dl/${KIND_VERSION}/kind-linux-$(go env GOARCH) \
     && chmod +x ./kind \
     && mv ./kind /usr/local/bin/kind \
     && curl -Lo ./kubebuilder https://go.kubebuilder.io/dl/latest/$(go env GOOS)/$(go env GOARCH) \
     && chmod +x ./kubebuilder \ 
     && mv ./kubebuilder /usr/local/bin/kubebuilder
RUN apt update && apt install -y libpcap-dev && rm -rf /var/lib/apt/lists/*
