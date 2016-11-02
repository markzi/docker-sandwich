FROM websphere-liberty:webProfile6
RUN installUtility install --acceptLicense adminCenter-1.0
ADD server.xml /opt/ibm/wlp/usr/servers/defaultServer/
RUN installUtility install --acceptLicense defaultServer
