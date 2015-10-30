FROM fedora:latest
MAINTAINER Tien Thanh <thanhvt1609@gmail.com>

RUN dnf install -y git \
    wget \
    curl \
    vim-X11 \
    go

RUN mkdir -p ~/workspace/go
RUN wget https://raw.githubusercontent.com/tthanh/dotfiles/master/vim/vimrc -O ~/.vimrc
ENV HOME "/root"
ENV PATH "$HOME/workspace/go/bin:$PATH"
ENV GOPATH "$HOME/workspace/go"

CMD ["/bin/bash"]
