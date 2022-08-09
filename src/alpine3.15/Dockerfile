FROM alpine:3.15 as builder

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories \
    && apk update  \
    && apk add curl clang bash git grep unzip gzip sudo iputils python3 \
    && adduser -D xmake \
    && echo "xmake ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers.d/xmake \
    && chmod 0440 /etc/sudoers.d/xmake

USER xmake

RUN curl -fsSL https://xmake.io/shget.text | bash \
    && sudo ln -s ~/.local/bin/xmake /usr/bin/xmake \
    && sudo ln -s ~/.local/bin/xrepo /usr/bin/xrepo

RUN git clone https://gitee.com/xmake-mirror/build-artifacts.git /home/xmake/.xmake/repositories/build-artifacts
RUN git clone https://gitee.com/tboox/xmake-repo.git /home/xmake/.xmake/repositories/xmake-repo
