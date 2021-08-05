FROM debian:10.5-slim

RUN apt update
RUN apt install -y debmirror gpg curl apt-transport-https ca-certificates

# RUN
RUN gpg --no-default-keyring --keyring trustedkeys.gpg --list-keys

# KUBERNETES
RUN curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg

# DOCKER
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# ELASTIC
RUN curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch | gpg --dearmor -o /usr/share/keyrings/elasticsearch-archive-keyring.gpg

# HASHICORP
RUN curl -fsSL https://apt.releases.hashicorp.com/gpg | gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg

# NGINX
RUN curl -fsSL https://nginx.org/keys/nginx_signing.key | gpg --dearmor -o /usr/share/keyrings/nginx-archive-keyring.gpg
# curl -o /tmp/nginx_signing.key https://nginx.org/keys/nginx_signing.key
# gpg --dry-run --quiet --import --import-options import-show /tmp/nginx_signing.key

# POSTGRES
RUN curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc | gpg --dearmor -o /usr/share/keyrings/postgres-archive-keyring.gpg


# UBUNTU
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 871920D1991BC93C
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32 
RUN gpg --no-default-keyring --keyring ~/.gnupg/trustedkeys.gpg --keyserver keyserver.ubuntu.com --recv 871920D1991BC93C
RUN gpg --no-default-keyring --keyring ~/.gnupg/trustedkeys.gpg --keyserver keyserver.ubuntu.com --recv 3B4FE6ACC0B21F32
# curl -fsSLo /tmp/ubuntu-keyring_2021.03.26_all.deb http://ubuntu.mirrors.tds.net/ubuntu/pool/main/u/ubuntu-keyring/ubuntu-keyring_2021.03.26_all.deb
# dpkg -i /tmp/ubuntu-keyring_2021.03.26_all.deb
# gpg --keyring /usr/share/keyrings/ubuntu-archive-keyring.gpg --export | gpg --no-default-keyring --keyring /usr/share/keyrings/ubuntu-archive-keyring.gpg --import
# RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9578539176BAFBC6
# RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6494C6D6997C215E

CMD [ "sh", "-c", "debmirror ${DEST} --nosource --host=${HOST} --root=${ROOT} --dist=${DIST} --section=${SECTION} --i18n --arch=${ARCH} --passive --cleanup --method=${METHOD} --progress ${OTHERARGS} --rsync-extra=${RSYNCEXTRA:=trace}" ]





