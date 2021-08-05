# RM

```sh
docker build --no-cache -t quay.io/vdmpo/debmirror:1.0.0 .
docker push quay.io/vdmpo/debmirror:1.0.0
```

# Sources List

```sh
deb http://archive.ubuntu.com/ubuntu/ focal main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ focal main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ focal-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ focal-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu focal partner
deb-src http://archive.canonical.com/ubuntu focal partner
```

# Run

```sh
docker run --rm -it -e DEST=/mnt/debmirror/ubuntu \
                    -e HOST=mirror.arizona.edu \
                    -e ROOT=ubuntu/ \
                    -e DIST=groovy \
                    -e SECTION=main,restricted,universe,multiverse \
                    -e ARCH=amd64 \
                    -e METHOD=http \
                    debmirror
```

```sh
export DEST=/mnt/debmirror/ubuntu
export HOST=mirror.arizona.edu
export ROOT=ubuntu/
export DIST=focal
export SECTION=main,restricted,universe,multiverse
export ARCH=amd64
export METHOD=http

debmirror ${DEST} --nosource --host=${HOST} --root=${ROOT} --dist=${DIST} --section=${SECTION} --i18n --arch=${ARCH} --passive --cleanup --method=${METHOD}
```
