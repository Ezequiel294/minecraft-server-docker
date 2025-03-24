# Minecraft Server Docker Template

A customizable Docker template for running a Minecraft server using the `itzg/minecraft-server` image.

## Features

- Configurable server type (Vanilla, Forge, etc.)
- Easy mod installation
- Customizable whitelist and permissions
- Volume mapping for persistent data

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Installation

1. Clone or download this template:
   ```
   git clone https://github.com/yourusername/minecraft-server-docker.git
   cd minecraft-server-docker
   ```

2. Configure the `docker-compose.yml` file with your desired settings

3. Start the server:
   ```
   docker-compose up -d
   ```

4. To stop the server (without removing it):
   ```
   docker stop minecraft-server
   ```

5. To restart a stopped server:
   ```
   docker start minecraft-server
   ```

6. To completely remove the server (will not delete your world data):
   ```
   docker-compose down
   ```

7. To delete the server and all world data:
   ```
   docker-compose down
   rm -rf ./data
   ```

## Usage

- The Minecraft server will be available at: `your-server-ip:25565`
- Set your admin user(s) in the `OPS` environment variable

## Configuration Options

The server is configured via environment variables in the docker-compose.yml file:

- **VERSION**: Minecraft version (e.g., "1.16.5", "1.19.2")
- **MEMORY**: RAM allocation (e.g., "2G", "4G")
- **DIFFICULTY**: World difficulty (peaceful, easy, normal, hard)
- **TYPE**: Server type (VANILLA, FORGE, FABRIC, etc.)

### Adding Mods

Use the `MODRINTH_PROJECTS` variable to specify mods to install from Modrinth:

```yaml
MODRINTH_PROJECTS: |
  mod-slug-1
  mod-slug-2
```

## Whitelist Management

Control access to your server with the whitelist feature:

```yaml
ENABLE_WHITELIST: "true"
FORCE_WHITELIST: "true"
WHITELIST: |
  Player1
  Player2
  Player3
```

## Data Persistence

All server data is stored in the `./data` directory, which is mapped to the container's `/data` directory. This includes:

- World files
- Configuration files
- Mods and plugins
- Logs

## Backup Recommendations

It's recommended to regularly backup the `./data` directory to prevent data loss.

## Advanced Configuration

For more configuration options, refer to the [itzg/minecraft-server documentation](https://github.com/itzg/docker-minecraft-server).
