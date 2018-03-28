FROM jenkins:2.60.3
USER root

# prerequisites for docker
RUN apt-get update \
    && apt-get -y install \
        apt-transport-https \
        ca-certificates \
        curl \
        software-properties-common

# Install docker
RUN wget https://download.docker.com/linux/debian/gpg && \
    apt-key add gpg && \
    echo "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | tee -a /etc/apt/sources.list.d/docker.list && \
    apt-get update && \
    apt-get install -qy docker-ce

# Install compose
RUN curl -k -L https://github.com/docker/compose/releases/download/1.8.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose

# docker
RUN apt-get -y install docker-ce

# give jenkins docker rights
RUN usermod -aG docker jenkins

#COPY executors.groovy /usr/share/jenkins/ref/init.groovy.d/executors.groovy
#COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
#RUN /usr/local/bin/plugins.sh /usr/share/jenkins/ref/plugins.txt

# add the jenkins user to the docker group so that sudo is not required to run docker commands
RUN groupmod -g 1026 docker && gpasswd -a jenkins docker
USER jenkins

