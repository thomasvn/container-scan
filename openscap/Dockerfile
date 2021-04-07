# FROM registry.access.redhat.com/ubi7/ubi:7.9
# FROM ib-ubi7:7.9
# FROM centos:8
FROM fedora:34

# OpenSCAP and additional dependencies
RUN yum install openscap-scanner -y && \
    yum install scap-security-guide -y && \
    yum install wget unzip -y
