```
sudo apt install -y apache2 apache2-utils
sudo apt update -y && sudo apt upgrade -y
sudo systemctl enable apache2
sudo chown www-data:www-data /var/www/html/ -R
sudo apache2ctl -t
sudo nano /etc/apache2/conf-available/servername.conf
sudo a2enconf servername.conf
sudo systemctl reload apache2
sudo apache2ctl -t
```
```
sudo apt install mariadb-server mariadb-client
sudo systemctl enable mariadb
sudo mysql -u root
CREATE DATABASE mautic;
CREATE USER 'mautic_user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON mautic.* TO 'mautic_user'@'localhost';
FLUSH PRIVILEGES;
```

```
sudo  apt install software-properties-common -y
sudo add-apt-repository ppa:ondrej/php
sudo apt-get install -y php8.1 php8.1-cli php8.1-curl php8.1-mbstring php8.1-mysql php8.1-xml php8.1-zip php8.1-intl php8.1-gd php8.1-imap php8.1-bcmath libapache2-mod-php8.1 unzip
php -v
sudo systemctl restart apache2
```

```
sudo apt install npm
sudo apt install nodejs -y
nodejs -v
npm -v
```

```
sudo curl -sS https://getcomposer.org/installer -o composer-setup.php
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
sudo rm composer-setup.php
sudo -u www-data composer --version
sudo a2enmod rewrite
sudo a2enmod headers
sudo systemctl restart apache2
```

```
sudo mkdir -p /var/www/mautic
sudo chown -R www-data:www-data /var/www
sudo nano /etc/apache2/sites-available/mautic.conf
sudo a2ensite mautic.conf
sudo systemctl reload apache2
```

```
Connect Cloudfare HTTP
```

```
sudo apt-get install -y certbot python3-certbot-apache
sudo certbot --apache
```

```
Make Cloudfare Tunnel HTTPS
```

```
sudo -u www-data composer create-project mautic/recommended-project:^6 /var/www/mautic --no-interaction
```

```
sudo nano /etc/php/8.1/apache2/php.ini
sudo systemctl restart apache2
```
   
