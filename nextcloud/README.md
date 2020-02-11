# NextCloud+MariaDB+Redis

1. Get `docker-compose.yml` file
```bash
wget https://raw.githubusercontent.com/kamilkobak/docker/master/nextcloud/docker-compose.yml
```
2. Run:
```bash
docker-compose up -d
```
3. Go to http://your_IP_address
When you first access your Nextcloud, the setup wizard will appear and ask you to choose an administrator account, password and the database connection. For the database use `mariadb` as host and `nextcloud` as table and user name. Also enter the password you chose in your docker-compose.yml file.

