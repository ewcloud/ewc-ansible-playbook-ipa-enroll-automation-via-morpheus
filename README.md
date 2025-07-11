# EWC Ansible Role IPA Enroll Automation Via Morpheus

This repository contains a configuration template 
(i.e. an [Ansible Role](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_roles.html)) 
to customize your environment in the
[European Weather Cloud (EWC)](https://europeanweather.cloud/).
Applying this template will trigger the configuration of [Morpheus](https://morpheusdata.com/) 
entities, enabling you to edit/automate management of EWC computer resources'
life cycle via a web-based graphical user interphase (GUI).

Assuming an [IPA server](https://www.freeipa.org/) is already provisioned 
and configured within your EWC environment, the template is designed to:
* Setup automation (i.e. Morpheus Workflow) such that:
  * Any and all new virtual machines created, via the Morpheus GUI, within
  a user-specified Morpheus Domain, will enroll onto the IPA server's
  provided DNS and LDAP services.


## Copyright and License
>💡 No dependencies are distributed as part of this repository.

See the [LICENSE](./LICENSE) file for licensing information as it pertains to
files in this repository.

## Usage

The step-by-step described below assume your local file system follows the 
example structure below, with 
`ewc-ansible-role-ipa-enroll-automation-via-morpheus` being a clone of this
repository:
```
.
├── ewc-ansible-role-ipa-enroll-automation-via-morpheus
└── playbook.yml
```

### 1. Customize the template

Edit input values for the template [variables](./vars/main.yml) as needed (see
[Inputs](#inputs) section for details).
Then, proceed to create an Ansible Playbook file to load your customizations: 

```yaml
# playbook.yml
---
- name: Setup Morpheus Automation for enrollment into IPA LDAP/DNS of VMs upon provisioning
  hosts: all
  become: false

  roles:
    - ewc-ansible-role-ipa-enroll-automation-via-morpheus

```

### 2. Apply the template


You can apply changes on the target host by running:
```bash
ansible-playbook playbook.yml
```

## Inputs
> 🛠️ To be defined.

## Changelog
All notable changes (i.e. fixes, features and breaking changes) are documented 
in the [CHANGELOG.md](./CHANGELOG.md).

## Contributing

Thanks for taking the time to join our community and start contributing!
Please make sure to:
* Familiarize yourself with our [Code of Conduct](./CODE_OF_CONDUCT.md) before 
contributing.
* See [CONTRIBUTING.md](./CONTRIBUTING.md) for instructions on how to request 
or submit changes.

## Authors

[European Weather Cloud](http://support.europeanweather.cloud/) 
<[support@europeanweather.cloud](mailto:support@europeanweather.cloud)>
