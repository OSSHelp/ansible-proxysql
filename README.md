# ProxySQL

[![Build Status](https://drone.osshelp.ru/api/badges/ansible/proxysql/status.svg)](https://drone.osshelp.ru/ansible/proxysql)

Role which installs ProxySQL

## Usage (example)

```yaml
    - role: proxysql
```

## Available parameters

### Installation

| Param | Default | Description  |
| -------- | -------- | -------- |
| `proxysql_setup` | `full` | Setup mode. See [OSSHelp KB article](https://oss.help/kb4895) |
| `proxysql_ver` | `2.0` | Version of ProxySQL to install (2.0 or 1.4) |
| `proxysql_cnf_src` | `files/proxysql/proxysql.cnf` | source path for proxysql.cnf |
| `pxcli_uri` | [scripts](https://oss.help/scripts/databases/proxysql/pxcli) | URL to download pxcli script from |

### Pxcli.cnf

Params for `/root/.pxcli.cnf`

| Param | Default | Description  |
| -------- | -------- | -------- |
| `pxcli_host` | `127.0.0.1` | host |
| `pxcli_port` | `6032` |port |
| `pxcli_user` | `admin` |user |
| `pxcli_password` | `strong_password` |password |
| `pxcli_promt` | `'proxysql> '`| cli promt |

## FAQ

### How to update proxysql configuration in database

Just restart the service via systemctl. Systemd unit calls the binary with `--reload` param, which forces it to merge configuration to database on every restart:

```plain
~# proxysql --help | grep reload
--reload                     Merge config file into database file
```

## Useful links

- [GitHub](https://github.com/sysown/proxysql)
- [Our KB](https://oss.help/kb1603)

## TODO

- write template for proxysql.cnf
- get ansible_distribution_release by task (setup module) if doesn't exist
- move default variables to defaults/main.yml

## License

GPL3

## Author

OSSHelp Team, see <https://oss.help>
