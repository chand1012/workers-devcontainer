FROM ubuntu:20.04

# set to noninteractive
ENV DEBIAN_FRONTEND=noninteractive

# set timezone to newyork
ENV TZ=America/New_York

# set user name
ENV USER=rusty

# install packages
# and clear apt cache
RUN apt-get update && apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common \
    git \
    build-essential && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# create a new user
RUN useradd -m -s /bin/bash -G sudo rusty

# make sure the user can sudo without a password
RUN echo "rusty ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# make user UID 1000
RUN usermod -u 1000 rusty

# set the hostname
RUN echo "workers" > /etc/hostname

# switch to user
USER rusty

# install rust
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y

# set back to interactive
ENV DEBIAN_FRONTEND=dialog