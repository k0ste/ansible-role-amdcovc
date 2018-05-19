
# ansible-amdcovc

Deploy [amdcovc](//github.com/matszpk/amdcovc) - Utility to overclock AMD Radeon
GPU's.

## Requirements

* Ansible 2.4+;
* Linux systemd distro (ArchLinux 100% supported);

# Extra

Role allow to deploy setting for every card or equal settings for bunch of cards
(see examples below).

Systemd service is respect [xmrig-amd](//github.com/xmrig/xmrig-amd) and will
start before any miner instance.

# Example configuration

```yaml
---
amdcovc:
- role_settings:
  # Enable amdcovc service (default is 'false').
  - enable: 'true'
  # Restart amdcovc after successful deploy (default is 'false').
    restart: 'true'
  # Install amdcovc package or not (default is 'false').
    install_package: 'true'
  # 'present' (do nothing if package is already installed) or 'latest' (always
  #  upgrade to last version).
    package_state: 'present'
  instance_settings:
# Set equal settings for first 5 cards.
  - card: '0-4'
    core_clock: '1150'
    mem_clock: '1600'
    fan_speed: '100'
# And special settings for last card.
  - card: '5'
    core_clock: '1050'
    mem_clock: '1500'
    fan_speed: '100'
```
