FROM rocm/rocm-terminal:5.5
USER root

## requriements inatallation 
RUN apt-get update && apt-get install -y automake \
    make g++ unzip build-essential autoconf \
    libtool pkg-config libgflags-dev libgtest-dev\
    clang libc++-dev curl libcap-dev supervisor && \
    apt-get install -y rdc && \
    apt-get install -y prometheus && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    pip3 install prometheus_client

## copy needed files
COPY ../python_binding /rdc/python_binding
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

## start service
CMD ["/usr/bin/supervisord"]
