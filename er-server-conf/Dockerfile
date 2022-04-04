FROM debian

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    nano \
    sudo \
    openssh-server

ARG USER=a00038
ARG PW=8hjkj9jk

# Creacion usuario para sftp USER pass PW
RUN useradd -m ${USER} && echo "${USER}:${PW}" | chpasswd
RUN mkdir -m 777 -p /opt/app/ficheros/batchULL

COPY ssh_config /etc/ssh/ssh_config
COPY sshd_config /etc/ssh/sshd_config
COPY entrypoint.sh /usr/local/bin/entrypoint.sh

ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]

CMD tail -f /dev/null
