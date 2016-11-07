#####################################################################################
# Dockerfile that provides the image for JBoss Drools Workbench 6.4.0.Final Showcase
#####################################################################################

####### BASE ############
FROM jboss/drools-workbench:6.4.0.Final

####### MAINTAINER ############
MAINTAINER "Michael Biarnes Kiefer" "mbiarnes@redhat.com"

####### ENVIRONMENT ############
# Use demo and examples by default in this showcase image (internet connection required).
ENV KIE_DEMO true
ENV KIE_SERVER_PROFILE standalone-full-drools

####### Drools Workbench CUSTOM CONFIGURATION ############
ADD etc/standalone-full-drools.xml $JBOSS_HOME/standalone/configuration/standalone-full-drools.xml
ADD etc/drools-users.properties $JBOSS_HOME/standalone/configuration/drools-users.properties
ADD etc/drools-roles.properties $JBOSS_HOME/standalone/configuration/drools-roles.properties
ADD etc/ojdbc7.jar $JBOSS_HOME/modules/system/layers/base/com/oracle/main/ojdbc7.jar
ADD etc/module.xml $JBOSS_HOME/modules/system/layers/base/com/oracle/main/module.xml

# Added files are chowned to root user, change it to the jboss one.
USER root
RUN chown jboss:jboss $JBOSS_HOME/standalone/configuration/standalone-full-drools.xml && \
chown jboss:jboss $JBOSS_HOME/standalone/configuration/drools-users.properties && \
chown jboss:jboss $JBOSS_HOME/standalone/configuration/drools-roles.properties && \
chown jboss:jboss $JBOSS_HOME/modules/system/layers/base/com/oracle/main/ojdbc7.jar && \
chown jboss:jboss $JBOSS_HOME/modules/system/layers/base/com/oracle/main/module.xml

# Switchback to jboss user
USER jboss

####### RUNNING DROOLS-WB ############
WORKDIR $JBOSS_HOME/bin/
CMD ["./start_drools-wb.sh"]
