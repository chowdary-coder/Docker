FROM ubuntu
RUN apt update
ENV TZ=Asia/Kolkata
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ /etc/timezone
RUN apt install -y apache2
COPY index.html /var/www/html/
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf
CMD ["apache2ctl","-D","FOREGROUND"]
EXPOSE 80
