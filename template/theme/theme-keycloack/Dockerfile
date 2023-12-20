FROM quay.io/keycloak/keycloak:19.0.3 as keycloak_base
# data path
RUN mkdir -p /tmp/data
RUN mkdir -p /opt/keycloak/data/tmp/kc-gzip-cache/jiwz3/
# update theme
RUN rm -fr /opt/keycloak/themes/afranet
COPY --chown=1000:0 ./themes/keycloak /opt/keycloak/themes/afranet
COPY --chown=1000:0 ./themes/keycloak/welcome /opt/keycloak/data/tmp/kc-gzip-cache/jiwz3/welcome
# disablbe theme cache
#RUN sed -i 's/<staticMaxAge>2592000/<staticMaxAge>-1/g' /opt/jboss/keycloak/standalone/configuration/standalone.xml
#RUN sed -i 's/<cacheThemes>true/<cacheThemes>false/g' /opt/jboss/keycloak/standalone/configuration/standalone.xml
#RUN sed -i 's/<cacheTemplates>true/<cacheTemplates>false/g' /opt/jboss/keycloak/standalone/configuration/standalone.xml
# move webhook to image
COPY --chown=1000:0 ./webhooks/keycloak-event-listener-http/target/event-listener-http-jar-with-dependencies.jar /opt/keycloak/providers
# update keycloak configuration
# RUN rm -fr /opt/jboss/keycloak/standalone/configuration/standalone.xml
# COPY --chown=1000:0 ./configs/standalone/standalone.xml /opt/jboss/keycloak/standalone/configuration
WORKDIR /opt/keycloak
#LABEL org.opencontainers.image.source=https://github.com/unicoria/auth.unicoria.com
#LABEL org.opencontainers.image.description=""
#LABEL org.opencontainers.image.licenses=""
