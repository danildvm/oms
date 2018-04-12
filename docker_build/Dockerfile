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
    LANG=zh_CN.UTF-8

CMD ["/bin/bash"]
