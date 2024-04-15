# syntax=docker/dockerfile:1

FROM almalinux/9-init

RUN rm -f /lib/systemd/system/multi-user.target.wants/*;\
    rm -f /etc/systemd/system/*.wants/*;\
    rm -f /lib/systemd/system/local-fs.target.wants/*; \
    rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
    rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
    rm -f /lib/systemd/system/basic.target.wants/*;\
    rm -f /lib/systemd/system/anaconda.target.wants/*

RUN dnf install -y mysql-server

#Configuration de systemd
COPY --chmod=750 setup-tuleap.service /usr/lib/systemd/system/setup-tuleap.service
RUN systemctl enable setup-tuleap.service

RUN echo -e '[mysqld]\nsql-mode="NO_ENGINE_SUBSTITUTION"' > /etc/my.cnf.d/tuleap.cnf
RUN systemctl enable mysqld


COPY --chmod=750 script.sh /usr/local/sbin/script.sh

VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
