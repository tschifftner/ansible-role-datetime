# Ansible Role: Install DateTime

[![Build Status](https://travis-ci.org/tschifftner/ansible-role-datetime.svg?branch=master)](https://travis-ci.org/tschifftner/ansible-role-datetime)

Installs and configures ntp and defines timezone on Debian/Ubuntu linux servers.

## Requirements

None

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```
# ntp
datetime_ntp_config_server: [ '0.de.pool.ntp.org', '1.de.pool.ntp.org', '2.de.pool.ntp.org', '3.de.pool.ntp.org' ]

# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html
datetime_ntp_config_restrict:
- '-4 default kod notrap nomodify nopeer noquery'
- '-6 default kod notrap nomodify nopeer noquery'
- '127.0.0.1'
- '::1'

datetime_ntp_stats:
  - statistics loopstats peerstats clockstats
  - filegen loopstats file loopstats type day enable
  - filegen peerstats file peerstats type day enable
  - filegen clockstats file clockstats type day enable

# Add additional configuration here
datetime_ntp_config_additional: ''

datetime_sync_hardware_clock: true

# timezone
datetime_timezone: 'Europe/Berlin'

# Monit
datetime_enable_monit_check: true
```

## Dependencies

None.

## Installation

```
$ ansible-galaxy install tschifftner.datetime
```

## Example Playbook

```
- hosts: server
  roles:
    - { role: tschifftner.datetime }
```

## Supported OS

 - Debian 9 (Stretch)
 - Debian 8 (Jessie)
 - Ubuntu 18.04 (Bionic Beaver)
 - Ubuntu 16.04 (Xenial Xerus)
 
## Required ansible version

Ansible 2.5+

## License

[MIT License](http://choosealicense.com/licenses/mit/)

## Author Information

 - [Tobias Schifftner](https://twitter.com/tschifftner), [ambimax® GmbH](https://www.ambimax.de)