# Ansible Role: Prysm

### Description
Ansible role that will install, configure and runs [prysm](https://github.com/prysmaticlabs/prysm): an enterprise Ethereum 2 Client

### Table of Contents
  - [Supported Platforms](#supported-platforms)
  - [Dependencies](#dependencies)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [License](#license)
  - [Author Information](#author-information)

### Supported Platforms
```
* MacOS
* Debian
* Ubuntu
* Redhat(CentOS/Fedora)
* Amazon
```

### Role Variables:

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file. By and large these variables are configuration options. Please refer to the prysm [docs](https://docs.prylabs.network/docs/prysm-usage/parameters) for more information


| Name                           | Default Value                      |  Description                                                                                                        |
|--------------------------------|------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| `prysm_version`             | ___unset___                        | __REQUIRED__ Version of prysm to install and run.                                                            |
| `prysm_user`                | prysm                         | prysm user                                                                                                   |
| `prysm_group`               | prysm                         | prysm group                                                                                                  |
| `prysm_base_dir`            | /opt/prysm                    | Path to install to                                                                                           |
| `prysm_config_dir`          | /etc/prysm                    | Path for default configuration                                                                               |
| `prysm_data_dir`            | /opt/prysm/data               | Path for data directory                                                                                      |
| `prysm_validator_data_dir`  | /opt/prysm/validatorData      | Path for validaror data directory                                                                            |
| `prysm_log_dir`             | /var/log/prysm                | Path for logs directory                                                                                      |
| `prysm_log_level`           | "info"                        | Log level                                                                                               |
| `prysm_network`             | mainnet                       | Predefined network configuration                                                                                    |
| `prysm_jwt_auth_file`       | "/etc/jwt-secret.hex"         | Path of the JWT file                                                                                                |
| `prysm_execution_urls`                 | "http://127.0.0.1:8551" | The elc execution url                                                                                               |
| `prysm_validator_beacon_interface`     | "http://127.0.01"       | The beacon endpoint for the validator to use                                                                |
| `prysm_checkpoint_sync_url`            | "https://beaconstate-{{prysm_network}}.chainsafe.io" | Checkpoint sync to speed things up                                          |
| `prysm_default_fee_recipient`          | ""                      | The default fee recepient address                                                                         |
| `prysm_keystores_dir`  | "/config/keys"                          |  The keys directory for validators                                                                        |
| `prysm_beacon_enabled`    | True                                 |  Default run the beacon node                                                                              |
| `prysm_validator_enabled` | False                                | Whether to run in validator mode - please note that the secrets and keys need to be copied by you         |


prysm_beacon_custom_cmdline_args: ""
prysm_validator_custom_cmdline_args: ""

prysm_beacon_enabled: True
prysm_validator_enabled: False
### Keys/Secrets
Please note that you must put your own secrets and keys in the config directory that you are using ie `prysm_config_dir`

### Example Playbook

1. Default setup:
Install the role from galaxy
```
ansible-galaxy install consensys.prysm
```

Create a requirements.yml with the following:
Replace `x.y.z` below with the version you would like to use from the prysm [releases](https://github.com/prysmaticlabs/prysm/releases) page
```
---
- hosts: localhost
  connection: local
  force_handlers: True

  roles:
  - role: consensys.prysm
    vars:
      prysm_version: vx.y.z

```

Run with ansible-playbook:
```
ansible-playbook -v /path/to/requirements.yml
```


2. Install via github

```
ansible-galaxy install git+https://github.com/consensys/ansible-role-prysm.git
```

Create a requirements.yml with the following:
Replace `x.y.z` below with the version you would like to use from the prysm [releases](https://github.com/prysmaticlabs/prysm/releases) page
```
---
- hosts: localhost
  connection: local
  force_handlers: True

  roles:
  - role: ansible-role-prysm
    vars:
      prysm_version: vx.y.z

```

Run with ansible-playbook:
```
ansible-playbook -v /path/to/requirements.yml
```


### License

Apache


### Author Information

PegaSysEng, 2020
