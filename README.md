# Ansible Role: snmp exporter

## Description

Deploy and manage prometheus [SNMP exporter](https://github.com/prometheus/snmp_exporter) using ansible.

## Requirements

- Ansible >= 2.6 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `proxy_env` | {} | Proxy environment variables |
| `snmp_exporter_version` | 0.18.0 | SNMP exporter package version |
| `snmp_exporter_web_listen_address` | "0.0.0.0" | Address on which SNMP exporter will be listening |
| `snmp_exporter_web_listen_port` | 9116 | Port on which SNMP exporter will be listening |
| `snmp_exporter_config_file` | "" | If this is empty, role will download snmp.yml file from https://github.com/prometheus/snmp_exporter. Otherwise this should contain path to file with custom snmp exporter configuration |
| `snmp_exporter_log_level` | "warn" | Loglevel of the exporter |
| `snmp_exporter_log_format` | "json" | Logformat fo the exporter |
| `snmp_exporter_firewalld_state` | "disabled | Enabled/Disabled Firewalld and open the port |
| `snmp_exporter_binary_local_dir` | "/usr/local/bin" | Exporter binary path |
| `snmp_exporter_config_dir` | "/etc/snmp_exporter" | Exporter config folder |
| `snmp_exporter_create_consul_agent_service` | true | Add consul-agent service snipped |
| `snmp_exporter_system_user` | "{{ prometheus_user | default('prometheus') }}" | Exporter running user |
| `snmp_exporter_system_group` | "{{ prometheus_group | default('prometheus') }}" | Exporter running group |
| `snmp_exporter_config_file` | "config.yml" | Config stored in files folder. If empty, there download the orignal snmp.yml from github repository |

## Example

### Playbook

```yaml
- hosts: all
  become: yes
  roles:
    - ansible-role-snmp-exporter
```

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
