# Golden Config Datastore

This repository contains Golden Config data for Nautobot.

## Directory Structure

```
.
├── backup/              # Device backup configurations (auto-populated by Golden Config)
├── intended/            # Generated intended configurations (auto-populated)
├── jinja2/              # Jinja2 templates for intended configs
│   └── arista_eos/      # Arista EOS specific templates
│       └── base_config.j2
└── compliance/          # Compliance rules and features (optional)
```

## Templates

### Arista EOS Base Configuration (`jinja2/arista_eos/base_config.j2`)
Provides basic configuration including:
- Hostname
- Management interface
- DNS and NTP
- AAA (admin user)
- API services (HTTP, gNMI, NETCONF)
- Banner

## Usage in Nautobot

1. Repository is synced automatically by Nautobot
2. Backup job stores device configs in `backup/`
3. Intended config job generates configs using `jinja2/` templates
4. Compliance job (optional) compares backup vs intended

## Devices Managed

- spine01 (172.30.30.11)
- leaf01 (172.30.30.21)
- leaf02 (172.30.30.22)
