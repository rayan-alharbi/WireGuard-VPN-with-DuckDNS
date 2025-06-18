# WireGuard VPN with DuckDNS

A secure, self-hosted VPN solution using WireGuard and DuckDNS for dynamic DNS. This setup uses Docker Compose for easy deployment and management.

## 🌟 Features

- **End-to-End Encryption**: Secure your internet connection with WireGuard's modern cryptography
- **Dynamic DNS**: Automatic IP updates with DuckDNS for dynamic IP addresses
- **Multi-Device**: Support for multiple simultaneous client connections
- **Dockerized**: Easy deployment and management with Docker Compose
- **Lightweight**: Minimal resource footprint

## 🚀 Quick Start

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/)
- A [DuckDNS](https://www.duckdns.org/) account and subdomain
- Port forwarding for UDP traffic (default: 51820) on your router

### 1. Clone the Repository

```bash
git clone https://github.com/rayan-alharbi/WireGuard-VPN-with-DuckDNS.git
cd WireGuard-VPN-with-DuckDNS
```

### 2. Configure Environment

Edit the `.env` file with your settings:

```ini
# Required Configuration
DUCKDNS_SUBDOMAIN=your-subdomain
DUCKDNS_TOKEN=your-duckdns-token
TZ=Asia/Riyadh

# Optional Configuration
SERVER_PORT=51820           # WireGuard port
PEERS=1                     # Number of client configs to generate
INTERNAL_SUBNET=10.13.13.0  # Internal VPN subnet
```

### 3. Start the Services

```bash
docker-compose up -d
```

### 4. Get Client Configuration

After starting, find your client configuration at:
```
./wireguard/config/peer_X/peer_X.conf
```
Where `X` is the peer number (starting from 1).

## 📱 Connecting Clients

1. Install [WireGuard](https://www.wireguard.com/install/) on your device
2. Import the `peer_X.conf` file
3. Connect to the VPN

## 🔒 Security Best Practices

- 🔐 Keep your `.env` file private and never commit it to version control
- 🔑 Use strong, unique passwords for all services
- 🔄 Regularly update your Docker containers
- 🔍 Monitor your server logs for suspicious activity

## 🛠️ Maintenance

### View Logs
```bash
docker-compose logs -f
```

### Update Containers
```bash
docker-compose pull
docker-compose up -d --force-recreate
```

### Backup Configurations
Backup the `wireguard/config` directory to preserve your VPN settings.

## 🚨 Troubleshooting

### Common Issues

1. **Can't connect to VPN**
   - Verify port forwarding on your router
   - Check firewall settings
   - Ensure Docker is running

2. **DNS resolution issues**
   - Check your client's DNS settings
   - Verify DuckDNS is updating correctly

3. **Container won't start**
   - Check logs with `docker-compose logs`
   - Verify all environment variables are set

## 📚 Resources

- [WireGuard Documentation](https://www.wireguard.com/)
- [DuckDNS Setup Guide](https://www.duckdns.org/install.jsp)
- [Docker Documentation](https://docs.docker.com/)
