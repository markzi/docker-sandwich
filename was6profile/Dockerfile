# use this image as the base
FROM websphere-liberty:webProfile6

# install the admin center
RUN installUtility install --acceptLicense adminCenter-1.0

# copy across the DB2 JDBC driver
RUN mkdir -p /opt/ibm/wlp/usr/shared/resources/db2/v10
ADD db2jcc4.jar /opt/ibm/wlp/usr/shared/resources/db2/v10

# copy jvm options file to server
ADD jvm.options /opt/ibm/wlp/usr/servers/defaultServer/

# copy application
ADD sample.ear /opt/ibm/wlp/usr/servers/defaultServer/dropins

# copy up the server.xml and install the features
ADD server.xml /opt/ibm/wlp/usr/servers/defaultServer/
RUN installUtility install --acceptLicense defaultServer
