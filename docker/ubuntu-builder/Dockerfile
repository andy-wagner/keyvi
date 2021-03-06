FROM ubuntu:16.04

# install packages required by pyenv
RUN set -ex \
    && apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y git  make build-essential libssl-dev zlib1g-dev libbz2-dev \
    libreadline-dev libsqlite3-dev \
    wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev \
    && rm -rf /var/lib/apt/lists/*

# install packages required by keyvi
RUN set -ex \
    && apt-get update \
    && apt-get install -y cmake g++ libboost-all-dev libsnappy-dev libzzip-dev zlib1g-dev clang clang-format-6.0 doxygen \
    && rm -rf /var/lib/apt/lists/*

RUN update-alternatives --install /usr/bin/clang-format clang-format /usr/bin/clang-format-6.0 1000

# install pyenv
RUN curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
ENV PATH "/root/.pyenv/shims/:/root/.pyenv/bin:$PATH"

# install python versions
RUN pyenv install 2.7.16
RUN pyenv install 3.5.7
RUN pyenv install 3.6.9
RUN pyenv install 3.7.4
RUN pyenv install 3.8.0
RUN pyenv install pypy2.7-7.2.0
RUN pyenv install pypy3.6-7.2.0

# install rust
RUN curl https://sh.rustup.rs -sSf | sh -s -- --default-toolchain stable -y
ENV PATH "~/.cargo/bin:$PATH"
