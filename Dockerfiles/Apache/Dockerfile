FROM ubuntu:16.04
# Install apache2 package

RUN apt-get update && \
    apt-get install -y apache2 && \
    apt-get clean
EXPOSE 80

# Launch apache2 server in the foreground
ENTRYPOINT ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
