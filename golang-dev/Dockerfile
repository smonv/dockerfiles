FROM fedora:latest
MAINTAINER Tien Thanh <thanhvt1609@gmail.com>

RUN dnf install -y \
    git \
    gcc \
    gcc-c++ \
    kernel-devel \
    make \
    automake \
    cmake \
    wget \
    vim-minimal \
    vim-common \
    vim-enhanced \
    vim-X11 \
    python-devel \
    cmake \
    tar \
    && dnf clean all

# Install Go
ENV GO_VERSION 1.5.1
RUN curl -sSL  "https://storage.googleapis.com/golang/go${GO_VERSION}.linux-amd64.tar.gz" | tar -v -C /usr/local -xz
ENV PATH /go/bin:/usr/local/go/bin:$PATH
ENV GOPATH /go

RUN wget https://raw.githubusercontent.com/tthanh/dotfiles/master/vim/vimrc -O ~/.vimrc \
    && mkdir -p ~/.vim/autoload \
    && curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
        https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim \
    && vim +PlugInstall +qall \
    && vim +GoInstallBinaries +qall

RUN mkdir -p /go/src/github.com/tthanh
