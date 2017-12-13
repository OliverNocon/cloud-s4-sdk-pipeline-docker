FROM openjdk:8-jdk

RUN apt-get update \
  && apt-get install -y \
    maven \
  && rm --recursive --force /var/lib/apt/lists/*

# add group & user
RUN addgroup -gid 1000 piper \
 && useradd piper --uid 1000 --gid 1000 --shell /bin/bash --create-home
 
RUN mvn com.sap.cloud:neo-java-web-maven-plugin:1.133.4:install-sdk -DsdkInstallPath=sdk -Dincludes=tools/**,license/**,sdk.version \
  && chown -R 1000:1000 sdk
  && ln -s sdk/tools/neo.sh /usr/bin/neo.sh

USER piper
