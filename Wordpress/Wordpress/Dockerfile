FROM wordpress:latest

MAINTAINER Jeff Benson <jbenson14@liberty.edu>

RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar && \
	chmod +x wp-cli.phar && \
	mv wp-cli.phar /usr/local/bin/wp

#ADD wp-config.php /var/www/html/wp-config.php

RUN wp core download --debug --locale=en_US --version=latest --force --allow-root && \
	wp config create --dbname=wordpress --dbuser=root --dbpass=example --dbhost=mysql --debug --skip-salts --skip-check --force --allow-root && \
	wp core install --url=localhost --debug --path=/var/www/html --title=MYAWESOMESITE --allow-root
	#--admin_user=admin --admin_email=test@testing.com --admin_password=admin --allow-root


RUN	wp plugin install --activate advanced-custom-fields --allow-root && \
	wp plugin install --activate tinymce-advanced --allow-root && \
	wp plugin install --activate wordpress-seo --allow-root
