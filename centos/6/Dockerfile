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
RUN yum -y install epel-release centos-release-scl-rh\
      https://ftp.heanet.ie/mirrors/repoforge/redhat/el6/en/x86_64/rpmforge/RPMS/rpmforge-release-0.5.3-1.el6.rf.x86_64.rpm &&\
    yum -y update &&\
    yum -y install vim\
                   wget\
                   gcc\
                   autoconf\
                   zlib-devel\
                   gettext\
                   asciidoc\
                   xmlto\
                   perl-ExtUtils-MakeMaker\
                   curl-devel\
                   gcc-c++\
                   cmake\
                   MariaDB-server\
                   MariaDB-client\
                   redhat-lsb-core\
                   automake\
                   libtool\
                   openssl-devel\
                   libcurl-devel\
                   pam-devel\
                   ccache\
                   rpm-build\
                   boost-devel\
                   perl-Proc-ProcessTable\
                   perl-libwww-perl\
                   perl-JSON\
                   perl-HTTP-Daemon-SSL\
                   perl-Config-Std\
                   perl-FCGI\
                   perl-Convert-ASN1\
                   perl-Socket6\
                   perl-Time-HiRes\
                   perl-File-Copy-Recursive\
                   perl-HTTP-Proxy\
                   perl-File-ExtAttr\
                   perl-LDAP\
                   perl-Crypt-SSLeay\
                   perl-File-Slurp\
                   perl-IPC-Run\
                   uuid-perl\
                   attr\
                   dmidecode\
                   rsync\
                   clang\
                   the_silver_searcher\
                   perl-TermReadKey\
                   perl-Digest-SHA\
                   perl-DBD-MySQL\
                   perl-suidperl\
                   nc\
                   valgrind\
                   openssh-server\
                   cgdb\
                   nodejs\
                   lcov\
                   createrepo\
                   devtoolset-7-gcc-c++\
                   MariaDB-devel &&\
    yum clean all &&\
    rm -rf /tmp/* /var/tmp/* /var/cache/yum /usr/lib/mariadb/libmariadbclient.a
RUN cd /tmp &&\
    wget https://www.kernel.org/pub/software/scm/git/git-2.13.1.tar.gz &&\
    tar xf git-2.13.1.tar.gz &&\
    cd /tmp/git-2.13.1 &&\
    make configure &&\
    ./configure --prefix=/usr &&\
    make -j3 all doc &&\
    make -j3 install install-doc &&\
    rm -rf /tmp/git-2.13.1*
RUN cd /tmp &&\
    wget https://downloads.mariadb.com/Connectors/c/connector-c-3.0.2/mariadb-connector-c-3.0.2-src.tar.gz &&\
    tar xf /tmp/mariadb-connector-c-3.0.2-src.tar.gz &&\
    cd mariadb-connector-c-3.0.2-src &&\
    cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr . &&\
    make -j3 &&\
    make -j3 install &&\
    rm -rf /tmp/mariadb-connector-c-3.0.2-src*
RUN ln -s /usr/bin/vim /usr/bin/vi

