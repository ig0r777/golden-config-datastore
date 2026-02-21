# Golden Config Datastore

This repository contains Golden Config data for Nautobot.

## Directory Structure

```
.
├── backup/              # Device backup configurations (auto-populated by Golden Config)
├── intended/            # Generated intended configurations (auto-populated)
├── jinja2/              # Jinja2 templates for intended configs
│   └── arista_eos/      # Arista EOS specific templates
│       ├── banner.j2    # Banner/MOTD configuration
│       ├── ssh.j2       # SSH settings and security
│       ├── hostname.j2  # Device hostname
│       ├── management.j2 # Management interface
│       ├── ntp_dns.j2   # NTP and DNS servers
│       ├── aaa.j2       # AAA and local users
│       └── base_config.j2 # Full base config (legacy)
└── compliance/          # Compliance rules for config validation
    └── arista_eos/
        ├── banner.txt   # Banner compliance rule
        ├── ssh.txt      # SSH compliance rule
        └── hostname.txt # Hostname compliance rule
```

## Features

Golden Config uses a feature-based approach where each template represents a specific configuration feature:

### Banner (`banner.j2`)
- Login banner (MOTD)
- Device identification
- Security warning

### SSH (`ssh.j2`)
- SSH version 2 enforcement
- Timeout settings
- Authentication retries
- Management SSH configuration

### Hostname (`hostname.j2`)
- Device hostname from Nautobot

### Management Interface (`management.j2`)
- Management1 interface configuration
- IP address from Nautobot primary_ip4

### NTP/DNS (`ntp_dns.j2`)
- DNS servers (Google, Cloudflare)
- NTP servers (Google, Cloudflare)

### AAA (`aaa.j2`)
- Local authentication
- Admin user account

## Usage in Nautobot

1. Repository is synced automatically by Nautobot
2. Backup job stores device configs in `backup/`
3. Intended config job generates configs using `jinja2/` templates
4. Compliance job (optional) compares backup vs intended

## Devices Managed

- spine01 (172.30.30.11)
- leaf01 (172.30.30.21)
- leaf02 (172.30.30.22)
