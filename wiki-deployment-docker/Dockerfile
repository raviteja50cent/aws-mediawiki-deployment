FROM centos:7.6.1810
ENV container docker

# PHP & Mariadb Installation
RUN yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm; yum -y install http://rpms.remirepo.net/enterprise/remi-release-7.rpm; yum -y install yum-utils; yum-config-manager --enable remi-php71; yum -y install php php-opcache
RUN yum -y install php71 \
    php71-php \
    php71-php-pdo \
    php71-php-mbstring \
    php71-php-mysqlnd \
    php71-php-gd \
    php71-php-xml \
    mariadb-server \
    mariadb \
    wget \
    vim

# Apache httpd Installation
RUN yum -y update; yum clean all; yum -y install httpd

# MySQL Installation
RUN wget https://repo.mysql.com/mysql80-community-release-el7-1.noarch.rpm; yum localinstall mysql80-community-release-el7-1.noarch.rpm; yum repolist enabled | grep "mysql.*-community.*"; yum-config-manager --disable mysql57-community; yum install mysql-community-server

# Set working directory
RUN mkdir /opt/mediawiki
WORKDIR /opt/mediawiki

# Download and untar mediawiki
RUN wget https://releases.wikimedia.org/mediawiki/1.31/mediawiki-1.31.1.tar.gz; tar xvzf mediawiki-1.31.1.tar.gz 
EXPOSE 80

# Install systemd
RUN yum -y install systemd; yum clean all; \
(cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;
VOLUME [ “/sys/fs/cgroup” ]
CMD [“/usr/sbin/init”]