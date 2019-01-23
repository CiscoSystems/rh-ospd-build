# Cisco VTS DHCP Agent Interface driver dockerfile
# Author: wdec@cisco.com 2018

FROM registry.access.redhat.com/rhosp13-beta/openstack-neutron-dhcp-agent
LABEL  name="neutron-cisco-dhcp-agent" vendor="cisco.com" version="2.6.3"
LABEL summary="cisco vts dhcp agent"
LABEL description="Neutron Openstack 13 DHCP agent with extension for runnion alongside cisco VPFA"

ARG OS_VERSION=queens
#ARG USER=wdec
#ARG TOKEN=
ARG REPO=devhub.cisco.com/artifactory/vts-yum-dev/2.6.3.vts263-os-${OS_VERSION}
ARG VTS_ML2_RPM=python-cisco-controller-agent-device-drivers-0.1.7-9.el7_osp13.cisco.noarch.rpm
ARG RPM_DST=/

USER root

#Copy RPM
ADD ["https://${USER}:${TOKEN}@${REPO}/ml2_plugin/${VTS_ML2_RPM}", "${RPM_DST}"]

# Add required license info
RUN mkdir /licenses
COPY license.txt /licenses

RUN rpm -i ${RPM_DST}${VTS_ML2_RPM}

#RUN rm -rf /${VTS_ML2_RPM}

USER neutron