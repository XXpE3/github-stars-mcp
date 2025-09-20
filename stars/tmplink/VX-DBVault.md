---
project: VX-DBVault
stars: 3
description: |-
    VX-DBVault is a Docker-based automated backup tool for MariaDB and MySQL databases.
url: https://github.com/tmplink/VX-DBVault
---

# VX-DBVault

[中文指南](README_cn.md) | [日本語ガイド](README_jp.md)

## Introduction

VX-DBVault is a Docker-based database backup tool designed specifically for MySQL/MariaDB databases. It provides automated database backup functionality with support for scheduled backups, file compression, and multi-platform deployment.

### Key Features

* 🔧 **Easy Deployment**: Docker container-based, one-click startup
* ⏰ **Scheduled Backups**: Support for custom backup intervals
* 🗜️ **Smart Compression**: Automatic backup file compression to save storage space
* 🔒 **Secure Connection**: Support for secure database connection configuration
* 📊 **Detailed Logging**: Complete backup process logging
* 🌐 **Multi-Platform**: Support for linux/amd64 and linux/arm64 architectures

### System Requirements

- Docker 18.09+ or Docker Desktop
- Supported architectures: linux/amd64, linux/arm64
- For multi-platform builds: Docker Buildx support

## Quick Start

### Method 1: Using Pre-built Image (Recommended)

Pull and use directly from Docker Hub:

```bash
# Pull the latest image
docker pull vxlink/db_vault

# Basic usage (backup all databases, 24-hour interval)
docker run -d --name db_vault \
    -v /host/backup/path:/tmp \
    -e DB_HOST="your.database.host" \
    -e DB_USER="your_username" \
    -e DB_PASS="your_password" \
    vxlink/db_vault
```

### Method 2: Local Build

```bash
# Build for native platform
./build.sh

# Build for all supported platforms
./build.sh --all-platforms

# Build and push to Docker Hub (login required)
./build.sh --push
```

Windows users should use PowerShell:

```powershell
# Build for native platform
.\build.ps1

# Build for all supported platforms
.\build.ps1 -AllPlatforms

# Build and push to Docker Hub
.\build.ps1 -Push
```

## Configuration Options

Configure backup parameters via environment variables:

| Variable | Default | Description |
|----------|---------|-------------|
| `DB_HOST` | `1.1.1.1` | Database host address |
| `DB_USER` | `root` | Database username |
| `DB_PASS` | `password` | Database password |
| `DB_NAMES` | `vxdb` | Database names to backup (space-separated) |
| `BACKUP_INTERVAL` | `24` | Backup interval in hours, 0 for one-time backup |

## Usage Examples

### 1. Basic Backup (Default Configuration)

```bash
docker run -d --name db_vault \
    -v /root/dbbackup:/tmp \
    vxlink/db_vault
```

### 2. Specify Databases to Backup

```bash
docker run -d --name db_vault \
    -v /root/dbbackup:/tmp \
    -e DB_NAMES="mydb1 mydb2 mydb3" \
    vxlink/db_vault
```

### 3. Set Backup Interval (Every 6 hours)

```bash
docker run -d --name db_vault \
    -v /root/dbbackup:/tmp \
    -e BACKUP_INTERVAL="6" \
    vxlink/db_vault
```

### 4. One-time Backup (No Loop)

```bash
docker run -d --name db_vault \
    -v /root/dbbackup:/tmp \
    -e BACKUP_INTERVAL="0" \
    vxlink/db_vault
```

### 5. Complete Configuration Example

```bash
docker run -d --name db_vault \
    -v /host/backup/directory:/tmp \
    -e DB_HOST="192.168.1.100" \
    -e DB_USER="backup_user" \
    -e DB_PASS="secure_password" \
    -e DB_NAMES="production staging development" \
    -e BACKUP_INTERVAL="12" \
    vxlink/db_vault
```

### Windows Example

```cmd
docker run -d --name db_vault ^
    -v D:\db_vault:/tmp ^
    -e DB_HOST="192.168.1.100" ^
    -e DB_USER="backup_user" ^
    -e DB_PASS="secure_password" ^
    -e DB_NAMES="production staging" ^
    -e BACKUP_INTERVAL="24" ^
    vxlink/db_vault
```

## Monitoring and Management

### View Backup Logs

```bash
# View real-time logs
docker logs -f db_vault

# View recent logs
docker logs --tail 100 db_vault
```

### Container Management

```bash
# Stop backup
docker stop db_vault

# Restart backup
docker restart db_vault

# Remove container
docker rm db_vault
```

## Backup Files

* Backup files are saved in the container's `/tmp` directory (mapped to host directory)
* File naming format: `{database_name}-YYYYMMDDHHMMSS.zip`
* Files contain complete backup of specified databases, compressed with ZIP

## Build Options

### Linux/macOS Build Script Options

```bash
./build.sh [options]

Options:
  -p, --push        Push images to registry after building
  -v, --version     Specify version tag
  -h, --help        Show help message
  --no-cache        Disable build cache
  --platform        Specify target platforms
  --all-platforms   Build for all supported platforms
```

### Windows PowerShell Build Script Options

```powershell
.\build.ps1 [options]

Options:
  -Push             Push images to registry after building
  -Version          Specify version tag
  -Help             Show help message
  -NoCache          Disable build cache
  -Platform         Specify target platforms
  -AllPlatforms     Build for all supported platforms
```

## Project Structure

```
VX-DBVault/
├── dockerfile              # Docker build file
├── build.sh                # Linux/macOS build script
├── build.ps1               # Windows PowerShell build script
├── build.version           # Version management file
├── README.md               # Project documentation
└── source/                 # Source code directory
    └── mysqldump.sh        # Database backup script
```

## System Requirements

* Docker 18.09+ or Docker Desktop
* Supported architectures: linux/amd64, linux/arm64
* For multi-platform builds: Docker Buildx support

## Troubleshooting

### 1. Database Connection Failed

Check database host address, username and password:

```bash
# Test database connection
docker run --rm -it vxlink/db_vault \
    mysqldump -h YOUR_HOST -u YOUR_USER -p YOUR_PASS --version
```

### 2. Permission Issues

Ensure Docker has permission to access the mounted directory:

```bash
# Set directory permissions
chmod 755 /host/backup/directory
```

## License

This project is licensed under the Apache 2.0 License.

## Support

For questions or suggestions, please submit an Issue.
