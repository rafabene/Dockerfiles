#This file is for demonstration purposes only. Please, don't use this image for production

# Use fedora:23 image as the base
FROM fedora:23

MAINTAINER Rafael Benevides <benevides@redhat.com>

ENV WILDFLY_VERSION 10.0.0.Final

# Install necessary packages
RUN dnf -y install java-1.8.0-openjdk-devel tar && dnf clean all

RUN mkdir -p /opt/jboss/

#Add Wildfly 10.0.0 to this image
WORKDIR /tmp
RUN curl -O https://download.jboss.org/wildfly/$WILDFLY_VERSION/wildfly-$WILDFLY_VERSION.tar.gz  
RUN tar xf wildfly-$WILDFLY_VERSION.tar.gz 
RUN mv /tmp/wildfly-$WILDFLY_VERSION /opt/jboss/wildfly 
RUN rm /tmp/wildfly-$WILDFLY_VERSION.tar.gz
      
# Expose the ports we're interested in
EXPOSE 8080

# Set the default command to run on boot
# This will boot WildFly in the standalone mode and bind to all interface
CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0"]
