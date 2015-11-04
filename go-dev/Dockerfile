FROM fedora:23
MAINTAINER Tien Thanh <thanhvt1609@gmail.com>

RUN dnf install -y \
    git \
    gcc \
    gcc-c++ \
    kernel-devel \
    make \
    automake \
    cmake \
    tmux \
    ctags \
    the_silver_searcher \
    python-devel \
    python-pip \
    tar \
    wget \
    httpie \
    xclip \
    dnf-plugins-core \
    redhat-rpm-config \
    && dnf clean all

RUN dnf copr enable -y dperson/neovim \
    && dnf install -y neovim \
    && dnf clean all \
    && pip install neovim

# Install Go
ENV GO_VERSION 1.5.1
RUN curl -sSL  "https://storage.googleapis.com/golang/go${GO_VERSION}.linux-amd64.tar.gz" | tar -v -C /usr/local -xz
ENV PATH=/usr/local/go/bin:/go/bin:$PATH GOPATH=/go

RUN mkdir -p ~/.config/nvim
RUN git clone --depth 1 https://github.com/tthanh/dotfiles.git ~/.dotfiles \
    && cd ~/.dotfiles && make docker-nvim
RUN nvim +PlugInstall +qall 1>/dev/null 2>&1
RUN nvim +GoInstallBinaries +qall 1>/dev/null 2>&1
RUN mkdir -p /go/src/github.com/tthanh

EXPOSE 8080

ENV TERM="xterm-256color"
