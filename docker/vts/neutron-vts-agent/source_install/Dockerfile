# Cisco VTS ML2 Plugin dockerfile for installing plugin from source
# Author: wdec@cisco.com 2018

FROM registry.access.redhat.com/rhosp13/openstack-neutron-openvswitch-agent
LABEL  name="neutron-cisco-dhcp-agent" vendor="cisco.com" version="2.6.3"
LABEL summary="cisco vts agent"
LABEL description="Neutron Openstack 13 OVS with extension for runnion alongside cisco VTS"

ARG OS_VERSION=queens
#ARG USER=wdec
#ARG TOKEN=
ARG REPO=devhub.cisco.com/artifactory/vts-yum-dev/2.6.3.vts263-os-${OS_VERSION}
ARG PACKAGE=cisco-vts-agent-2.6.2-7.noarch.rpm
ARG _DST=/

USER root

RUN mkdir -p "${_DST}"
#Install
ADD "${PACKAGE}" "${_DST}"

RUN yum-config-manager --disable rhel-7-server-htb-rpms && \
    yum-config-manager --enable rhel-7-server-rpms \
      rhel-7-server-extras-rpms rhel-7-server-rh-common-rpms rhel-ha-for-rhel-7-server-rpms \
      rhel-7-server-openstack-13-rpms
RUN yum clean all && yum -y install python-crypto && yum install -y "${_DST}${PACKAGE}"

# Add required license info
RUN mkdir /licenses
COPY license.txt /licenses

#RUN rm -rf ${_DST}

USER neutron