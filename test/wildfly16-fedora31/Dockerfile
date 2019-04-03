# Use fedora:31 image as the base
FROM wildfly15-fedora31

# Set the WILDFLY_VERSION env variable
ENV WILDFLY_VERSION 16.0.0.Final

# Add the WildFly distribution to /opt, and make wildfly the owner of the extracted tar content
# Make sure the distribution is available from a well-known place
RUN cd $HOME && curl -O https://download.jboss.org/wildfly/$WILDFLY_VERSION/wildfly-$WILDFLY_VERSION.tar.gz 
RUN cd $HOME && tar xf wildfly-$WILDFLY_VERSION.tar.gz 
RUN rm -rf /opt/jboss/wildfly/*
RUN mv $HOME/wildfly-$WILDFLY_VERSION/* /opt/jboss/wildfly 
RUN rm $HOME/wildfly-$WILDFLY_VERSION.tar.gz 

# Expose the ports we're interested in
EXPOSE 8080

# Set the default command to run on boot
# This will boot WildFly in the standalone mode and bind to all interface
CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0"]