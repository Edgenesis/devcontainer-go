# [Choice] Go version (use -bullseye variants on local arm64/Apple Silicon): 1, 1.18, 1.17, 1-bullseye, 1.18-bullseye, 1.17-bullseye, 1-buster, 1.18-buster, 1.17-buster
ARG VARIANT=1-bullseye
FROM golang:${VARIANT}

# Copy library scripts to execute
COPY script-library/*.sh script-library/*.env /tmp/library-scripts/

ENV GO111MODULE=auto
ENV DOCKER_BUILDKIT=1
RUN bash /tmp/library-scripts/common-debian.sh \
    && bash /tmp/library-scripts/go-debian.sh "none" \
    && bash /tmp/library-scripts/install-dapr-tools.sh \
    && bash /tmp/library-scripts/docker-debian.sh \
    && bash /tmp/library-scripts/kubectl-helm-debian.sh "latest" "latest" "none" \
    && bash /tmp/library-scripts/python-debian.sh "os-provided" \
    && bash /tmp/library-scripts/github-debian.sh "latest" \
    # && apt-get install -y protobuf-compiler \
    && apt-get install -y libpcap-dev python-is-python3 \
    && apt-get autoremove -y && apt-get clean -y && rm -rf /var/lib/apt/lists/* \
    && echo "source /etc/bash_completion" >> "/root/.bashrc" \
    && echo "source <(kubectl completion bash)" >> "/root/.bashrc"

ENV GOPRIVATE=github.com/Edgenesis,edgenesis.io/shifu
ARG KIND_VERSION="v0.16.0"

RUN curl -Lo ./kind https://kind.sigs.k8s.io/dl/${KIND_VERSION}/kind-linux-$(go env GOARCH) \
     && chmod +x ./kind \
     && mv ./kind /usr/local/bin/kind \
     && curl -Lo ./kubebuilder https://go.kubebuilder.io/dl/latest/$(go env GOOS)/$(go env GOARCH) \
     && chmod +x ./kubebuilder \ 
     && mv ./kubebuilder /usr/local/bin/kubebuilder

ENTRYPOINT ["/usr/local/share/docker-init.sh"]
CMD ["sleep", "infinity"]