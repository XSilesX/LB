FROM ubuntu

MAINTAINER rskpar@mail.ru

RUN apt update && apt upgrade -y
RUN apt install nginx -y
RUN apt install nano -y
RUN rm -rf var/www/*
RUN mkdir /var/www/company.com
COPY site /var/www/company.com
COPY site/index.html /var/www/company.com
RUN chmod 754 /var/www/company.com -R
RUN useradd alex
RUN addgroup timofeev
RUN usermod -a -G timofeev alex
RUN chown -R alex:timofeev var/www/company.com
RUN sed -i 's#/var/www/html#/var/www/company.com#g' /etc/nginx/sites-enabled/default
RUN sed -i 's#/user#/alex#/g' /etc/nginx/nginx.conf

CMD ["nginx", "-g", "daemon off;"]
