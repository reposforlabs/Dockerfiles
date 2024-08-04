FROM ubuntu
ENV TZ=Asia/Kolkata
RUN apt-get update
RUN apt-get install -y tzdata
RUN apt-get install -y apache2
RUN apt-get install -y apache2-utils
RUN apt-get install git -y
RUN apt update
RUN apt install -y libz-dev libssl-dev libcurl4-gnutls-dev libexpat1-dev gettext cmake gcc
RUN apt-get install -y nano && \
    apt-get install -y wget && \
    rm -fr /var/lib/apt/lists/*
RUN apt-get clean
EXPOSE 80
CMD ["apache2ctl", "-D", "FOREGROUND"]
