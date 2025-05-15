# Configuration files to run n8n in Google cloud


## Cloud SQL Proxy

### Download and install Cloud SQL Proxy
```zsh
wget https://dl.google.com/cloudsql/cloud_sql_proxy.linux.amd64 -O cloud_sql_proxy
chmod +x cloud_sql_proxy
sudo cp ./cloud_sql_proxy /usr/local/bin
```

### Location of systemd config for Google Cloud SQL Auth Proxy
- `/etc/systemd/system/cloud-sql-proxy.service`

### Reload systemd, start and enable the Cloud SQL Auth Proxy service
```zsh
sudo systemctl daemon-reload
sudo systemctl start cloud-sql-proxy.service
sudo systemctl enable cloud-sql-proxy.service
```

### Display the status of the Cloud SQL Proxy service
```zsh
sudo systemctl status cloud-sql-proxy.service
```

## Updates
### Updating Docker Compose
Given that we are running n8n using a Docker Compose file, we need to follow these steps to update n8n:
https://docs.n8n.io/hosting/installation/docker/#updating-docker-compose

#### Pull latest version
```zsh
docker compose pull
```

#### Stop and remove older version
```zsh
docker compose down
```

#### Start the container
```zsh
docker compose up -d
```
