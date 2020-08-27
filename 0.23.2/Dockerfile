FROM ubuntu:18.04

# Change Timezone
ENV TZ=Asia/Seoul
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

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
RUN mkdir /root/.pip && \
    echo -e \
"[global]\n"\
"index-url=http://mirror.kakao.com/pypi/simple/\n"\
"trusted-host=mirror.kakao.com\n"\
"progress-bar=emoji"\
        > /root/.pip/pip.conf && \
    # pip3 install --upgrade pip && \
    pip3 install matplotlib && \
    pip3 install scikit-learn

# Add alias
RUN alias l="ls -alh --full-time" && \
    alias cls='clear'

# Define Workdir
WORKDIR /root

# Write maintainer information
LABEL maintainer="LIM HYUN SEOK <contact@loopback.kr>"
