# Docker File : Create Jenkins image to dockerise jenkins build
# Build imagee : docker build -t dockerimage .
# Linux users : docker run -p 8180:8080 -p 51000:50000 -v /var/run/docker.sock:/var/run/docker.sock /home/docker/volume:/var/jenkins_home dockerimage
# Mac users : docker run -p 8180:8080 -p 51000:50000  -v /var/run/docker.sock:/var/run/docker.sock  -v $(which docker):/usr/bin/docker dockerimage

FROM jenkins/jenkins

MAINTAINER Pierre Malherbe (pierre.malherbe6@gmail.com)

# this is a non-interactive automated build - avoid some warning messages
ENV DEBIAN_FRONTEND noninteractive
#set for nano
ENV TERM xterm

ARG cur_user="jenkins"

USER root

RUN apt-get update \
          && apt-get install -y sudo nano wget curl unzip \
                ca-certificates openssl openssh-server \
                git subversion

# add jenkins user to sudo group
RUN echo "${cur_user} ALL=NOPASSWD: ALL" >> /etc/sudoers

ARG usr_bin="/usr/local/bin"

# Clean
RUN  apt-get clean \
          && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/man/?? /usr/share/man/??_*

