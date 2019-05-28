FROM debian

RUN apt update && apt upgrade -y
RUN apt install nginx -y
RUN mkdir /var/www/Dog.com
COPY site /var/www/Dog.com
RUN useradd Alex && groupadd Timofeev
RUN usermod -a -G Timofeev Alex
RUN chown -R Alex:Timofeev /var/www/Dog.com
RUN sed -i 's#/var/www/html#/var/www/Dog.com#g' /etc/nginx/sites-enabled/default
RUN sed -i 's#www-data;#Alex;#g' /etc/nginx/nginx.conf
CMD ["nginx", "daemon off"]
