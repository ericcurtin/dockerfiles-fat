FROM i386/centos:6

RUN sed -i '/tsflags=nodocs/d' /etc/yum.conf
RUN printf $'[mariadb]\n\
name = MariaDB\n\
baseurl = http://yum.mariadb.org/10.0/centos6-x86\n' > /etc/yum.repos.d/mariadb.repo

