FROM centos:centos7

RUN yum install -y iputils net-tools iperf3 qperf iproute tcpdump && yum clean all

ENTRYPOINT ["qperf"]
