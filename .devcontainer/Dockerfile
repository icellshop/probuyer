FROM mcr.microsoft.com/devcontainers/base:ubuntu

RUN apt-get update && \
    apt-get install -y curl git unzip xz-utils zip libglu1-mesa libpq-dev && \
    rm -rf /var/lib/apt/lists/*

ENV FLUTTER_VERSION=3.19.3
RUN curl -O https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_${FLUTTER_VERSION}-stable.tar.xz && \
    tar xf flutter_linux_${FLUTTER_VERSION}-stable.tar.xz && \
    mv flutter /usr/local/flutter && \
    ln -s /usr/local/flutter/bin/flutter /usr/local/bin/flutter && \
    rm flutter_linux_${FLUTTER_VERSION}-stable.tar.xz

ENV PATH="/usr/local/flutter/bin:${PATH}"

RUN flutter precache --web && \
    flutter precache --android && \
    flutter precache --ios

RUN yes | flutter doctor --android-licenses || true

WORKDIR /workspaces/pro_buyer_app
