FROM fedora:23
MAINTAINER Tien Thanh <thanhvt1609@gmail.com>

RUN dnf update -y \
    && dnf install -y \
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
    xclip \
    dnf-plugins-core \
    redhat-rpm-config \
    golang \
    && dnf clean all \
    && rm -rf ~/.cache

RUN dnf copr enable -y dperson/neovim \
    && dnf install -y neovim \
    && dnf clean all \
    && pip install --no-cache-dir neovim \
    && rm -rf ~/.cache

RUN mkdir -p ~/ws/go/{src/github.com/tthanh,bin,pkg}
ENV GOPATH=/root/ws/go \
    PATH=$PATH:$GOPATH/bin \
    TERM="xterm-256color"

RUN mkdir -p ~/.config/nvim
RUN git clone --depth 1 https://github.com/tthanh/dotfiles.git ~/.dotfiles \
    && cd ~/.dotfiles && make docker
RUN nvim +PlugInstall +qall 1>/dev/null 2>&1 \
    && cd ~/.config/nvim/plugins/YouCompleteMe/third_party/ycmd/third_party \
    && rm -rf {OmniSharpServer, gocode, jedi}

RUN nvim +GoInstallBinaries +qall 1>/dev/null 2>&1

EXPOSE 8080
