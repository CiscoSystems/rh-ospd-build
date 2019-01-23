# Cisco VTS DHCP Agent dockerfile for installing plugin from source RPM
# Author: wdec@cisco.com 2018

FROM registry.access.redhat.com/rhosp13-beta/openstack-collectd
LABEL  name="cisco-collectd-agent" vendor="cisco.com" version="2.6.3"

ARG OS_VERSION=queens
#ARG USER=
#ARG TOKEN=
ARG REPO=devhub.cisco.com/artifactory/vts-yum-dev/2.6.3.vts263
ARG PACKAGE=cisco-vpfa-collectd-plugin-1.0.2-4.noarch.rpm

USER root

#RUN mkdir -p "${_DST}"
#Install
ADD "${PACKAGE}" /

#RUN yum-config-manager --disable rhel-7-server-htb-rpms && yum-config-manager --enable rhel-7-server-rpms rhel-7-server-extras-rpms rhel-7-server-rh-common-rpms rhel-ha-for-rhel-7-server-rpms rhel-7-server-openstack-beta-rpms
RUN yum install -y /${PACKAGE}

# Add required license info
RUN mkdir /licenses
COPY license.txt /licenses

#RUN rm -rf ${_DST}

USER collectd