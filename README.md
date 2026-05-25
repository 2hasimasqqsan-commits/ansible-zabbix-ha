# Zabbix HA Ansible Lab

## Nodes

- zbx-ha-db01: 192.168.56.111
- zbx-ha-db02: 192.168.56.112
- Zabbix Web VIP: 192.168.56.113
- DB VIP: 192.168.56.114
- BMC db01: 192.168.56.121
- BMC db02: 192.168.56.122

## Fencing:
- Proxmox fence_pve is replaced by BMC fencing.
- Default agent: fence_ipmilan
- stonith-action: off

## DB HA Components

- Corosync
- Pacemaker
- DRBD
- MariaDB
- IPaddr2 DB VIP

## Build order

1. Run common role
2. Run DRBD role
3. Run init_drbd.yml only once
4. Run mysql_ha role
5. Run pacemaker.yml
6. Run verify.yml

## Important note

STONITH is currently disabled for lab verification.

```bash
stonith-enabled=false
