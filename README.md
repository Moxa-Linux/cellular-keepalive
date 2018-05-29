# Cellular Keepalive

This example script/systemd.service are written for keep cellular connections always up with ping check (ping 8.8.8.8 continuously every 5 minutes).

- Please ensure there is no PIN code protection. You could use `cell_mgmt sim_status` and `cell_mgmt unlock_pin <PIN>` to check and unlock.

## Install
1. Copy files
    - `cellular-keepalive` to `/usr/sbin/cellular-keepalive`
    - `cellular-keepalive` to `/etc/systemd/system/cellular-keepalive.service`
2. Set executable permission `chmod +x /usr/sbin/cellular-keepalive`
3. Enable systemd service, `systemctl enable cellular-keepalive`
4. Start systemd service, `systemctl start cellular-keepalive`
>  The service will start automatically at each boot and keep running

### Update `PING_TARGET` and `QMI_NODE` in `cellular-keepalive` if needed
Get cellular module info (output may vary)

```
root@Moxa:/home/moxa# cell_mgmt module_info
SLOT: 1
Module: MC7354
WWAN_node: wwan0
AT_port: /dev/ttyUSB2
GPS_port: /dev/ttyUSB1
QMI_port: /dev/cdc-wdm0
Modem_port: NotSupport
```

By default `QMI_NODE` => `/dev/cdc-wdm0` and `PING_TARGET` => `8.8.8.8` (Google DNS Service)

## Uninstall
1. Stop/Disable systemd service
    - `systemctl stop cellular-keepalive`
    - `systemctl disable cellular-keepalive`
2. Remove files
    - `/usr/sbin/cellular-keepalive`
    - `/etc/systemd/system/cellular-keepalive.service`
