# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.238.1/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version (use ubuntu-22.04 or ubuntu-18.04 on local arm64/Apple Silicon): ubuntu-22.04, ubuntu-20.04, ubuntu-18.04
ARG VARIANT="jammy"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# Install openvpn client
RUN export DEBIAN_FRONTEND=noninteractive && apt-get update \
    && apt-get -y install --no-install-recommends openvpn \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/library-scripts \
    #
    # Remove the OPENVPN_CONFIG variable since we don't neeed it after is written to a file 
    && echo 'OPENVPN_CONFIG=""' >> /etc/environment \
    && echo "unset OPENVPN_CONFIG" | tee -a /etc/bash.bashrc > /etc/profile.d/999-unset-openvpn-config.sh \
    && if [ -d "/etc/zsh" ]; then echo "unset OPENVPN_CONFIG" >> /etc/zsh/zshenv; fi
