# compose-on-boot

Start common software on boot with Systemd and Docker Compose

First, create a template unit for Docker Compose which is parameterized by the name of the service (see systemd.service(5) § SERVICE TEMPLATES):

```bash
sudo cp docker-compose@.service /etc/systemd/system/docker-compose@.service
```

Then, for each service you would like to run, set up a directory with the Compose file and any other required files (such as .env files) at /opt/project_name.

Then, enable/start **docker-compose@app_name.service**.

```bash
sudo systemctl status docker-compose@postgresql.service
sudo systemctl status docker-compose@redis.service

sudo systemctl enable --now docker-compose@redis.service
```

## Docs

[SystemD Service Template](https://man.archlinux.org/man/systemd.service.5#SERVICE_TEMPLATES)
