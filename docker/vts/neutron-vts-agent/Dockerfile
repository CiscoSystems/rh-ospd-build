# Cisco VTS Agent dockerfile
# Author: wdec@cisco.com 2018

FROM registry.access.redhat.com/rhosp13/openstack-neutron-openvswitch-agent
LABEL  name="neutron-cisco-dhcp-agent" vendor="cisco.com" version="2.6.3"
LABEL summary="cisco vts agent"
LABEL description="Neutron Openstack 13 OVS with extension for runnion alongside cisco VTS"

ARG OS_VERSION=queens
#ARG USER=wdec
#ARG TOKEN=
ARG REPO=devhub.cisco.com/artifactory/vts-yum-dev/2.6.3.vts263-os-${OS_VERSION}
ARG VTS_ML2_RPM=cisco-vts-agent-2.6.3-22.noarch.rpm
ARG RPM_DST=/

USER root

#Copy RPM
ADD ["https://${USER}:${TOKEN}@${REPO}/ml2_plugin/${VTS_ML2_RPM}", "${RPM_DST}"]

# Add required license info
RUN mkdir /licenses
COPY license.txt /licenses

RUN rpm -i /${VTS_ML2_RPM}

#RUN rm -rf /${VTS_ML2_RPM}

USER neutron