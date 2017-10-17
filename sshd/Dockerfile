FROM alpine:latest

MAINTAINER Jerry Jia "jerryjiahaha@gmail.com"

ENV usrname lucifer
ENV passwd bokunopico
ENV port   10233

RUN adduser -D ${usrname}
RUN echo "${usrname}:${passwd}" | chpasswd

RUN apk update
RUN apk add openssh-server

# TODO use static key
RUN ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N "" -t rsa
RUN ssh-keygen -f /etc/ssh/ssh_host_dsa_key -N "" -t dsa
RUN ssh-keygen -f /etc/ssh/ssh_host_ecdsa_key -N "" -t ecdsa
RUN ssh-keygen -f /etc/ssh/ssh_host_ed25519_key -N "" -t ed25519

RUN rm -rf /var/cache/apk

EXPOSE ${port}

ENTRYPOINT ["/usr/sbin/sshd", "-D"]
