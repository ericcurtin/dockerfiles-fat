FROM centos:6

ENV http_proxy=$http_proxy
ENV https_proxy=$https_proxy
ENV ftp_proxy=$ftp_proxy

RUN sed -i '/tsflags=nodocs/d' /etc/yum.conf
RUN printf $'[mariadb]\n\
name=MariaDB\n\
baseurl=https://yum.mariadb.org/10.0/centos6-amd64\n\
gpgcheck=0\n' > /etc/yum.repos.d/mariadb.repo
RUN curl -sL https://rpm.nodesource.com/setup_6.x | bash -
RUN ln -s /usr/bin/vim /usr/bin/vi

