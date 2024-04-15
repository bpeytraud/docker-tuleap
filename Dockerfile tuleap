# syntax=docker/dockerfile:1

FROM almalinux/9-init

RUN rm -f /lib/systemd/system/multi-user.target.wants/*;\
    rm -f /etc/systemd/system/*.wants/*;\
    rm -f /lib/systemd/system/local-fs.target.wants/*; \
    rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
    rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
    rm -f /lib/systemd/system/basic.target.wants/*;\
    rm -f /lib/systemd/system/anaconda.target.wants/*

RUN dnf install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.r>
RUN dnf install -y https://rpms.remirepo.net/enterprise/remi-release-9.rpm
RUN dnf install -y https://ci.tuleap.net/yum/tuleap/rhel/9/dev/x86_64/tuleap-community->

RUN dnf install -y \
    tuleap \
    tuleap-theme-burningparrot \
    tuleap-theme-flamingparrot \
    tuleap-plugin-tracker

#Configuration de systemd
COPY --chmod=750 setup-tuleap.service /usr/lib/systemd/system/setup-tuleap.service
RUN systemctl enable setup-tuleap.service

COPY --chmod=750 script.sh /usr/local/sbin/script.sh

RUN systemctl disable tuleap


VOLUME ["/sys/fs/cgroup"]
CMD ["/usr/sbin/init"]
