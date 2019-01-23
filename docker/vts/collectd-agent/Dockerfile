# Cisco VTS DHCP Agent Interface driver dockerfile
# Author: wdec@cisco.com 2018

FROM registry.access.redhat.com/rhosp13-beta/openstack-collectd
LABEL  name="cisco-collectd-agent" vendor="cisco.com" version="2.6.3"

ARG OS_VERSION=queens
#ARG USER=
#ARG TOKEN=
ARG REPO=devhub.cisco.com/artifactory/vts-yum-dev/2.6.3.vts263
ARG REPO_PATH_SUFFIX=vts-collectd-plugin/noarch
ARG RPM=cisco-vpfa-collectd-plugin-1.0.2-4.noarch.rpm
ARG RPM_DST=/

USER root

#Copy RPM
ADD ["https://${USER}:${TOKEN}@${REPO}/${REPO_PATH_SUFFIX}/${RPM}", "${RPM_DST}"]

# Add required license info
RUN mkdir /licenses
COPY license.txt /licenses

RUN rpm -i ${RPM_DST}${RPM}

#RUN rm -rf ${RPM_DST}${RPM}

USER collectd