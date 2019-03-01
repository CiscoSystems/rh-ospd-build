# Cisco VTS ML2 Plugin dockerfile
# Author: wdec@cisco.com 2018

FROM registry.access.redhat.com/rhosp13-beta/openstack-neutron-server
LABEL name="neutron-cisco-vts-ml2" vendor="cisco.com" version="2.6.3"
LABEL summary="cisco vts ml2"
LABEL description="Neutron Openstack 13 server with cisco VTS ML2"

ARG OS_VERSION=queens
ARG DRIVER_VERSION=0.1.7-17
ARG USER=wdec
#ARG TOKEN=
ARG REPO=devhub.cisco.com/artifactory/vts-yum-dev/2.6.3.vts263-os-${OS_VERSION}
ARG REPO2=devhub.cisco.com/artifactory/vts-yum-dev/2.6.3.vts263
ARG VTS_ML2_RPM=python-cisco-controller-${DRIVER_VERSION}.el7_osp13.cisco.noarch.rpm
ARG PACKAGE2=python2-jsondiff-1.1.2-2.el7.centos.noarch.rpm
ARG RPM_DST=/

USER root

#Copy RPM
ADD ["https://${USER}:${TOKEN}@${REPO}/ml2_plugin/${VTS_ML2_RPM}", "${RPM_DST}"]
ADD ["https://${USER}:${TOKEN}@${REPO2}/jsondiff/${PACKAGE2}", "${RPM_DST}"]

# Add required license info
RUN mkdir /licenses
COPY license.txt /licenses

RUN rpm -i ${RPM_DST}${VTS_ML2_RPM} ${RPM_DST}${PACKAGE2}

#RUN rm -rf /${VTS_ML2_RPM}

USER neutron