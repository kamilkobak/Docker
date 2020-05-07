# NextCloud+MariaDB+Redis

1. Get `docker-compose.yml` file
```bash
wget https://raw.githubusercontent.com/kamilkobak/docker/master/nextcloud/docker-compose.yml
```

2. Change the password in the file and run it
```bash
vim docker-compose.yml
docker-compose up -d
```

3. Configure your firewall
 * RedHat/CentOS
```bash
firewall-cmd --zone=public --permanent --add-service=http
firewall-cmd --zone=public --permanent --add-service=https
firewall-cmd --reload
```
 * Debian/Ubuntu
```bash
ufw allow http
ufw allow https

```

4. When you first access your Nextcloud, the setup wizard will appear and ask you to choose an administrator account, password and the database connection. For the database use `mariadb` as host and `nextcloud` as table and user name. Also enter the password you chose in your docker-compose.yml file.


5. If you need to use SSL
```bash
mkdir /var/lib/docker/volumes/nextcloud_apache2/_data/ssl
cd /var/lib/docker/volumes/nextcloud_apache2/_data/ssl
sudo openssl req -x509 -nodes -days 1095 -newkey rsa:2048 -keyout nextcloud.key -out nextcloud.pem
cd /var/lib/docker/volumes/nextcloud_apache2/_data/sites-enabled/
wget https://raw.githubusercontent.com/kamilkobak/docker/master/nextcloud/ssl.conf
docker exec nextcloud a2enmod ssl
docker restart nextcloud
docker logs nextcloud
```
