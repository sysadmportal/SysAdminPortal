## Apache Installation
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
## MariaDB Installation & Setup
```
sudo apt install mariadb-server mariadb-client
sudo systemctl enable mariadb
sudo mysql -u root
CREATE DATABASE mautic;
CREATE USER 'mautic_user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON mautic.* TO 'mautic_user'@'localhost';
FLUSH PRIVILEGES;
```
## PHP8.1 Installation
```
sudo  apt install software-properties-common -y
sudo add-apt-repository ppa:ondrej/php
sudo apt-get install -y php8.1 php8.1-cli php8.1-curl php8.1-mbstring php8.1-mysql php8.1-xml php8.1-zip php8.1-intl php8.1-gd php8.1-imap php8.1-bcmath libapache2-mod-php8.1 unzip
php -v
sudo systemctl restart apache2
```
## NPM and NodeJS Installation
```
sudo apt install npm
sudo apt install nodejs -y
nodejs -v
npm -v
```
## Composer Installation
```
sudo curl -sS https://getcomposer.org/installer -o composer-setup.php
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
sudo rm composer-setup.php
sudo -u www-data composer --version
sudo a2enmod rewrite
sudo a2enmod headers
sudo systemctl restart apache2
```
## Make Directory for Mautic
```
sudo mkdir -p /var/www/mautic
sudo chown -R www-data:www-data /var/www
sudo nano /etc/apache2/sites-available/mautic.conf
sudo a2ensite mautic.conf
sudo systemctl reload apache2
```
## Connect Cloudfare
```
Connect Cloudfare HTTP
```
## Certbot and SSL Installation
```
sudo apt-get install -y certbot python3-certbot-apache
sudo certbot --apache
```
## Cloufare Tunnel edit to HTTPS and NO TLS VERIFY
```
Make Cloudfare Tunnel HTTPS
```
## Mautic Installation
```
sudo -u www-data composer create-project mautic/recommended-project:^6 /var/www/mautic --no-interaction
```
## Fixing Recommendations from Mautic 
```
sudo nano /etc/php/8.1/apache2/php.ini
sed -i 's/^memory_limit =.*/memory_limit = 512M/' /etc/php/8.1/apache2/php.ini
sed -i 's/^upload_max_filesize =.*/upload_max_filesize = 64M/' /etc/php/8.1/apache2/php.ini
sed -i 's/^post_max_size =.*/post_max_size = 64M/' /etc/php/8.1/apache2/php.ini
sed -i 's/^max_execution_time =.*/max_execution_time = 300/' /etc/php/8.1/apache2/php.ini
systemctl restart apache2
sudo systemctl restart apache2
```
   
