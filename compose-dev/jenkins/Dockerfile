FROM jenkins/jenkins:2.141-alpine

USER root
RUN apk add --no-cache curl tar

ARG MAVEN_VERSION=3.5.4
ARG SHA512=2a803f578f341e164f6753e410413d16ab60fabe31dc491d1fe35c984a5cce696bc71f57757d4538fe7738be04065a216f3ebad4ef7e0ce1bb4c51bc36d6be86
ARG BASE_URL=http://www-us.apache.org/dist/maven/maven-3/${MAVEN_VERSION}/binaries
ARG DESTINATION_DIR=/var/maven
RUN mkdir -p ${DESTINATION_DIR} \
  && curl -fsSL -o /tmp/apache-maven.tar.gz ${BASE_URL}/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
  && echo "${SHA512}  /tmp/apache-maven.tar.gz" | sha512sum -c - \
  && tar -xzf /tmp/apache-maven.tar.gz -C ${DESTINATION_DIR} --strip-components=1 \
  && rm -f /tmp/apache-maven.tar.gz \
  && ln -s ${DESTINATION_DIR}/bin/mvn /usr/bin/mvn

ENV MAVEN_HOME ${DESTINATION_DIR}
