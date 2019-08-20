FROM ubuntu:16.04

MAINTAINER Kia <kia@csie.io>

# Update apt
RUN dpkg --add-architecture i386 && \
    apt update -y && apt upgrade -y && \
    apt install -y \
    build-essential \ 
    libc6-dbg:i386 \
    libc6-dbg \
    libssl-dev \
    libffi-dev \
    gdb-multiarch \
    gcc-multilib \
    git \
    wget curl \
    vim \
    python3-dev \
    python-dev \
    python-pip \
    net-tools \
    strace ltrace \
    tmux \
    nasm \
    ruby \
    ruby-dev

# install ROPGadget
RUN pip install \
    capstone \
    ropgadget

# install pwntools
RUN pip install \
    pwntools && \
    pip install --upgrade pwntools

# install one_gadget
RUN gem install one_gadget

# install pwndbg pwngdb
RUN mkdir /root/tools && git clone https://github.com/pwndbg/pwndbg /root/tools/pwndbg && cd /root/tools/pwndbg && ./setup.sh && \
    cd /root/tools && git clone https://github.com/scwuaptx/Pwngdb.git &&   \
    cat /root/tools/Pwngdb/.gdbinit >> /root/.gdbinit && sed -i 's?source ~/peda/peda.py?# source ~/peda/peda.py?g' /root/.gdbinit && \
    sed -i 's?source ~/Pwngdb/?source ~/tools/Pwngdb/?g' /root/.gdbinit

# install some tools
RUN gem install seccomp-tools

# set tmux config
RUN cd /root && wget https://raw.githubusercontent.com/kia280/MyEnv/master/tmux/.tmux.conf


WORKDIR /root

CMD ["/bin/bash"]

