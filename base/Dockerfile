FROM centos:7

#env vars
ENV AG_MOBILE_SDK /opt/mobile-sdk

RUN yum install -y \
  wget \
  tar \
  unzip \
  zlib.i686 \
  ncurses-libs.i686 \
  bzip2-libs.i686 \
  epel-release \
  openssh-clients \
  git \
  gcc-c++ \
  make

#Install Python 3.4
RUN yum install -y python34
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python3.4 /get-pip.py
RUN rm /get-pip.py

#install cli
COPY tools /opt/tools
RUN /opt/tools/install-cli

#configure volumes and folders
RUN mkdir -p /opt/mobile-sdk && mkdir -p /etc/digger
VOLUME /opt/mobile-sdk

ENTRYPOINT ["abcd"]
CMD ["--help"]

