FROM debian:10.5-slim

## APT
RUN apt update
RUN apt install -y debmirror gpg curl apt-transport-https ca-certificates

## USER and PERMISSIONS
RUN groupadd -r -g 101 debmirror && useradd -m --no-log-init -r -g debmirror -u 101 debmirror

RUN chgrp -R debmirror /usr/share/keyrings && \
    chmod g+w /usr/share/keyrings && \
    chgrp -R debmirror /etc/apt && \
    chmod -R g+w /etc/apt

WORKDIR /home/debmirror

USER debmirror

RUN gpg --no-default-keyring --keyring trustedkeys.gpg --list-keys

## UBUNTU
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 871920D1991BC93C
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32 
RUN gpg --no-default-keyring --keyring ~/.gnupg/trustedkeys.gpg --keyserver keyserver.ubuntu.com --recv 871920D1991BC93C
RUN gpg --no-default-keyring --keyring ~/.gnupg/trustedkeys.gpg --keyserver keyserver.ubuntu.com --recv 3B4FE6ACC0B21F32

## KUBERNETES
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 836F4BEB
RUN gpg --no-default-keyring --keyring ~/.gnupg/trustedkeys.gpg --keyserver keyserver.ubuntu.com --recv 836F4BEB

## DOCKER
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0EBFCD88
RUN gpg --no-default-keyring --keyring ~/.gnupg/trustedkeys.gpg --keyserver keyserver.ubuntu.com --recv 0EBFCD88

## ELASTIC
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D88E42B4
RUN gpg --no-default-keyring --keyring ~/.gnupg/trustedkeys.gpg --keyserver keyserver.ubuntu.com --recv D88E42B4

## HASHICORP
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A3219F7B
RUN gpg --no-default-keyring --keyring ~/.gnupg/trustedkeys.gpg --keyserver keyserver.ubuntu.com --recv A3219F7B

## NGINX
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7BD9BF62
RUN gpg --no-default-keyring --keyring ~/.gnupg/trustedkeys.gpg --keyserver keyserver.ubuntu.com --recv 7BD9BF62

# POSTGRES
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7FCC7D46ACCC4CF8
RUN gpg --no-default-keyring --keyring ~/.gnupg/trustedkeys.gpg --keyserver keyserver.ubuntu.com --recv 7FCC7D46ACCC4CF8

CMD [ "sh", "-c", "debmirror ${DEST} --nosource --host=${HOST} --root=${ROOT} --dist=${DIST} --section=${SECTION} --i18n --arch=${ARCH} --passive --cleanup --method=${METHOD} --progress ${OTHERARGS} --rsync-extra=${RSYNCEXTRA:=trace}" ]





