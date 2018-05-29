# Cellular Keepalive

This example script

## Update PING_TARGET and QMI_NODE in `cellular-keepalive`
1. Get cellular module info
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
2. By default `QMI_NODE` => `/dev/cdc-wdm0` and `PING_TARGET` => `8.8.8.8` (Google DNS Service)

## Install
1. Copy files
    - `cellular-keepalive` to `/usr/sbin/cellular-keepalive`
    - `cellular-keepalive` to `/etc/systemd/system/cellular-keepalive.service`
2. Set executable permission `chmod +x /usr/sbin/cellular-keepalive`
3. Enable systemd service, `systemctl enable cellular-keepalive`
4. Start systemd service, `systemctl start cellular-keepalive`
>  The service will start automatically at each boot and keep running

## Uninstall
1. Stop/Disable systemd service
    - `systemctl stop cellular-keepalive`
    - `systemctl disable cellular-keepalive`
2. Remove files
    - `/usr/sbin/cellular-keepalive`
    - `/etc/systemd/system/cellular-keepalive.service`