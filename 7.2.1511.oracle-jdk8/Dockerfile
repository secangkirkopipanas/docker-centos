FROM centos:7.2.1511
MAINTAINER Robertus Lilik Haryanto <robert.djokdja@gmail.com>

# Configure environment variables
ENV JAVA_VERSION 8u91
ENV BUILD_VERSION b14

# Upgrade and install additional softwares
RUN \
	echo "### Upgrade and install additional softwares" && \
	yum -y upgrade && \
    yum -y install nano wget zip telnet && \
	yum clean all

# Downloading Java
RUN \
	wget --no-cookies --no-check-certificate --header "Cookie: oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/$JAVA_VERSION-$BUILD_VERSION/jdk-$JAVA_VERSION-linux-x64.rpm" -O /tmp/jdk-8-linux-x64.rpm && \
	yum -y install /tmp/jdk-8-linux-x64.rpm && \
	yum clean all && \
	rm -fR /tmp/jdk-8-linux-x64.rpm

# Configure alternatives
RUN \
	alternatives --install /usr/bin/java jar /usr/java/latest/bin/java 200000 && \
	alternatives --install /usr/bin/javaws javaws /usr/java/latest/bin/javaws 200000 && \
	alternatives --install /usr/bin/javac javac /usr/java/latest/bin/javac 200000

# Configure environment variables
ENV JAVA_HOME /usr/java/latest
ENV PATH $PATH:$JAVA_HOME/bin
ENV TZ Asia/Singapore

# Define default command
CMD ["/bin/bash"]