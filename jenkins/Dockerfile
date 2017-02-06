# FROM jenkins
FROM jenkins:2.19.3 

# There was no need for a custom image when jenkins official image was sufficient.
# However there was no way plugins.txt file could be processed by just mounting it as a volume 
# to the container running on the official jenkins image. 
# So to make that work, we need a Dockerfile for jenkins and create our oun jenkins image,
# named : yourcompany/jenkins
# The two lines below serve that need.

# For installing plugins, use the following two lines or use the one line solution further below:
# Reference: https://github.com/jenkinsci/docker
##############################################################################
COPY plugins.txt /usr/share/jenkins/ref/
RUN /usr/local/bin/plugins.sh /usr/share/jenkins/ref/plugins.txt
##############################################################################
#
# RUN /usr/local/bin/install-plugins.sh docker-slaves github-branch-source:1.8
##############################################################################
# Also, for now, please ignore the message telling you to use install-plugins.sh .
# That does not work with plugins.txt file.

# The following is necessary to set the correct time zone in the container.

# USER root
# ENV TZ=Europe/Oslo
# RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

USER jenkins

# The following passes the context to the jenkins container. 
# To be able to access jenkins service as jenkins.example.com/jenkins, you use "--prefix=/jenkins".
# To be able to access jenkins service as jenkins.example.com, you use "--prefix=/".
# CMD ["--prefix=/jenkins"]
CMD ["--prefix=/"]

# built it with: docker build --rm -t yourcompany/jenkins .

