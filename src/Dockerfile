FROM wenzhi/centos7-systemd
MAINTAINER wenzhi
ADD ./files /usr/local
RUN yum -y install build-essential openssl openssl-devel unixODBC unixODBC-devel make gcc gcc-c++ kernel-devel m4 ncurses-devel tk tc xz socat wget && \
    cp /usr/local/rabbitmq_erlang.repo /etc/yum.repos.d/rabbitmq_erlang.repo && \
    cp /usr/local/rabbitMQ.repo /etc/yum.repos.d/rabbitMQ.repo && \
    yum -y install erlang && \
    cd /usr/local && \
    wget https://github.com/rabbitmq/rabbitmq-server/releases/download/v3.7.16/rabbitmq-server-3.7.16-1.el7.noarch.rpm && \
    rpm --import https://github.com/rabbitmq/signing-keys/releases/download/2.0/rabbitmq-release-signing-key.asc && \
    yum -y install rabbitmq-server-3.7.16-1.el7.noarch.rpm && \ 
    rm -f /usr/local/rabbitmq_erlang.repo && \
    rm -f /usr/local/rabbitMQ.repo && \
    rm -f /usr/local/rabbitmq-server-3.7.16-1.el7.noarch.rpm && \
    yum clean all && \ 
    sed -i "s/{loopback_users, \[<<\"guest\">>\]},/{loopback_users, \[\]},/" /usr/lib/rabbitmq/lib/rabbitmq_server-3.7.16/ebin/rabbit.app && \
    rabbitmq-plugins enable rabbitmq_management
ENV LANG     en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
ENV LC_ALL   en_US.UTF-8

CMD rabbitmq-server start

EXPOSE 15671 15672
EXPOSE 4369 5671 5672 25672
