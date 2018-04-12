FROM ubuntu:latest
ADD jdk-6u45-linux-x64.bin /opt/jdk-6u45-linux-x64.bin
RUN cd /opt/ && \
    ./jdk-6u45-linux-x64.bin && \
    mv /opt/jdk1.6.0_45/jre /opt/java6 && \
    rm -rf /opt/jdk-6u45-linux-x64.bin \
    /opt/jdk1.6.0_45 \
USER ubuntu
ENV JAVA_HOME=/opt/java6 \ 
    PATH=${PATH}:/opt/java6/bin \ 
    LANG=en_US.UTF-8

COPY jboss-as-7.1.1.Final.tar.gz /opt/jboss-as-7.1.1.Final.tar.gz
RUN cd /opt/ && \
    tar xf /opt/jboss-as-7.1.1.Final.tar.gz && \
    mv /opt/jboss-as-7.1.1.Final /opt/jboss && \
    rm -rf /opt/jboss-as-7.1.1.Final.tar.gz

ENV JBOSS_HOME /opt/jboss
ENV LAUNCH_JBOSS_IN_BACKGROUND true

EXPOSE 8080

CMD ["/opt/jboss/bin/standalone.sh", "-b", "0.0.0.0"]