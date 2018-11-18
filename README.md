# rh-ospd-build

Docker files and artefacts used to enable the OSPD container builds hosted by RedHat
Contact wdec@cisco.com or muraliv@cisco.com for details on running the builds.

Repository has two dockerfile versions, one allowing YUM retrieval of the RPMs, the other using
a local RPM copy for cases where YUM access is not possible.