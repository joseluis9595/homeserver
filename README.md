# Homeserver

Ansible project to deploy and configure my local homeserver, with dockerized services such as home assistant or plrex

## Hardware

#### Setup SSD boot on rpi4

- https://www.youtube.com/watch?v=Mq5zBTpGNlE&t=262s

----

## Execution

To execute the ansible playbook on this repo:
`ansible-playbook run.yml --vault-password-file=.vault_pass --tags="desired_tag"`
To modify secrets vault
`EDITOR=nano ansible-vault edit group_vars/all/secrets.yml --vault-password-file=.vault_pass`

----

## Containers

### Services

- **zigbee2mqtt** on port **8080**
- **homeAssistant** on port **8123**

----

## Containers configuration

### SWAG (NGINX + letsencrypt)

To be able to use home assistant with a reverse proxy, add this snippet to the `configuration.yml` file

```
http:
  use_x_forwarded_for: true
  trusted_proxies: 172.19.0.2
```

#### Access logs

Available on `/home/jose/homeserver/docker/data/swag/logs`


----

## TODO

- ~~- Proxy for remote connections~~
- Proxy for local connections
- VPN
- User configuration
- Static IP address
- Data backup

- Containers
    - Plex
    - Vaultwarden
    - Grafana + influxdb
    - loki?

- Home assistant
    - Grafana integration
    - 3d floorplan