FROM centos:7.3.1611

RUN sed -i '/tsflags=nodocs/d' /etc/yum.conf
RUN yum install -y rpm-build gcc clang vim ccache epel-release git \
      make rpm&& \
    yum clean all && \
    rm -rf /tmp/* /var/tmp/

