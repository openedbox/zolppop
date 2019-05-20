FROM debian:jessie
USER root
RUN mkdir -p /deployments

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        bzip2 \
        libfontconfig \
        curl \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && mkdir /tmp/phantomjs \
    && curl -L https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2 \
           | tar -xj --strip-components=1 -C /tmp/phantomjs \
    && cd /tmp/phantomjs \
    && mv bin/phantomjs /usr/local/bin \
    && cd \
    # && apt-get purge --auto-remove -y \
    #     curl \
    && apt-get clean \
    && rm -rf /tmp/* /var/lib/apt/lists/*


# Agent bond including Jolokia and jmx_exporter
ADD agent-bond-opts /opt/run-java-options
COPY agent-bond.jar /opt/agent-bond/
COPY run-java.sh /deployments/
COPY jdk1.8.0_202 /opt/java
RUN mkdir -p /opt/agent-bond
RUN chmod 444 /opt/agent-bond/agent-bond.jar \
 && chmod 755 /opt/run-java-options
ADD jmx_exporter_config.yml /opt/agent-bond/
EXPOSE 8778 9779


ENV JAVA_APP_DIR=/deployments \
    JAVA_HOME=/opt/java \
    CLASSPATH=.:/opt/java/lib/tools.jar \
    PATH=$PATH:/opt/java/bin \
    LANG=C.UTF-8

RUN chmod 755 /deployments/run-java.sh

CMD [ "/deployments/run-java.sh" ]
