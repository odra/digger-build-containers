FROM aerogear/digger-base-builder

#copy tools
RUN mkdir -p /opt/tools /root/.android
COPY tools /opt/tools
COPY config /root/.android

#keystore args
ARG KS_ALIAS=androiddebug
ARG KS_NAME=AG
ARG KS_UNIT=AeroGear 
ARG KS_ORG=RedHat
ARG KS_LOC=Waterford
ARG KS_STATE=WD
ARG KS_COUNTRY=IRL
ARG KS_PATH=/etc/digger
ARG KS_STOREPASS=android
ARG KS_KEYPASS=android

#env vars
ENV JAVA_HOME /etc/alternatives/java_sdk_1.8.0
ENV ANDROID_HOME ${AG_MOBILE_SDK}
ENV AG_KEYSTORE_PATH ${KS_PATH}/debug.keystore
ENV AG_KEYSTORE_KEYPASS ${KS_KEYPASS}
ENV AG_KEYSTORE_STOREPASS ${KS_STOREPASS}
ENV AG_KEYSTORE_ALIAS ${KS_ALIAS}

RUN yum install -y \
  java-1.8.0-openjdk-devel \
  java-1.8.0-openjdk \
  ant

# install node 4.x
RUN curl --silent --location https://rpm.nodesource.com/setup_4.x | bash -
RUN yum -y install nodejs

# install Cordova CLI
RUN npm install -g cordova@6

#android tools
ENV PATH ${PATH}:${AG_MOBILE_SDK}/tools

#default keystore:q
RUN mkdir -p /etc/digger
RUN /opt/tools/gen-keystore ${KS_ALIAS} ${KS_NAME} ${KS_UNIT} ${KS_ORG} ${KS_LOC} ${KS_STATE} ${KS_COUNTRY} ${KS_PATH} ${KS_STOREPASS} ${KS_KEYPASS}
