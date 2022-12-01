FROM mcr.microsoft.com/devcontainers/base:jammy

ADD nix-feature/ nix-feature/

RUN nix-feature/install.sh
RUN sudo apt install -y acl && sudo setfacl -k /tmp

ENV PATH="${PATH}:/root/.nix-profile/bin"
ENV USER=root

RUN nix-env -iA cachix -f https://cachix.org/api/v1/install
RUN echo "trusted-users = root vscode" | sudo tee -a /etc/nix/nix.conf
RUN cachix use devenv && nix-env -if https://github.com/cachix/devenv/tarball/v0.4