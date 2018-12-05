FROM ubuntu:16.04
LABEL maintainer="Boilertalk Ltd"
LABEL Description="Docker Container for Vapor applications"

# Setup Vapor apt repository
RUN apt-get -q update && \
    apt-get -q install -y wget && \
    /bin/bash -c "$(wget -qO- https://apt.vapor.sh)"

# Instal Vapor related packages
RUN apt-get -q install -y cmysql ctls

# Install swift run-time dependencies
RUN apt-get -qq -y install lsb-release curl git libicu55 libxml2 libcurl4-openssl-dev libc6-dev clang

# Install swiftenv
ENV SWIFTENV_ROOT /usr/local
ADD https://github.com/kylef/swiftenv/archive/1.4.0.tar.gz /tmp/swiftenv.tar.gz
RUN tar -xzf /tmp/swiftenv.tar.gz -C /usr/local/ --strip 1

# Add swiftenv shims to PATH
ENV PATH /usr/local/shims:$PATH

# Install swift
RUN swiftenv install https://swift.org/builds/swift-4.2.1-release/ubuntu1604/swift-4.2.1-RELEASE/swift-4.2.1-RELEASE-ubuntu16.04.tar.gz
RUN swiftenv global 4.2.1-RELEASE

# Uninstall unneeded packages
RUN apt-get -q remove -y --auto-remove curl wget

# Print installed swiftenv Version
RUN swiftenv --version

# Print installed Swift Version
RUN swift --version
