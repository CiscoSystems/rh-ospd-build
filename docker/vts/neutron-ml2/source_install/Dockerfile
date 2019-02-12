# Cisco VTS ML2 Plugin dockerfile for installing plugin from source
# Author: wdec@cisco.com 2018

FROM registry.access.redhat.com/rhosp13/openstack-neutron-server
LABEL name="neutron-cisco-vts-ml2" vendor="cisco.com" version="2.6.3"
LABEL summary="cisco vts ml2"
LABEL description="Neutron Openstack 13 server with cisco VTS ML2"

ARG OS_VERSION=queens
#ARG USER=wdec
#ARG TOKEN=
ARG REPO=devhub.cisco.com/artifactory/vts-yum-dev/2.6.3.vts263-os-${OS_VERSION}
ARG REPO2=devhub.cisco.com/artifactory/vts-yum-dev/2.6.3.vts263
ARG PACKAGE=python-cisco-controller-0.1.7-14.el7_osp13.cisco.noarch.rpm
ARG PACKAGE2=python2-jsondiff-1.1.2-2.el7.centos.noarch.rpm
ARG _DST=/

USER root

#RUN mkdir -p "${_DST}"
#Install
ADD "${PACKAGE}" "${_DST}"
ADD "${PACKAGE2}" "${_DST}"

RUN yum-config-manager --disable rhel-7-server-htb-rpms && \
    yum-config-manager --enable rhel-7-server-rpms \
      rhel-7-server-extras-rpms rhel-7-server-rh-common-rpms rhel-ha-for-rhel-7-server-rpms \
      rhel-7-server-openstack-13-rpms
RUN yum clean all && yum install -y ${_DST}${PACKAGE} ${_DST}${PACKAGE2}

# Add required license info
RUN mkdir /licenses
COPY license.txt /licenses

#RUN rm -rf ${_DST}

USER neutron
