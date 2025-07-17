# EWC Ansible Role IPA Enroll Automation Via Morpheus

This repository contains a configuration template 
(i.e. an [Ansible Role](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_roles.html)) 
to customize your environment in the
[European Weather Cloud (EWC)](https://europeanweather.cloud/).
Applying this template will trigger the configuration of [Morpheus](https://morpheusdata.com/) 
entities, enabling you to edit/automate management of EWC computer resources'
life cycle via a web-based graphical user interphase (GUI).

Assuming an [IPA server](https://www.freeipa.org/) is already provisioned 
and configured within the EWC environment, the template is designed to:
* Setup automation (i.e. Morpheus Integration, Tasks, Workflow and Network Domain) such that:
  * New virtual machines created via the Morpheus GUI within
  a user-defined Morpheus Network Domain, will enroll onto a the IPA server's
  provided DNS and LDAP services.
  * Enrolled virtual machines will disenroll from the IPA server upon
  their deletion via Morpheus GUI


## Copyright and License
>💡 No dependencies are distributed as part of this repository.

See the [LICENSE](./LICENSE) file for licensing information as it pertains to
files in this repository.

## Authentication

Before proceeding, if you lack a Morpheus API access token, make sure
to check out the [EWC documentation](https://confluence.ecmwf.int/display/EWCLOUDKB/How+to+generate+Morpheus+API+access+tokens)
for steps on how to generate one in a self-service manner.

## Usage

The step-by-step described below assume your local file system follows the 
example structure below, with 
`ewc-ansible-role-ipa-enroll-automation-via-morpheus` being a clone of this
repository:
```
.
├── roles
│   └── ewc-ansible-role-ipa-enroll-automation-via-morpheus
└── playbook.yml
```

### 1. Customize the template

Edit input values for the template [variables](./vars/main.yml) as needed (see
[Inputs](#inputs) section for details).
Then, proceed to create an Ansible Playbook file to load your customizations: 

```yaml
# playbook.yml
---
- name: Setup Morpheus automation IPA client lifecycle management
  hosts: localhost
  connection: local
  gather_facts: false

  roles:
    - ewc-ansible-role-ipa-enroll-automation-via-morpheus

```

### 2. Apply the template

You can apply changes to by running:
```bash
ansible-playbook playbook.yml
```

### 3. Manually link the Morpheus Workflow to the user-defined Morpheus Domain
> ⚠️ As of 17.07.2025, technical limitations on the side of the 
[Morpheus API](https://apidocs.morpheusdata.com/v7.0.9/reference/createnetworkdomain)
lead to unreliable configuration of links between workflows and domains.
As a workaround, manual action over the Morpheus GUI is required.

Finalize the configuration over the Morpheus GUI:

1. Login to the Morpheus GUI of your EWC environment
2. From the top navigation bar, go to `Infrastructure > Network`.
3. Select `Domains` from the sub navigation bar. 
4. A table will be displayed in the lower portion of the view port, and
containing details of available domains in your EWC environment. Click on the 
edit icon (`🖉`) on the same row where your defined domain is listed.
5. Within the pop-up edit form, click on the `Select Workflow` drop-down 
menu and select `ipa-enroll-automation`. Click on `SAVE CHANGES` at the 
bottom of the form to finalize the setup.

## Inputs
> ⚠️ If set, the `update_morpheus_cypher` flag will trigger the creation/edition of secrets within Morpheus Cypher.
To avoid unexpected behavior during IPA clients enrollment, ensure the values of all input secrets (i.e. those with
`morpheus_cypher_` prefix) are set and match to the values currently store by the IPA server in your EWC environment.

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|----------|
| morpheus_token | Morpheus API access token | `string` | n/a | yes |
| morpheus_url | Morpheus API URL | `string` | n/a | yes |
| morpheus_tenant_name | Morpheus tenant name.  Example: `<memberstate>-<organization>-<projectname>` | `string` | n/a | yes |
| update_morpheus_cypher | flag to update required secrets in Morpheus Cypher. Only `yes` will be accepted to approve | `string` | n/a | yes |
| morpheus_cypher_ipa_domain | IPA domain name. Must match with the value set used during used during configuration of a pre-existing IPA server within the EWC environment. Example: `<memberstate>-<organization>-<projectname>.ewc` | `string` | n/a | yes |
| morpheus_cypher_ipa_server_hostname | IPA server host name. Must match with the value set used during used during configuration of a pre-existing IPA server within the EWC environment. Example: `ldap` | `string` | n/a | no |
| morpheus_cypher_ipa_admin_username | IPA Directory Manager/Admin username. Must match with the value set used during used during configuration of a pre-existing IPA server within the EWC environment | `string` | n/a | no |
| morpheus_cypher_ipa_admin_password | IPA Directory Manager/Admin password. Must match with the value set used during used during configuration of a pre-existing IPA server within the EWC environment | `string` | n/a | no |

## Final Environment

Applying this template will configure the following  entities in the Morpheus GUI:

| Name | Type | Description |
|------|---------|---------|
| `ewc-flavours` | Morpheus Integration | Links to EWC Community Hub's GitHub repository where Ansible Playbooks for IPA client enrollment/disenrollment are published |
| `ipa-client-enroll` | Morpheus Task | Executes an Ansible Playbook to carry out IPA client enrollment |
| `ipa-client-disenroll` | Morpheus Task |  Executes an Ansible Playbook to perform IPA client disenrollment |
| `ipa-enroll-automation` | Morpheus Workflow | Orchestrates tasks to run specifically during provision and teardown stages of a virtual machine's life cycle  |
| `<user defined>` | Morpheus Domain | Encapsulates virtual machines and automates workflow triggering |
| `secret/ipa_domain` | Morpheus Cypher Secret | Read during enrollment/disenrollment Ansible Playbooks execution |
| `secret/ipa_server_hostname` | Morpheus Cypher Secret | Read during enrollment/disenrollment Ansible Playbooks execution |
| `secret/ipa_admin_username` | Morpheus Cypher Secret | Read during enrollment/disenrollment Ansible Playbooks execution |
| `secret/ipa_admin_password` | Morpheus Cypher Secret | Read during enrollment/disenrollment Ansible Playbooks execution |

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
