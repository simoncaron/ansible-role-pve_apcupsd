Ansible Role: Proxmox VE apcupsd Config
=========

![Ansible Lint](https://github.com/simoncaron/ansible-role-pve_apcupsd/actions/workflows/lint.yml/badge.svg)
![Ansible Release](https://github.com/simoncaron/ansible-role-pve_apcupsd/actions/workflows/release.yml/badge.svg)
[![Ansible Galaxy Downloads](https://img.shields.io/badge/dynamic/json?color=blueviolet&label=Galaxy%20Downloads&query=%24.download_count&url=https%3A%2F%2Fgalaxy.ansible.com%2Fapi%2Fv1%2Froles%2F26239%2F%3Fformat%3Djson)](https://galaxy.ansible.com/ui/standalone/roles/simoncaron/pve_apcupsd/)

An Ansible Role that configures apcupsd on Proxmox VE. Notifications are sent using Promox built-in notification tool `proxmox-mail-forward` which will send emails to the address configured for the root user of the PVE node by default.

This role was tested on Proxmox VE 7.2.

Requirements
------------

None.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

    pve_apcupsd_ups_name: ""
    pve_apcupsd_ups_cable: usb
    pve_apcupsd_ups_type: usb
    
    pve_apcupsd_device: ""
    pve_apcupsd_on_battery_delay: "6"
    
    pve_apcupsd_ups_battery_level: "5"
    pve_apcupsd_ups_minutes: "3"
    pve_apcupsd_nisip: 127.0.0.1

    pve_apcupsd_monitored_hosts: []

Default configuration should be enough to configure standard USB APC UPSes and corresponds to the default configuration shipped with apcupsd.

For additionnal information on configuration values for the `apcupsd.conf` file see [the daemon documentation]().

The key `pve_apcupsd_monitored_hosts` allows to configure hosts monitored by multimon and upsstats. Each entry in this list should contain the host address and description:

    pve_apcupsd_monitored_hosts:
      - address: 192.168.2.2
        description: Server1
      - address: 192.168.2.3
        description: Server2

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: localhost

      vars:
        pve_apcupsd_ups_name: ""
        pve_apcupsd_on_battery_delay: "10"
        pve_apcupsd_ups_battery_level: "10"
        pve_apcupsd_ups_minutes: "5"

      roles:
        - simoncaron.pve_apcupsd

License
-------

MIT

Author Information
------------------

This role was created in 2022 by [Simon Caron](https://simoncaron.com/).
