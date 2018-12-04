FROM ubuntu:16.04
LABEL maintainer="Boilertalk Ltd"
LABEL Description="Docker Container for Vapor applications"

# Setup Vapor apt repository
RUN apt-get -q update && \
    apt-get -q install -y wget && \
    /bin/bash -c "$(wget -qO- https://apt.vapor.sh)"

# Instal Swift and related packages
RUN apt-get -q install -y swift vapor cmysql ctls

# Print Installed Swift Version
RUN swift --version

# Print Installed Vapor Version
RUN vapor --version

