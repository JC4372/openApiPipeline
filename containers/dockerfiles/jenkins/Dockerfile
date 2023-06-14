FROM jenkins/jenkins:lts
EXPOSE 8080
USER root

RUN apt-get update
RUN apt-get install python3 python3-pip python3-venv -y
RUN curl -O https://fastdl.mongodb.org/tools/db/mongodb-database-tools-debian11-x86_64-100.7.2.deb
RUN apt install ./mongodb-database-tools-debian11-x86_64-100.7.2.deb


COPY ./jenkins-plugins.txt /usr/share/jenkins/ref/jenkins-plugins.txt
COPY ./casc.yaml /var/jenkins_home/casc.yaml

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false -Dhudson.model.DirectoryBrowserSupport.CSP=""
ENV JENKINS_ADMIN_ID admin
ENV JENKINS_ADMIN_PASSWORD admin123
ENV CASC_JENKINS_CONFIG /var/jenkins_home/casc.yaml

RUN jenkins-plugin-cli --plugins -f /usr/share/jenkins/ref/jenkins-plugins.txt