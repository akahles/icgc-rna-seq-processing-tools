FROM ubuntu:18.04

RUN apt-get update && \
    apt-get install -y python3-pip python3-dev software-properties-common curl && \
    apt-get install -y samtools bwa libz-dev pkg-config libtool m4 autotools-dev automake

RUN mkdir /tools

RUN cd /tools \
    && curl -sSL -o 2.7.7a.tar.gz --retry 10 https://github.com/alexdobin/STAR/archive/2.7.7a.tar.gz \
    && tar -xzf 2.7.7a.tar.gz

# Install OpenJDK-8
RUN apt-get update && \
    apt-get install -y openjdk-8-jdk && \
    apt-get install -y ant && \
    apt-get clean;

# Picard installation
RUN curl -sSL -o /tools/picard.jar --retry 10 https://github.com/broadinstitute/picard/releases/download/2.19.0/picard.jar

ENV LD_LIBRARY_PATH=/usr/local/lib

ENV PATH="/tools:/tools/STAR-2.7.7a/bin/Linux_x86_64:${PATH}"

CMD /bin/bash
