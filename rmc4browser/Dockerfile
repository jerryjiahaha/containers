FROM base/archlinux:latest

MAINTAINER Jerry Jia "jerryjiahaha@gmail.com"

ENV username vncuser
ENV passwd vncuser1234

RUN pacman -Sy tigervnc libglvnd ttf-droid chromium pepper-flash openbox vim xterm --noconfirm && pacman -Scc --noconfirm

RUN useradd -m -g users -G wheel,network,video,audio -s /bin/bash -p ${passwd} ${username}

USER ${username}:users
# RUN su vncuser -c 'mkdir ~/.vnc && mkdir -p ~/.config/openbox'
RUN mkdir ~/.vnc && mkdir -p ~/.config/openbox

# TODO let user specify password
# RUN su vncuser -c 'printf "test1234\ntest1234\ny\n12345678\n12345678\n" | vncpasswd'
RUN printf "test1234\ntest1234\ny\n12345678\n12345678\n" | vncpasswd

COPY vnc/* /home/vncuser/.vnc/
COPY openbox/* /home/vncuser/.config/openbox/
USER root
RUN chown vncuser:users /home/vncuser/.vnc/* /home/vncuser/.config/openbox/*

USER ${username}:users
RUN mkdir ~/.cache
VOLUME /home/${vncuser}/.cache

EXPOSE 5901 5801
