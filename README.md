# sysctl

This role configures sysctl values and restarts `systemd-sysctl` afterwards to apply them.
The file the sysctl values is written to is called `XX-ansible.conf` where `XX` is a configurable number (default: `10`).
This allows to set the priority of the file if other packages/modules also place sysctl configurations to `/etc/sysctl.d`.
Note that when changing the value, the old file is not automatically removed.

## Requirements

Debian with systemd

## Role Variables

| Name            | Default / Mandatory | Description                       |
|:----------------|:-------------------:|:----------------------------------|
| `sysctl_number` | `10`                | The number of the filename prefix |
| `sysctl`        | `{}`                | sysctl values to set              |

## Example Playbook

```yml
- hosts: all
  roles:
    - role: sysctl
      sysctl:
        net.ip6: 0
        net.bridge.bridge-nf-call-arptables: 0
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

## Author Information

- [Janne Heß](https://github.com/dasJ)
