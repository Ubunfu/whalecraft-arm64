# Whalecraft - ARM
Start up a Minecraft server inside a Docker container compatible with 64-bit ARM (arm64/armv8/aarch64) architectures.

> Note: This project will ONLY run on machines with 64-bit ARM architectures

## Run on a Linux 64-bit ARM machine (e.g. Raspberry Pi))
### Set up some tools
```bash
# Install Git
sudo apt -y install git

# Set up Docker
sudo snap install docker
sudo groupadd docker
sudo usermod -aG docker <linux_user>
newgrp docker
```

### Set up game server
```bash
# Clone the project
git clone XXX && cd XXX
```
In [docker-compose.yml](docker-compose.yml), replace /`home/ubuntu/mc-container-data` with the path of an existing directory where you'd like the container to persist its world and configuration data.

```bash
# Run
docker-compose up
```
You now have a vanilla Minecraft server running in a Docker container that will automatically reboot itself ~~if~~ when it goes down!

## Configuration Overrides
Check out [docker-compose.yml](docker-compose.yml) for a brief summary of some config options you might be into tweaking.

Tweak them by adding arguments to the start command like this, or by adding them to [docker-compose.yml](docker-compose.yml):
```bash
# docker compose up -e KEY=VALUE
docker compose up -e MEMORY=4G
```

Visit the [itzg/minecraft-server](https://github.com/itzg/docker-minecraft-server) GitHub repo for a full page of docs about stuff you can tweak.

## Viewing logs
```bash
docker-compose logs -f mc
```