Ansible Role: Proxmox VE apcupsd Config
=========

![Lint](https://github.com/simoncaron/ansible-role-pve_apcupsd/actions/workflows/lint.yml/badge.svg)

An Ansible Role that configures apcupsd on Proxmox VE. Notifications are sent using Promox built-in notification tool `pvemailforward` which will send emails to the address configured for the root user of the PVE node by default.

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

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

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
