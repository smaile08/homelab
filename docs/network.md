# Network

<!-- RU: Карта сети. IP-план, DNS, VLAN (когда появятся). -->

## Current topology

Flat `/24` network behind a GL.iNet Slate7 router. No VLAN segmentation yet —
to be added when the lab grows.

```
Internet
   │
   ▼
[GL.iNet Slate7]  192.168.1.1
   │
   ├── n5 (Proxmox VE)            192.168.1.10
   │     └── pbs (VM)             192.168.1.11
   │
   └── (other devices on the same LAN)
```

## IP allocation plan

| Range                  | Purpose                                  |
|------------------------|------------------------------------------|
| 192.168.1.1            | Router / gateway                         |
| 192.168.1.10–.19       | Physical hosts (hypervisors, NAS, etc.)  |
| 192.168.1.20–.99       | VMs and LXC containers                   |
| 192.168.1.100–.199     | DHCP pool (clients, IoT, guests)         |
| 192.168.1.200–.254     | Reserved for future use                  |

<!-- RU: Статика для серверов, DHCP для всего остального. Не пересекаются. -->

## DNS

Currently using the router as the DNS resolver. Local hostnames resolved via
`/etc/hosts` on each machine. **TODO:** deploy a proper DNS server (AdGuard
Home or Pi-hole) and switch the router to use it as upstream.

## Future: VLAN segmentation

Planned segments once VLAN support is configured on the router and Proxmox:

| VLAN ID | Name        | Purpose                                |
|---------|-------------|----------------------------------------|
| 10      | management  | Proxmox, IPMI, switch management       |
| 20      | trusted     | Personal devices                       |
| 30      | iot         | Smart home, cameras                    |
| 40      | guest       | Guest Wi-Fi                            |
| 50      | lab         | Lab VMs, DMZ, exposed services         |
