# Cisco VTS DHCP Agent dockerfile for installing plugin from source RPM
# Author: wdec@cisco.com 2018

FROM registry.access.redhat.com/rhosp13-beta/openstack-neutron-dhcp-agent
LABEL  name="neutron-cisco-dhcp-agent" vendor="cisco.com" version="2.6.3"
LABEL summary="cisco vts dhcp agent"
LABEL description="Neutron Openstack 13 DHCP agent with extension for runnion alongside cisco VPFA"

ARG OS_VERSION=queens
#ARG USER=wdec
#ARG TOKEN=
ARG REPO=devhub.cisco.com/artifactory/vts-yum-dev/2.6.3.vts263-os-${OS_VERSION}
ARG PACKAGE=python-cisco-controller-agent-device-drivers-0.1.7-14.el7_osp13.cisco.noarch.rpm
ARG _DST=/

USER root

#RUN mkdir -p "${_DST}"
#Install
ADD "${PACKAGE}" "${_DST}"

#RUN yum-config-manager --disable rhel-7-server-htb-rpms && yum-config-manager --enable rhel-7-server-rpms rhel-7-server-extras-rpms rhel-7-server-rh-common-rpms rhel-ha-for-rhel-7-server-rpms rhel-7-server-openstack-beta-rpms
RUN yum install -y "${_DST}${PACKAGE}"

# Add required license info
RUN mkdir /licenses
COPY license.txt /licenses

#RUN rm -rf ${_DST}

USER neutron