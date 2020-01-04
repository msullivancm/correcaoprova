# ./Docker/Dockerfile
#DockerBuild
#docker build -t phpldap -f ./docker/Dockerfile .
#docker run -p 8080:80 --name apacheteste phpldap


# Base image
FROM ubuntu:bionic

# Instalação dos pré-requisitos
RUN apt update
ENV TZ 'America/Sao_Paulo'
RUN echo $TZ > /etc/timezone && \
  apt-get update && apt-get install -y tzdata && \
  rm /etc/localtime && \
  ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
  dpkg-reconfigure -f noninteractive tzdata && \
  apt-get clean
RUN apt install -y acpid apache2 php libapache2-mod-php php-mysql php-ldap ghostscript gsfonts imagemagick libapache2-mod-auth-plain libauthen-pam-perl libio-pty-perl libnet-ssleay-perl libpam-runtime lm-sensors mysql-client openssl perl php php-cli php-gd php-imagick php-curl php-memcache php-mysql ssh texlive-base-bin zbar-tools php-bz2 php-curl php-fileinfo php-gettext php-gmp php-intl php-imap php-ldap php-mbstring php-exif  php-mysqli php-pdo-mysql php-pdo-sqlite php-soap php-sockets php-sqlite3 php-xmlrpc php-xsl && apt clean

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_PID_FILE /var/run/apache2/apache2.pid
ENV APACHE_LOCK_DIR /var/lock

# Convenient working directory
WORKDIR /var/www/html

RUN echo 'Hello, docker' > /var/www/html/index.html

CMD ["/usr/sbin/apache2","-D", "FOREGROUND"]

