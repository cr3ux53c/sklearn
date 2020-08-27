FROM ubuntu:18.04

# Change default Shell to bash
SHELL ["/bin/bash", "-c"]

# Change Ubuntu repository address to DaumKaKao
RUN sed -i 's/archive.ubuntu.com/mirror.kakao.com/g' /etc/apt/sources.list

# Install essential packages
RUN apt update && \
    apt install -y \
        git \
        vim \
        tree \
        wget \
        zip \
        unzip \
        python3 \
        python3-pip

# Configure default Pypi repository address and default progress bar style
RUN mkdir ~/.pip && \
    echo -e \
"[global]\n"\
"index-url=http://mirror.kakao.com/pypi/simple/\n"\
"trusted-host=mirror.kakao.com\n"\
"progress-bar=emoji"\
        > ~/.pip/pip.conf && \
    # pip3 install --upgrade pip && \
    pip3 install scikit-learn && \
    pip3 install matplotlib numpy opencv-python

# Add alias
RUN alias l="ls -alh --full-time" && \
    alias cls='clear'

# Write maintainer information
LABEL maintainer="LIM HYUN SEOK <contact@loopback.kr>"
