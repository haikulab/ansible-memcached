ansible-memcached for Debian/Ubuntu
============

Ansible role for configuration of memcached.

## Overwriting Variables

The `vars/main.yml` file should contain your list of packages you want to install in order to override defaults found in `defaults/main.yml`. Additionally, you can overwrite the variables as part of your playbook.

## Auto reboot is disabled

Some security updates require a reboot. To make sure that this doesn't happen when you're least expecting and brings down your production environment, `Unattended-Upgrade::Automatic-Reboot` is specifically set to `false` by default.

## Email Notifications

You can enable/configure sending of email notifications to let you know if any errors trigger during automated security updates.

```yml
system_packages:
  - memcached

memcached_log_path: /var/log/memcached.log
memcached_max_memory: 64
memcached_ip: 127.0.0.1
memcached_port: 11211
memcached_user: memcache
```

## Debugging

If you run into errors, uncomment the `- debug: msg="{{ ... }}"` statements.

Progress of the auto update process is logged and can be reviewed `/var/log/unattended-upgrades` directory.
