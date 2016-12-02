# centos-7-base
# Copyright (C) 2015-2016 Intel Corporation
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along
# with this program; if not, write to the Free Software Foundation, Inc.,
# 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

FROM centos:centos7

ADD http://downloads.yoctoproject.org/releases/yocto/yocto-2.2/buildtools/x86_64-buildtools-nativesdk-standalone-2.2.sh /buildtools.sh

RUN yum -y install epel-release && \
    yum -y update && \
    yum -y install \
        gawk \
        make \
        wget \
        tar \
        bzip2 \
        gzip \
        python \
        python34 \
        unzip \
        perl \
        patch \
        diffutils \
        diffstat \
        git \
        cpp \
        gcc \
        gcc-c++ \
        glibc-devel \
        texinfo \
        chrpath \
        socat \
        perl-Data-Dumper \
        perl-Text-ParseWords \
        perl-Thread-Queue \
        SDL-devel \
        file \
        tigervnc-server \
        xz \
        screen \
        tmux \
        which && \
    yum -y clean all && \
    groupadd -g 1000 yoctouser && \
    useradd -u 1000 -g yoctouser -m yoctouser && \
    mkdir -p /home/yoctouser/.vnc && \
    echo "" | vncpasswd -f > /home/yoctouser/.vnc/passwd && \
    chmod 0600 /home/yoctouser/.vnc/passwd && \
    chmod +x /buildtools.sh && \
    echo -e "/opt/buildtools\ny\n" | /buildtools.sh && \
    echo '. /opt/buildtools/environment-setup*' >> /etc/profile.d/buildtools.sh && \
    chown -R yoctouser:yoctouser /home/yoctouser && \
    rm -f /buildtools.sh

USER yoctouser
WORKDIR /home/yoctouser
CMD /bin/bash
