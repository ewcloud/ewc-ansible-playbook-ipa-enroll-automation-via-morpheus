# Changelog

All notable changes to this project are documented in this file. See
[Conventional Commits](https://conventionalcommits.org) for commit guidelines.

# [1.1.0](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/compare/1.0.1...1.1.0) (2025-12-03)


### Features

* Test automation support ([#3](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/issues/3)) ([03191c2](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/03191c22fcd2ff9476ae3ed3f3fc1c7b3c4be037))

# [1.0.1](https://github.com/ewcloud/ewc-flavours/compare/1.0.0...1.0.1) (2025-10-02)


### Bug Fixes

* Item metadata rendering ([5bb07e2](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/5bb07e267ea9672f130e949e43efe405f32be500))

# 1.0.0 (2025-09-19)


### Bug Fixes

* Avoide use of FQDN for role input hostname ([2dda26b](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/2dda26be57c2546dfb6847f9ec9c9d75fb4ed102))
* Prevent Morpheus Workflow updates from de-orchestrating teardown task ([c3659a3](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/c3659a3d1c25ecd8444bfa627eb42ac37ac04223))
* Re-direct Morpheus automation to migrated playbook assets ([0c88688](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/0c88688ecdb07a9b5beeb4a7321d9d0d0f60122e))


### Features

* Add Ansible Playbook pre-configured for input prompting and localhost execution ([141a0e7](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/141a0e764c9e49645754568ddaaf8bbbe07c7d7f))
* Add IPA info as Morpheus Cypher secrets, including optional skip for subsequent runs ([a9b9f66](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/a9b9f66aab4801cd48b651a1c581294a043e0c6e))
* Add Morpheus Workflow to orchestrate provision and teardown phases of IPA client lifecyle ([36c48f8](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/36c48f8265d3cb85c3ef1f7ad36e321f11f22ebf))
* Add user-defined Morpheus Network Domain under which IPA client provision/teardown runs automatically ([42af176](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/42af176750f9c97e23a9462b5d9340e2e24dfe33))
* Authenticate against user-defined EWC tenant via Morpheus API ([79d0657](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/79d06570452a54d66b59961aff25266c04c1d609))
* Bump IPA client enroll dependency version to 1.1.1 ([3d346c9](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/3d346c995ca64ffdda37e40dc789ffb2a32279ec))
* Configure integration with ewc-flavours GitHub repository ([af6f75a](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/af6f75a06519f31d43c3592640b62ee14aa2b92f))
* Configure Morpheus Tasks out of Ansible Playbooks from GitHub integration ([e66940b](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/e66940bb7b12b8b6b0f8f553eb38ee31f7a90196))
* Consistent variable naming for Morpheus API inputs ([e21d817](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/e21d817096d919002bd996ec598a6cc6a0e7cb6c))
* Downgrade to manual link of Workflow and Domain via GUI ([2fbd34c](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/2fbd34cc9a778bba3eb67d733aa831955d92062b))
* Link Morpheus Workflow to user-defined Morpheus Network Domain for automatic triggering ([bd31b63](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/bd31b630bc1a9e3b827a9204efe89175d48e729f))
* Prevent credential leaks into logs upon task failure ([610c4ba](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/610c4ba76da322f02f4559a1b429ddc13e0d5ee9))
* Support remote Ansible Role installationwith requirements.yml and Ansible Galaxy ([7abc38d](https://github.com/ewcloud/ewc-ansible-playbook-ipa-enroll-automation-via-morpheus/commit/7abc38d2cfc4ffbb48d4a4ab37f6582d046d3988))
