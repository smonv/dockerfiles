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
    vim-minimal \
    vim-common \
    vim-enhanced \
    vim-X11 \
    python-devel \
    tar \
    wget \
    httpie \
    && dnf clean all

# Install Go
ENV GO_VERSION 1.5.1
RUN curl -sSL  "https://storage.googleapis.com/golang/go${GO_VERSION}.linux-amd64.tar.gz" | tar -v -C /usr/local -xz
ENV PATH=/go/bin:/usr/local/go/bin:$PATH GOPATH=/go

RUN git clone https://github.com/tthanh/dotfiles.git ~/.dotfiles \
    && cd ~/.dotfiles && make docker \
    && vim +PlugInstall +qall \
    && vim +GoInstallBinaries +qall \
    && mkdir -p /go/src/github.com/tthanh

EXPOSE 8080
