ARG PSCALE_VERSION
ARG VARIANT

FROM mcr.microsoft.com/vscode/devcontainers/typescript-node:${VARIANT}

RUN echo ${PSCALE_VERSION}
RUN echo ${VARIANT}

# [Install a mysql-client so we can query locally
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends default-mysql-client

# [Optional] Uncomment if you want to install an additional version of node using nvm
# ARG EXTRA_NODE_VERSION=10
# RUN su node -c "source /usr/local/share/nvm/nvm.sh && nvm install ${EXTRA_NODE_VERSION}"

# [Optional] Uncomment if you want to install more global node modules
# RUN su node -c "npm install -g <your-package-list-here>"

# Enable pnpm
RUN corepack enable

# Grab the pscale CLI
RUN sudo wget "https://github.com/planetscale/cli/releases/download/v0.125.0/pscale_0.125.0_linux_amd64.deb" && \
    sudo dpkg -i pscale_0.125.0_linux_amd64.deb