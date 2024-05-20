FROM jenkins/jenkins

USER root

RUN apt-get update && \
    apt-get install -y apt-transport-https ca-certificates curl software-properties-common

# Add Docker's official GPG key
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -

# Add Docker repository
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"

# Install Docker
RUN apt-get update && \
    apt-get install -y docker-ce

# Change back to the jenkins user
#USER jenkins
